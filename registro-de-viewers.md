# Registro de viewers: refatorando um `switch` com Open/Closed

Material de estudo sobre como trocar o `switch` do `EnterViewer` por um **registro** (lookup table), aplicando o princípio **Open/Closed** do SOLID.

---

## 1. O problema

O `switch` cresce a cada formato novo, e a mesma lista de formatos acaba repetida em vários lugares:

```tsx
function viewerCase(form: string) {
  switch (form) {
    case "square":
      return <SquareView></SquareView>;
    case "pyramid":
      return <PyramidView></PyramidView>;
    case "copyMachine":
      return <CopyMachineView></CopyMachineView>;
    case "anakinPod":
      return <PodAnakinView></PodAnakinView>;
  }
}
```

Para adicionar um formato, é preciso editar **três lugares**:

1. a união de tipos: `"square" | "pyramid" | ...`
2. o `switch`
3. o `App.tsx` (um `<EnterViewer>` por formato, com o texto do botão)

Um erro desse tipo já aconteceu: o `case "anakinPod"` devolvia `<PodAnakin>` (o modelo) em vez de `<PodAnakinView>` (a view), e o TypeScript não avisou.

---

## 2. O princípio: Open/Closed (o "O" do SOLID)

> O código deve ser **aberto para extensão** e **fechado para modificação**.

Na prática: adicionar um formato novo deve ser **acrescentar** algo, e não **editar** código que já funciona e já foi testado.

Técnica usada aqui: um **registro** (objeto que mapeia chave → componente). Ele é parente dos padrões **Strategy** e **Factory**, mas em TypeScript/React não precisa de classes nem interfaces: um objeto com componentes já é o padrão aplicado.

---

## 3. A implementação

### `src/viewers/registry.ts`

```ts
import type { ComponentType } from "react";
import { SquareView } from "./squareView";
import { PyramidView } from "./pyramidView";
import { CopyMachineView } from "./copyMachineView";
import { PodAnakinView } from "./podAnakinView";

export const viewers = {
  square:      { label: "Ver cubo",      View: SquareView },
  pyramid:     { label: "Ver pirâmide",  View: PyramidView },
  copyMachine: { label: "Ver copiadora", View: CopyMachineView },
  anakinPod:   { label: "Ver pod",       View: PodAnakinView },
} satisfies Record<string, { label: string; View: ComponentType }>;

export type ViewerKey = keyof typeof viewers;
```

### `src/components/EnterViewer/enterViewer.tsx`

```tsx
import { useState } from "react";
import { createXRStore, XR } from "@react-three/xr";
import { Canvas } from "@react-three/fiber";
import { viewers, type ViewerKey } from "../../viewers/registry";
import "./enterViewer.css";

export function EnterViewer({ geometricForm }: { geometricForm: ViewerKey }) {
  const [store] = useState(() => createXRStore());
  const { label, View } = viewers[geometricForm];

  return (
    <div className="container">
      <button className="card" onClick={() => store.enterAR()}>
        {label}
      </button>

      <Canvas className="canvas">
        <XR store={store}>
          <View />
        </XR>
      </Canvas>
    </div>
  );
}
```

### `src/App.tsx`

```tsx
import { EnterViewer } from "./components/EnterViewer/enterViewer";
import { viewers, type ViewerKey } from "./viewers/registry";
import "./App.css";

export default function App() {
  return (
    <div className="viewers">
      {(Object.keys(viewers) as ViewerKey[]).map((key) => (
        <EnterViewer key={key} geometricForm={key} />
      ))}
    </div>
  );
}
```

---

## 4. Como adicionar um formato novo

Só **uma linha** no `registry.ts`:

```ts
cilindro: { label: "Ver cilindro", View: CilindroView },
```

O `EnterViewer` e o `App` não mudam. O botão aparece sozinho, porque o `App` percorre o registro.

---

## 5. O que cada parte faz

| Parte | Função |
|---|---|
| `satisfies Record<string, {...}>` | Valida o formato de cada entrada **sem apagar as chaves literais**. Se colocar algo que não é componente, o TypeScript reclama na hora. |
| `keyof typeof viewers` | Deriva `ViewerKey` do próprio objeto. Não existe mais uma união de tipos escrita à mão para esquecer de atualizar. |
| `{ label, View }` | O texto do botão mora junto do viewer, e não espalhado no `App`. |
| `const { label, View } = viewers[geometricForm]` | Substitui o `switch`: é uma consulta direta por chave. |
| `Object.keys(viewers) as ViewerKey[]` | O `Object.keys` devolve `string[]`, então o cast para `ViewerKey[]` é necessário. É o único `as` do desenho. |

**Requisito:** `satisfies` exige TypeScript 4.9 ou mais novo.

---

## 6. O que se ganha

- **Adicionar um formato é uma linha**, sem mexer em código existente.
- **Uma única fonte da verdade**: antes eram três listas (tipo, `switch`, `App`).
- **Erros pegos em compilação**: o bug do `PodAnakin` no lugar de `PodAnakinView` não passa mais despercebido.
- **Metadados juntos**: ícone, descrição ou altura real podem entrar no mesmo objeto.

---

## 7. Quando **não** vale a pena

Um `switch` de 4 casos não é um problema por si só. O sinal para refatorar é o que apareceu aqui: **a mesma lista repetida em vários lugares**, e cada novo item pedindo edição em todos eles.

Se cada formato tivesse **lógica diferente** (e não só "qual componente mostrar"), valeria pensar em uma interface com métodos (Strategy "de verdade"). Não é o caso agora.

---

## 8. Experimentos para estudar

1. **Adicionar um campo ao registro.** Por exemplo `descricao: string` no tipo do `satisfies` e ver o TypeScript apontar todas as entradas que faltam.
2. **Quebrar de propósito.** Colocar `View: "texto"` em uma entrada e ler a mensagem de erro do `satisfies`.
3. **Carregar sob demanda com `lazy`.** Trocar por:

   ```ts
   import { lazy } from "react";

   anakinPod: {
     label: "Ver pod",
     View: lazy(() => import("./podAnakinView").then(m => ({ default: m.PodAnakinView }))),
   },
   ```

   Exige um `<Suspense>` em volta do `<View />`. Cada viewer, e o modelo 3D pesado dele, só é baixado quando usado.
4. **Comparar com `satisfies` vs. anotação de tipo.** Trocar `satisfies Record<...>` por `: Record<string, {...}>` e observar que `ViewerKey` vira `string` (as chaves literais se perdem). Isso mostra por que o `satisfies` importa aqui.
5. **Extrair o tipo da entrada.** Criar `type ViewerEntry = { label: string; View: ComponentType }` e reusar no registro, para praticar a separação entre tipo e valor.

---

## 9. Termos para pesquisar depois

- Princípio **Open/Closed** (SOLID)
- Padrão **Strategy** e padrão **Factory**
- **Lookup table** / dispatch table / *registry pattern*
- Operador `satisfies` (TypeScript 4.9)
- `React.lazy` e `Suspense`
- Eliminação de `switch` por **polimorfismo** ("replace conditional with polymorphism")
