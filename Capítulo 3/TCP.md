tags: #resource/book #area/academic/redes
_____________________

É um [[Protocolo]] da [[Camada de Transporte]] que opera entre [aplicações](Camada%20de%20Aplicação.md), assim como o [[UDP]].

- Serviço orientado a conexão:
  O protocolo TCP possui um comportamento em que cliente e servidor realizam um "Handshake", i.e., eles trocam informações da camada de transporte antes de qualquer troca de pacotes, permanecendo conectadas enquanto necessário. Ao fim, a aplicação encerra essa conexão.
   
- Serviço confiável de transporte:
  Com o uso do protocolo TCP, podemos ter certeza que os dados chegarão em ordem, sem erro e sem duplicidades.

- Controle de congestionamento:
  Voltado para o bem-estar da internet, e não necessariamente para a efetividade de uma aplicação, o protocolo TCP possui um mecanismo para controle de congestionamento, que limita a capacidade de transmissão de um processo quando a rede está congestionada.

O protocolo TCP pode ser aprimorado através do uso do [[SSL]] na camada de aplicação. 