---
tags:
  - programação
---
#programação

O método de organização Bubble sorted , é um método de organização que organização que organiza os números dentro de um array do menor para o maior, ou seja, em ordem crescente.

EXEMPLO:
```
for(int i = 0; i < 5; i++){
	for(int j = 0; j < 5 - 1; i++){
		if(vetor[j] > vetor[j + 1]){
			int temp = arr[j];
			arr[j] = arr[j + 1];
			arr[j + 1] = temp;
		}
	}
}
```



Bubble sorted reverso:
se baseia no mesmo método de organização  igual a anterior, mas esse organiza do maior para o menor, ou seja o array esta organizado em ordem decescente.

EXEMPLO:
```
for(int i = 0; i < 5; I++){
	for(int j = 0; j < 5; i++){
		if(vetor[j] < vetor[j + 1]){
			int temp = vetor[j + 1];
			vetor[j + 1] = vetor[j];
			vetor[j] = temp	;		
			
		}
	}
}
```