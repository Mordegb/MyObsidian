
#### O posté basicamente o metodo de enviar ou adicionar algo.

#### 1.  Você escreve seu texto e clica em "Publicar".
#### 2. O navegador envia um **POST** para `/textos/123/comentarios`.
#### 3. O servidor recebe seu texto, cria um novo espaço no banco de dados e gera um ID (ex: Comentário nº 500).

#### A diferença é que se vc escrever o mesmo objeto e por exemplo apertar publicar 2 vezes, ele não vai criar um objeto no banco de dados e dps atualizar o mesmo, ele vai criar 2 objetos iguais. (oque obviamente pode dar problema uma hora...)