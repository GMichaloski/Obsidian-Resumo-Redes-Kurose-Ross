tags: #resource/book #area/academic/redes 
_____________________

O HyperText Transfer Protocol é um [[Protocolo]] presente na [[Camada de Aplicação]] da rede que atua tanto no lado cliente quanto no lado servidor. 

Esse protocolo define como são realizadas as interações cliente-servidor na Web. Por exemplo, através do HTTP você pode obter uma página web através de uma URL. As URL's podem ser divididas em duas partes: *hostname* e *caminho do objeto*, como no exemplo:

`www.hostname.com/path/to/object`

O protocolo HTTP se conecta ao servidor através de uma conexão [[TCP]].  Com isso, ele possui a confiabilidade de envio de seus dados, não sendo sua responsabilidade se preocupar com isso. 

O protocolo HTTP não armazena estados de clientes, realizando o envio independente de fatores externos. Por exemplo, se o usuário realizar a mesma requisição duas vezes, ela será enviada duas vezes. Essa característica define o HTTP como um **protocolo sem estado.**

As respostas à requisições HTTP seguem os seguintes códigos:

| Código | Mensagem                   | Significado                                                     |
| ------ | -------------------------- | --------------------------------------------------------------- |
| 200    | OK                         | Requisição bem sucedida                                         |
| 301    | Moved Permanently          | Objeto movido. O software recuperará automaticamente o novo url |
| 400    | Bad Request                | Requisição não pôde ser atendida pelo servidor                  |
| 404    | Not Found                  | O documento requisitado não existe                              |
| 500    | Internal Server Error      | Erro interno do servidor                                        |
| 505    | HTTP Version Not Supported | Versão do HTTP requisitada não é suportada pelo servidor                   |

### Protocolo HTTP Não Persistente

![[ProtocoloHTTPNaoPersistente|1000]]

O tempo de resposta do Não Persistente é:

$N \cdot 2RTT + d_{trans}$, sendo:

$RTT$: Tempo para um pequeno pacote ir e voltar ao servidor
$N$: Quantidade de objetos

Obs: As $N$ requisições sobressalentes podem ser feitas paralelamente, o que reduziria para $2 \cdot 2RTT + d_{trans}$
### Protocolo HTTP Persistente

![[ProtocoloHTTPPersistente|1000]]

O tempo de resposta do Persistente é:
$2RTT + d_{trans}+ N \cdot (RTT + d_{trans})$ 
$RTT$: Tempo para um pequeno pacote ir e voltar do servidor
$N$: Quantidade de objetos

![[DiagramaHttpNaoPersistente|1000]]
