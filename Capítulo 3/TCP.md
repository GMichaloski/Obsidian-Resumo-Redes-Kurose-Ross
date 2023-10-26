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


## Informações mais detalhadas (Cap 3)

Propriedades:

- Um remetente, um destinatário
- Cadeia de bytes em ordem
- Paralelismo
- Buffer de envio e recepção
- Orientado a conexão (*handshaking*)
- Remetente não sobrecarrega destinatário

### Tempo de ida e volta & Timeout

*Como definir o valor de timeout do TCP?* Ideal é ser maior que o RTT, mas não tão maior. A questão é que o RTT varia bastante, como podemos estimar o RTT? 

Método iterativo:

$EstimatedRTT = (1 - \alpha) \cdot EstimatedRTT + \alpha \cdot SampleRTT$

1. *SampleRTT*: Intervalo de tempo entre a transmissão de um segmento e o recebimento do ACK, sem contar retransmissões. 
2. $\alpha$: Valor típico de 0.125

Com essa margem de RTT, basta adicionarmos uma "gordurinha" para o timeout ser maior, mas não tão maior. Para isso, fazemos o seguinte cálculo:

Primeiro, estimamos o DevRTT, que é uma estimativa iterativa do quanto o SampleRTT se desvia do EstimatedRTT:

$DevRTT = (1 - \beta) \cdot DevRTT + \beta \cdot |SampleRTT \cdot EstimatedRTT|$

1. $\beta$: Valor típico de 0.25

Com isso, finalmente, podemos definir o Timeout:

$TimeoutInterval = EstimatedRTT + 4 \cdot DevRTT$

### Controle de Fluxo

- Remetente não vai estourar buffer no destinatário transmitindo muitos dados rapidamente. TCP possui um serviço de compatibilização de velocidades.
- Destinatário anuncia espaço de buffer não usado no cabeçalho do segmento.

### Gerenciamento de Conexão

- Para conectar: *Handshaking* em três etapas:
  1. SYN -> "Bora conectar?"
  2. SYNACK -> "Bora!"
  3. ACK -> "Fechou!" (nesse segmento o remetente já pode aproveitar e enviar dados)

- Para fechar a conexão, quatro etapas:
1. Sistema final manda FIN para o servidor
2. Servidor manda FIN e ACK para sistema final. 
3. SF manda ACK para o servidor.
4. Servidor recebe ACK - conexão é fechada.