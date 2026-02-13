o comando map() cria um novo array apenas com os parâmetro que vc especificar nele,por exemplo nome ou idade , ou colocar uma função que multiplica por 2 por exemplo , que irá gerar um novo array com o dobro de todos os números do array original. A função map é ideal para criar um novo array apenas com dados específicos.

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

posso usar o comando map() para pegar só os nomes do usuários como no exemplo anterior.

```
const NomesLista = Lista.map(u => u.nome)
console.log(NomesLista)
```
vai imprimir:
```
[ 'alice', 'bruno', 'cadu', 'carla', 'diego' ]
```
