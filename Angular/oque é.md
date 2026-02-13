#### o angular é um framework de desenvolvimento frontend, sua estrutura se baseia em componentes, vc usa componentes para tudo, vc faz paginas usando eles e tudo mais, componentes são gerados por linha de comando ([[basic-comands]]) , todo componente possui a mesma estrutura:
 #### - component.<span style="color:rgb(255, 192, 0)">html</span>
 #### - component.<span style="color:rgb(0, 176, 240)">css</span>
 #### - componente<span style="color:rgb(0, 112, 192)">.spec.</span><span style="color:rgb(0, 112, 192)">ts</span>   <span style="color:rgb(120, 121, 125)">não mexer...</span>
 #### - componente.<span style="color:rgb(0, 112, 192)">ts</span>

#### No component.<span style="color:rgb(255, 192, 0)">html</span>, você ira escrever toda o seu esqueleto normalmente, como qualquer arquivo html. No component.<span style="color:rgb(0, 176, 240)">css</span> vc vai escrever todo o css do html do seu componente especifico. No seu component.<span style="color:rgb(0, 112, 192)">ts</span>  você vai escrever toda a logica das variáveis do seu componente e todo o resto para mostrar no seu html, porem suas conexões de API deve estar nun arquivo .service ([[service]]) , o arquivo .<span style="color:rgb(0, 112, 192)">ts</span> terá apenas suas logicas completas.
#### componente<span style="color:rgb(0, 112, 192)">.spec.ts</span> ... bem, jamais mexa nele

#### Exemplo de organização de componente:
![[../imgs/Pasted image 20260203085205.png]]