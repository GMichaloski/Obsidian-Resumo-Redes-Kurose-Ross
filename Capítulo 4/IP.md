tags: #resource #area/academic  
_____________________

### Fragmentação e Reconstrução

O IP, Internet Protocol, possui um grande datagrama, que é fragmentado em partes menores devido ao MTU (tamanho máx. de transferência) dos enlaces de rede. Ele é reconstruído apenas quando chega ao destino final. 


### Endereçamento IPV4

- Endereço IP -> Identificador de 32 bits para interface de hospedeiro e roteador
- Sub-redes -> Dispositivo mantém o identificador do roteador e altera o final, criando seu id único. Com isso, cada dispositivo pode alcançar um ao outro fisicamente sem roteador intermediário.  

*Como se obtém um endereço IP?* É fornecido pelo administrador do sistema em um arquivo. Além disso, 2 protocolos precisam ser destacados por essa função:

- DHCP: Recebe endereço dinamicamente do servidor
- NAT: Unificar subredes em um único endereço, mas com diferentes portas.


### ICMP

O Internet Control Message Protocol é um protocolo que, como sugerido pelo nome, é usado por hosts e roteadores para comunicar informações da rede.

É utilizado para fazer o traceroute.


### IPV6

Existe pois os 32 bits disponíveis para endereço do IPV4 em breve ficarão sem novas opções. 

- Cabeçalho de 40 bytes de tamanho fixo
- Não fragmenta
- ICMP próprio e atualizado -> ICMPv6

*Mas como será feita a modernização, já que não podemos substituir todos os roteadores?* Lógica de túnel!

![[ImplantacaoTunel.png]]
