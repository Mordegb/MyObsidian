
**Algoritimo BuscaAproximada(L,X):**
`N = tamanho de L`

`se N = 0:`
	`retorne nulo`
  
`se X<=L[1] então:`
	`retorne L[1]`

`se X>=L[N] então:`
	`retorne L[N]`
	
`esq = 1`
`dir = N`
`enquanto esq <= dir:`
	`meio = piso((esq + dir) / 2)`
	  se: L[<span style="color:rgb(0, 0, 0)">meio</span>] = X:`
     `retorne L[meio]`
  
  `senão se L[meio] < X:`
	`esq = meio + 1`
  
  `senão:`
	`dir = meio - 1`

`dist_esq = ValorAbsoluto(L[esq] - X)`
`dist_dir = ValorAbsoluto(L[dir] - X)`

`Se dist_dir <= dist_esq:`
	`retorne L[dir]`
`senão:`
	`retorne L[esq]`