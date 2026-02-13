A função some() faz um pergunta para o array , ele lê o array e verifica se pelomenos um dos elementos do array cumpre essa condição que voçe colocou dentro dele, se então pelomenos um dos elementos cumprir essa condição, ele retorna true, se não retorna false.
Voce pode usar a função some por exemplo, para verirficar se a idade de todos os elementos de um array de pessoas é maior que 18 anos sem querer criar um novo array. a função some é mais usada para verificar condições,comoele olha elemento por elmento verificando uma condição e retorna um booleano, é bem util para informações rápidas.

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

Verificar se tem algum usuario na lista que não esta ativo:
```
const TemInativo = Lista.some(u => u.ativo === false)
console.log(TemInativo)
```

Vai imprimir:
```
true
```
