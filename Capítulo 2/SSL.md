tags: #resource/book #area/academic/redes
_____________________

Não é realmente um terceiro [[Protocolo]] de transporte entre aplicações da escala do [[UDP]] ou [[TCP]], mas uma versão aprimorada do segundo. Nessa lógica, ele realiza tudo o que o [[TCP]] faz e mais um pouco!

A principal vantagem no uso do SSL é a condificação dos dados que ele disponibiliza. 

Para utilizar esse protocolo, deve-se incluir código SSL da aplicação tanto na parte cliente como no servidor. 

Quando uma aplicação usa SSL, o processo remetente envia os dados para o [[Socket]] SSL de um Host emissor, que, por sua vez, os codifica e envia para o [[Socket]] [[TCP]]. Os agora codificados dados percorrem a internet até o [[Socket]] [[TCP]] do destinatário, que passa para o SSL que, enfim, os decodifica.

Socket SSL (E) -> Socket TCP (E) -> Socket TCP (R) -> Socket SSL (R)

(E) -> Emissor
(R) -> Receptor