tags: #resource/book #area/academic/redes
_____________________

Basicamente, é o [[Protocolo]] da [[Camada de Transporte]] entre [aplicações](Camada%20de%20Aplicação.md) oposto ao [[TCP]]. Ele é bem mais simples e leve que sua contraparte. Entretanto, alguns de seus ônus são críticos.
  
- Serviço não orientado a conexão:
  No UDP, não há comunicação prévia à troca de pacotes.
  
- Não confiável:
  Esse protocolo não garente que os pacotes serão entregues. Além disso, os dados podem chegar errados, desorganizado e/ou duplicados.
  
- Sem mecanismo para tratar congestionamento:
  Um processo pode bombardear dados para a [[Camada de Rede]] o quanto quiser.

## Informações mais detalhadas (Cap 3)

- O protocolo UDP é bem direto ao ponto. Ele em nada altera o IP, a aplicação fala diretamente com o IP. Ele pega a mensagem da aplicação, anexa os campos de portas origem-destino, mais dois outros pequenos campos e passa para a camada de rede!

### Mas então qual a utilidade do UDP?

- Estabelecimento de conexão gera atraso, UDP, portanto, é mais rápido
- Simples de implementar
- Cabeçalho de segmento pequeno
- Sem controle de congestionamento, assim, pode transmitir o mais rápido possível

### Use cases

- Streaming de multimídia (tolerante à perdas -> o que é um pacote em meio a um filme de dados?)
- DNS
- SNMP
  
### Soma de verificação 

Essa etapa é essencial para detectarmos erros no segmento transmitido. 

A função do remetente é colocar o valor da **soma de verficação** no campo de soma de verificação UDP, para então o destinatário realizar o cálculo com base no segmento recebido e verificar se o valor bate com o do campo de soma de verificação.

> [!WARNING] Lembre-se!  
> A verificação do campo de soma **NÃO** garante que o arquivo não possui erros.



