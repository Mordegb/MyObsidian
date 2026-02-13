a função every() recebe uma condição e lê todos os elementos do array, se todos os elementos satisfazerem a condição, ele retorna true , e se não false. Você pode usar ele para por exemplo verificar em um array de pessoas, se todas as pessoas são de maior de idade, diferente do comando [[SOME]] que procura apenas um elemento que quebre as condições, o every verifica se todos os elementos cumprem elas. Ele é mais usando para verificar se as condições são cumpridas em todos os elementos do array.

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

verificar se todos os elementos do array tem mais que 20 anos:

```
const idade = Lista.every(u => u.idade > 20 )
console.log(idade)
```

vai imprimir:
```
false
```
