O comando find() retorna o primeiro usuário que atender as condições que você colocar dentro dele. Por exemplo,pode procurar por um nome ou ID especifico dentro desse array, e ele vai retornar o elemento, comando find não retorna um array, ele retorna um único elemento. Ele é usando para principalmente fazer buscas em arrays de objetos e tals.

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

Usando o comando find para buscar um usuário dentro do array:
```
const UsuarioEncontrado = Lista.find(u => u.nome === 'carla')
console.log(UsuarioEncontrado)
```

Vai imprimir:                                                                                **(ele retorna o elemento/objeto)**
```
{ id: 4, nome: 'carla', idade: 22, cargo: 'design', ativo: true }
```