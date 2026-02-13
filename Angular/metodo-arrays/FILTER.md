O comando filter() é literalmente um filtro, vc coloca as condicionais dentro dele e ele vai criar um novo array com  os elementos que atendem aquelas condições. Pode por exemplo num array de pessoas , filtrar elas para criar um novo array só com pessoa com idade superior a 18. A função filter() é usada mais para filtrar usuários realmente.

Exemplo de array de objetos:
```
const Lista:pessoa[] = [
	{id:1,nome:'alice',idade:25,cargo:'DEV',ativo:true},
	{id:2,nome:'bruno',idade:18,cargo:'ADM',ativo:false},
	{id:3,nome:'cadu',idade:19,cargo:'DEV',ativo:true},
	{id:4,nome:'carla',idade:22,cargo:'design',ativo:true},
	{id:5,nome:'diego',idade:30,cargo:'design',ativo:false},
]
```

Criar um novo array com pessoas com idade menos que 25:
```
const MaisNovos = Lista.filter(u => u.idade < 25)
console.log(Mais novos)
```

Vai imprimir:
```
[
  { id: 2, nome: 'bruno', idade: 18, cargo: 'ADM', ativo: false },
  { id: 3, nome: 'cadu', idade: 19, cargo: 'DEV', ativo: true },
  { id: 4, nome: 'carla', idade: 22, cargo: 'design', ativo: true }
]
```
