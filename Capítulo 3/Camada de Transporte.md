tags: #resource/book #area/academic/redes 
_____________________
A função dessa camada é oferecer **Comunicação Lógica** entre processos de aplicação rodando em hospedeiros diferentes.

Por isso, esses protocolos rodam nos próprios sistemas finais. Sua função enquanto remetente é dividir a mensagem da aplicação em **segmentos** para encaminhar para a [[Camada de Rede]]. Por sua vez, a sua função do lado destinatário é remontar a mensagem vinda da camada de rede e encaminhá-la para a [[Camada de Aplicação]].

Existem dois [protocolos](Protocolo) para essa camada: o [[UDP]] e o [[TCP]].
### Qual a diferença entre a camada de transporte e a camada de rede?

A camada de transporte é responsável pela comunicação lógica entre processos, enquanto a camada de rede é responsável por essa comunicação entre hospedeiros.

Traduzindo, a camada de transporte é responsável pela comunicação entre as aplicações, enquanto a camada de rede realiza o diálogo entre os hospedeiros.

Numa analogia real, a camada de transporte é o carteiro e a camada de rede é a central de correios. O carteiro é responsável por fazer a comunicação entre as casas (hospedeiros)  e a central. Por sua vez, os correios vão organizar as grandes quantidades de cartas (datagramas) e envia para as outras centrais, onde os carteiros correspondentes poderão levar as cartas (pacotes) ao seu destino final.


### Multiplexação e Demultiplexação

**Multiplexação**: No transmissor, muitos dados de sockets são reunidos e identificados pelo cabeçalho de transporte.

**Demultiplexação**: No receptor, utiliza-se o cabeçalho para entregar os segmentos aos sockets corretos.

*Mas como a demultiplexação funciona?* O hospedeiro recebe um datagrama IP, que possui endereço IP origem, destino e 1 segmento da camada de transporte. Esse segmento, por sua vez, possui um número de porta de origem, número de porta de destino e a mensagem em si. Com base nessas informações de endereço, o hospedeiro direciona o segmento ao socket apropriado.

A demultiplexação pode ser de dois tipos: *orientada* e *não orientada* a conexões. Eles se diferenciam em sua raiz: os orientados a conexão encaminham os dados para endereços previamente especificados, como portal de origem e destino. Essa abordagem é a utilizada em protocolos como o TCP. Por outro lado, a não orientada a conexão não requer informação adicional nem um *handshake*, assim sendo, os dados são roteados com base em informações armazenadas no próprio pacote, como endereços de IP e portas. Por exemplo, um programa python (como visto na atividade de sockets) consegue criar uma porta UDP através do comando `clientSocket = socket(socket.AF_INET, socket.SOCK_DGRAM)`.