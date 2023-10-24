tags: #resource/book #area/academic/redes
_____________________

Uma aplicação de rede é um programa que roda em diferentes [[Hosts]] que conversam entre si. Entretanto, nós podemos deixar os dispositivos do núcleo da rede de fora, uma vez que eles não executam aplicações do usuário.

Um **processo** é um programa rodando dentro de um hospedeiro. Para aplicações de rede, processos em diferentes hospedeiros se comunicam através de **mensagens**, sendo o **cliente** aquele que inicia a comunicação e **servidor** aquele que espera para ser contactado.

Esses processos não são identificados apenas pelo endereço IP, uma vez que muitos processos podem rodar no mesmo hospedeiro. Para isso, o identificador inclui, além do **IP**, um **número de porta**. Um bom exemplo é quando executamos um serviço de backend que sobe duas rotas: uma na porta 8000 e uma na 8001.