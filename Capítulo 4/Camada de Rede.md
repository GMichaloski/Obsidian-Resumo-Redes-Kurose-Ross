tags: #resource/book #area/academic/redes 
_____________________

Essa camada é responsável por levar o segmento de transporte do hospedeiro emissor ao receptor. O remetente encapsula esses segmentos em **datagramas**, que serão desmontados e enviados para a camada de suporte pelo destinatário.

Cada roteador possui protocolos da camada de rede. 

### Repasse X Roteamento

- Repasse: É o ato de mover os pacotes da entrada de um roteador para a saída do mesmo.
- Roteamento: É o ato de escolher, através de [[algoritmos de roteamento]], qual rota os pacotes devem tomar rumo ao destino.  

### Estabelecimento de Conexão 

Enquanto a [[camada de transporte]] é responsável pela conexão dentre dois processos, a camada de redes une dois hospedeiros (e os roteadores entre eles).

Assim, antes mesmo do envio dos datagramas, os hospedeiros e os roteadores criam uma conexão virtual. É uma espécie de *handshaking* da camada de redes!

### Modelo de Serviço de Rede

- Datagramas individuais:
	- Entrada garantida
	- Entrega garantida com atraso limitado
  
- Fluxo de datagramas: 
	- Entrega de datagrama na ordem
	- Largura de banda mínima garantida
	- Restrição sobre mudanças no espaçamento entre pacotes
	  

![[ModelosDeServico.png]]

### Rede de Circuitos Virtuais

- Estabelecimento de conexão para cada chamada antes da troca de dados (*handshaking*)
- Cada pacote possui identificador VC
- Roteadores mantém estado para cada conexão
- Recursos dedicados
- Sistemas finais "burros" -> telefones
- Complexidade dentro da rede

### Rede de Datagrama

- Serviço sem conexão
- Roteadores sem estado sobre conexões fim a fim
- Pacotes repassados usando endereço do hospedeiro de destino
- Pacotes podem tomar caminhos diferentes para chegar ao mesmo destino (depende do momento)
- Sistemas finais "inteligentes" -> computadores
- Simples dentro da rede, complexo na borda

### Roteador

- Executa algoritmos de roteamento
- Passa datagramas do enlace de entrada para o enlace de saída

*Quanto armazenamento em buffer?*
$\frac{RTT \cdot C}{\sqrt{N}}$

1. C -> Capacidade do enlace
2. N -> Quantidade de fluxos

### Algoritmos de Roteamento

São algoritmos que buscam encontrar o caminho mínimo de um grafo. Em termos de rede, são métodos que buscam o menor tempo de transmissão entre 2 roteadores.

Existem 2 tipos:

- Estado de Enlace: Nós já sabemos da condição completa do grafo, toda a informação de custo
  ex: Djikstra
  
- Vetor de Distância: Roteador só conhece seus vizinhos, processo iterativo. 
  ex: Bellman-Ford

Além disso, o algoritmo pode ser estático, quando as rotas mudam lentamente com o tempo, ou dinâmico, em que as rotas são atualizadas periódicamente, muito mais rápido, em resposta a mudanças no custo do enlace.

### Roteamento na Internet

Exemplos de protocolos que ocorrem IntraAS, isto é, que ocorrem dentro de um único Sistema Autônomo: RIP, OSPF, IGRP


1. **RIP (Routing Information Protocol)**:
   - RIP utiliza uma métrica simples (contagem de saltos) para determinar as melhores rotas e atualiza periodicamente as informações de roteamento entre os roteadores.
1. **OSPF (Open Shortest Path First)**:
   - O OSPF é altamente escalável, suporta tipos diferentes de redes e permite o uso de métricas mais complexas para calcular as melhores rotas.
2. **IGRP (Interior Gateway Routing Protocol)**:
   - O IGRP usa uma métrica baseada em largura de banda e atraso para determinar rotas, tornando-o mais flexível que o RIP em termos de escolha de rotas.

  Estes protocolos são usados para roteamento dentro de um único Sistema Autônomo, auxiliando na determinação das melhores rotas e na atualização das tabelas de roteamento para garantir que os pacotes de dados sejam encaminhados eficientemente dentro da rede interna da organização.