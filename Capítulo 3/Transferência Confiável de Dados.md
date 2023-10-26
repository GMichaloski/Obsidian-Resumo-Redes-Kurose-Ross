tags: #resource #area/academic/redes   
_____________________

Vamos ver os protocolos de Transferência Confiável de Dados existentes na [[Camada de Transporte]]:
### Rdt 1.0: Transferência confiável por canal confiável

- Sem erros de bit e sem perda de pacotes 
- Remetente envia dados para o canal subjacente
- Destinatário lê esses dados
  
  Máquinas de Estado Rdt 1.0:
![[Rdt1.0.png]]


### Rdt 2.0: Canal com erros de bits

- Canal subjacente pode trocar valores dos bits de um pacote -> Erro de bits!
- Reconhecimentos (ACKs): Destinatário envia uma mensagem ao remetente avisando que o pacote foi corretamente enviado
- Reconhecimentos Negativos (NAKs): Destinatário avisa ao remetente que o pacote teve erros. Com isso, o destinatário reenvia o pacote

![[Rdt2.0Remetente.png|350]]![[Rdt2.0Destinatario.png|200]]  

*Mas e se o ACK/NAK for corrompido?* 

### Rdt 2.1: Remetente trata de ACK/NACKs corrompidos!

Nesse caso, o remetente não sabe o que aconteceu no destinatário, então ele vai retransmitir. Entretanto, essa solução requer mais um detalhe: um tratamento de duplicadas por parte do destinatário, pois o remetente pode erroneamente enviar um pacote duas vezes. Nesse caso, um **número de sequẽncia** identifica cada pacote, assim, caso um pacote duplicado apareça, ele será descartado!

- Adiciona números de sequência ao pkt (apenas dois números, 0 e 1, bastam!)
- Lado remetente possui um estado para lembrar se pacote atual tem número de sequência 0 ou 1
- Lado destinatário verifica duplicada

![[Rdt2.1Remetente.png|500]]

![[Rdt2.1Destinatario.png|500]]

### Rdt 2.2: Protocolo sem NAK

- Igual ao RDT 2.1, mas utilizando apenas ACK
- Envia ACK para o último pacote recebido OK (identificado pelo número de sequência)
- ACK duplicado = Retransmissão do pacote atual 

### Rdt 3.0: Canais com erros e perda

Esse protocolo se baseia na possibilidade de um pacote (dados ou ACK) nunca chegar ao seu destino, o que causaria, nos pacotes anteriores, um estado de "infinita espera". Como esse protocolo resolve essa questão?

- Temporizador: Retransmite se não chegar um ACK dentro de uma janela de tempo razoável

Máquina de Estado lado remetente do Rdt 3.0 (o destinatário permanece igual ao Rdt 2.2):

![[Rdt3.0Remetente.png|500]]

Então o Rdt 3.0 é perfeito? Não! Ele possui um desempenho ruim. Isso acontece pois o protocolo limita o uso de recursos físicos! Essa teoria é demonstrada pela seguinte fórmula:

$U_{remet} = \frac{L/R}{RTT + L/R}$

1. **$U_{remet}$**: Esta é a fração de tempo em que o remetente está utilizando a rede. Ela indica quanto tempo o remetente passa transmitindo dados em relação ao tempo total.   
2. **$L/R$**: A razão entre o tamanho da carga útil (L) e a taxa de transmissão (R). Isso representa o tempo que o remetente levaria para transmitir os dados se a rede não tivesse atrasos ou limitações.
3. **$RTT$**: O Round-Trip Time é o tempo que leva para um pacote de dados viajar do remetente até o destinatário e retornar. Em outras palavras, é o atraso de ida e volta na rede. O RTT é crucial para determinar o desempenho da rede, uma vez que ele inclui a latência da rede.

### Protocolos com paralelismo 

Consistem no envio de múltiplos pacotes, sem esperar os ACKs.

- Deve possuir mais números de sequência
- Buffering no remetente e/ou destinatário
  
  $U_{remet} = \frac{N * L/R}{RTT + L/R}$
  
1. $N$: quantidade de pacotes enviados na rajada

### Go-Back-N:

- Remetente envia até N pacotes não reconhecidos na pipeline
- Remetente tem temporizador para pkt sem ACK mais antigo (se não chegar, manda todos os pacotes sem ACK sequencialmente)
- Destinatário só envia ACKs cumulativos - Não envia se tiver uma lacuna
  
  
### Repetição seletiva:

- Remetente envia até pacotes não reconhecidos na pipeline
- Remetente mantém temporizador para cada pkt sem ACK
- Destinatário reconhece ACKs individuais