#### Headers é o nome que se dá ao [[metadados]] que são enviados e ou recebidos através de uma requisição HTTP. dentro do headers vc especifica o tipo de dado que vc vai receber ou enviar, sendo eles json, xml e muitos outros, como mostrado no [[Content-Type e Accept]]. Tudo que lida com esse tipo de coisa vc coloca dentro do headers ,inclusive autenticação e acesso a tokens.

###### Por exemplo:
```
getMe(): Observable<any> {
	return this._http.get(`${environment.api}/auth/me`, {
	headers: {
		'Authorization': `Bearer ${sessionStorage.getItem('access_token')}`,
		'Accept': 'application/json'
	   }
    });
}
```

#### o Accept diz o tipo de informação que vamos receber, no caso formato json.,e o Authorization é para manter logado no email e mais sla oq (ainda vou estudar).