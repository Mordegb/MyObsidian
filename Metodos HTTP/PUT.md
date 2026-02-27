#### O metodo put é comunmente usado para atualizar um recurso ou criá-lo ,caso ele não exista.
Uma difrença é que o metodo put é indepotente, basicamente deve atualizar todas as informações de um recurso especifico, pq ele faz a substituição, é como se quisesse mudar o nome de uma pessoa no banco de dados, tivesse que atualizar todos os outros campos de informação tambem.


#### Se hipoteticamente tiver um sistema de usuarios e vc quiser atualizar co campo "Nome" do objeto joão, voçe deve enviar todos os outros campos do obejto junto ou eles vão ficar sem nada.
```
{
 "nome": "João Silva", 
 "email": "joao.silva@email.com",
 "biografia": "Desenvolvedor Backend e entusiasta de café." 
 }
```

