tags: #resource/book #area/academic/redes 
_____________________

Literalmente tudo na internet vai sempre ter algum delay para ser transmitido. Esse delay ocorre por diversos tipos de atraso, que ocorrem em diversas camadas da rede:

### Atraso de Processamento

*Camada: Aplicação* 

É o tempo necessário para processar o cabeçalho do pacote e verificar erros de bit.

Seu valor normalmente é dado. 

### Atraso de Fila

*Camada: Enlace*

É o tempo esperando para sair do enlace. Depende do nível de congestionamento do roteador em que esses dados forem chegar.

$D_{fila}=\frac{L \cdot a}{R}$, sendo
$L$ o tamanho do pacote (bits, kbits, Mbits, etc.)
$a$ a taxa média de chegada do pacote
$R$ a taxa de transmissão do roteador (bits/s, kbits/s, Mbits/s, etc.)
### Atraso de Transmissão

*Camada: Transporte*

É o tempo para enviar os bits ao enlace.

Calculado por:

$D_{trans} = \frac{L}{R}$
Sendo:
$D_{trans}$ o atraso de transmissão
$L$ o tamanho do pacote (bits, kbits, Mbits, etc.)
$R$ a taxa de transmissão do roteador (bits/s, kbits/s, Mbits/s, etc.)
### Atraso de Propagação

*Camada: Enlace*

É o tempo que o dado demora para percorrer o enlace. Por exemplo, um dado demoraria muito mais para atravessar um continente do que uma rua.

Por default, o valor assumido é de $2 \cdot 10^8$ m/s a $3 \cdot 10^8$ m/s

### Atraso de Nodal

É o tempo de atraso geral entre 2 nós.

Ele pode ser calculado como:

$d_{nodal} = d_{proc} + d_{fila} + d_{trans} + d_{prop}$ 

![[OndeOcorreCadaTipoDeAtraso|1000]]

