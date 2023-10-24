tags: #resource/book #area/academic/redes
_____________________

O correio eletrônico é uma das primeiras (se não a primeira) grande aplicação de rede. Para seu funcionamento, são utilizados 3 [protocolos](Protocolo.md): SMTP para envio e POP3/IMAP para recebimento. Todos esses protocolos são naturais da [[Camada de Aplicação]].

## SMTP

O protoclo SMTP ocorre entre servidores de correio. Uma vez identificada uma mensagem na fila, o servidor de correio abre uma conexão [[TCP]] para outro servidor SMTP, realizando o envio.
## POP3

O protocolo de acesso POP3 é extremamente simples, sendo bem curto e fácil de ler. Entretanto, isso torna sua funcionalidade limitada.  Após a conexão entre cliente e servidor de correio, o protocolo ocorre em 3 etapas:

1. Autenticação -> Agente de usuário envia usuário e senha para ser autenticado
2. Transação -> Agente de usuário recebe e baixa as mensagens
3. Atualização -> Agente de usuário encerra a sessão e, então, as mensagens baixadas são apagadas
   
Esse protocolo não armazena informações de estado entre conexões.
## IMAP

O IMAP veio como uma resposta ao maior problema do POP3: O acesso dentre múltiplos dispositivos, umas vez que o POP3 deleta suas mensagens após download, característica não presente no IMAP. 

Além disso, o IMAP permite a associação de uma mensagem à uma pasta, como a Inbox, por exemplo e a obtenção de apenas uma parte da mensagem, útil para situações em que a largura de banda está reduzida.

Esse protocolo armazena informações de estado entre conexões.
## HTTP

Um adendo aos protocolos de correio é o [[HTTP]]. Através dele, nós podemos enviar e receber mensagens dos servidores de correio. Todavia, é importante frisar que a comunicação entre os servidores de correio ainda é realizada pelo protocolo SMTP.



![[FluxoEmail.excalidraw|1000]]

![[ProtocoloSMTP|1500]]