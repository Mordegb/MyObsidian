A função findIndex() , lê as condições que você coloca dentro dela, e procura no array até achar o primeiro elemento que bata com as condições, e quando ele achar esse elemento vai retornar seu index. Por exemplo, achar uma pessoa dentro de array e ele vai retornar o índice dela de no array.é usado comumente para achar pessoas e conseguir seu indice no array.

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

Pegar um índice de um objeto:
```
const Index = Lista.findIndex(u => u.nome === 'cadu')
console.log(index)
```

vai imprimir:
```
2  => indice de cadu no array
```