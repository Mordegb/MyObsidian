##### o Contet-Type é usado geralmente dentro de um [[Headers]] , usando os metodos  [[../Metodos HTTP/POST|POST]] , [[../Metodos HTTP/GET|GET]] , [[../Metodos HTTP/PUT|PUT]] ou [[../Metodos HTTP/PATCH|PATCH]]. 

#### O Content-Type é usado para enviar dados para APIs,quando lidamos com API restful que funcionam e lidam com formatos JSON .

```
Headers{
	'Content-Type': 'application/json'
}
```
##### Isso significa que ta sendo enviado para a API os dados estruturados em formato JSON.


#### O Accept é o processo contrario, ele informar o tipo de informação que ele recebe
```
Headers{
	'Accept': 'application/json'
}
```
##### aq significa o tipo de dado que o front vai receber basicamente.