tags: #resource/book #area/academic/redes
_____________________

A internet é uma infraestrutura de redes que atende diversos serviços e aplicações, uma rede de redes que conecta bilhões de [sistemas finais](Hosts.md) entre si.É importante entender que a internet não é algo que "está no ar", mas, uma grande infraestrutura física que conecta esses dispositivos. 

Essas conexões são realizadas pelos chamados [enlaces](Camada de Enlace) de comunicação e por comutadores. Por elas, os sistemas finais enviam **pacotes**, que são fragmentos do dado original junto a um cabeçalho de informação.

Os sistemas finais acessam a Internet por meio de [[Provedores de Serviço de Internet]]. 

Esses sistemas de conexão de internet podem ser divididos entre **periferia** e **núcleo** da rede. O nome é autoexplicativo, a periferia é responsável por entregar para cada casa e o núcleo, por sua vez, é a malha de roteadores interconectados.

Notável que cada etapa da transmissão entre dados na internet causa um [[Atraso]].

![[BordaEPeriferiaDaRede|1000]]

Dentre as estratégias de transmissão de dados por uma rede de enlaces e comutadores: **comutação de circuitos** e **comutação de pacotes**.  

### Comutação de Circuitos

Nessa estratégia, temos as seguintes características:

- Recursos dedicados sem compartilhamento
- Desempenho tipo circuito (garantido)
- Utiliza toda a largura de banda do enlace
- Exige preparação da chamada

Vantagem em relação à Comutação de Pacotes -> Garantia de que os recursos são reservados ao longo da comunicação e menor delay (justamente por ser reservado).
### Comutação de Pacotes

- Usuários compartilham recursos da rede
- Cada pacote usa a largura de banda total do enlace
- Recursos usados quando necessários
- Disputa por recursos 

Vantagem em relação à Comutação de Circuitos -> Melhor compartilhamento de banda e mais simples implementação.

### Camadas da Rede

A rede é dividida entre camadas. Essa divisão se dá por dois motivos:
- Facilitar identificação e relação dentre partes complexas do sistema
- Facilitar manutenção e atualização através de [[modularização]]

Contudo, essa divisão contém pontos negativos, sendo eles:
- Duplicação de serviços
- Isolamento de informações importantes ("queria acessar informação de outra camada")



| Camadas        | Dado |
| -------------- | -------- |
| [[Camada de Aplicação]]  | Mensagem        |
| [[Camada de Transporte]] | Segmento        |
| [[Camada de Rede]]       | Datagrama        |
| [[Camada de Enlace]]     | Quadro        |
| Camada Física               | -  |

