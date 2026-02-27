#### o arquivo service é um arquivo de arquivo que deve ficar em uma pasta especifica de nome "<span style="color:rgb(255, 255, 0)">service</span>"  a pasta service  é gerada com um arquivo <span style="color:rgb(0, 112, 192)">.ts</span>  junto por linha de comando( [[basic-comands]]), dentro do arquivo <span style="color:rgb(0, 112, 192)">.ts</span>  da pasta service, voçe vai colocar a logica de comunicação com sua API, ela não fica no <span style="color:rgb(0, 112, 192)">.ts</span>  do seu componente diretamente, vc o colocar na pasta service e importa no seu componente com um construtor pra poder usar 
#### ![[../imgs/Pasted image 20260202222757.png]]
#### eis ai um exemplo de como ela deve ficar a pasta.

#### No service tambem em projetos mais complexos, vai interagir com [[Headers]] para a cominação com a API

#### Por exemplo:
![[../imgs/Pasted image 20260226132656.png]]

#### Vc lida mais ou menos assim.