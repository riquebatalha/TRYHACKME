# Relatório da sala [Introductory Networking](https://tryhackme.com/r/room/introtonetworking)


## Introdução

O OSI (Open Systems Interconnection) é um modelo padrão no qual demonstra a teoria por trás de uma rede de computador. Na prática, ela é mais compacta que o modelo TCP/IP.
o modelo OSI, em muitos aspectos, é mais fácil de obter uma compreensão inicial.

## Camada 7 - Aplicação:
A camada de aplicação no modelo OSI fornece opções de rede para  programas que estão rodando em um computador. Funciona quase exclusivamente com aplicativos, fornecendo uma interface para eles usarem a fim de transmitirem dados. Quando dados são enviados para à camada de aplicação, ele são transmitidos para a camada de Apresentação

## Camada 6- Apresentação:
A camada de Apresentação recebe os dados da camada de Aplicação. Esses dados tendem a ser em um formato que os aplicativosentendem, mas não está necessariamente em um formato padronizado que pode ser compreendido pela camada de aplicaçãono computador receptor.

## Camada 5- Sessão:
Quando a camada de sessão recebe no formato correto os dados da camada de apresentação, ela verifica se ele consegueestabelecer uma conexão com outro computador na rede. Se ele não conseguir ele retorna um erro e oprocesso não prosseguirá. Se a sessão pode ser estabelecida, então é trabalho da Camada de Sessão mantê-la, bem comocooperar com a camada de sessão do computador remoto para sincronizar as comunicações. A camada de sessão é particularmente importante porque a sessão que ela cria é exclusiva da comunicação em questão. Issoé o que permite que você faça várias solicitações para diferentes endpoints simultaneamente, sem que todos os dados se misturem (pense em abrir duas guias em um navegador da web ao mesmo tempo)! Quando a camada de sessão registra com êxito uma conexão entre o host e o computador remoto, os dados são transmitidos para a camada 4: a camada de transporte.

## Camada 4- Transporte:
A camada de transporte é uma camada muito interessante que desempenha inúmeras funções importantes. Seu primeiro objetivo é escolher o protocolo pelo qual os dados serão transmitidos. Os dois protocolos mais comuns na camada de transporte são TCP (Transmission Control Protocol) e UDP (User Datagram Protocol); com TCP a transmissão é baseada em conexão, o que significa que uma conexão entre os computadores é estabelecida e mantida durante a solicitação. Isso permite uma transmissão confiável, pois a conexão pode ser usada para garantir que todos os pacotes cheguem ao lugar certo. Uma conexão TCP permite que os dois computadores permaneçam em comunicação constante para garantir que os dados sejam enviados a uma velocidade aceitável e que quaisquer dados perdidos sejam reenviados. Com o UDP, o oposto é verdadeiro; pacotes de dados são essencialmente lançados no computador receptor - se ele não conseguir acompanhar, esse é o problema (é por isso que uma transmissão de vídeo por algo como o Skype pode ser pixelizada se a conexão estiver ruim). O que isto significa é que o TCP normalmente seria escolhido para situações em que a precisão é favorecida em detrimento da velocidade (por exemplo, transferência de arquivos ou carregamento de uma página da Web), e o UDP seria usado em situações em que a velocidade é mais importante (por exemplo, streaming de vídeo. 
OBS: TCP Com um protocolo selecionado, a camada de transporte divide a transmissão em pedaços pequenos (no TCP eles são chamados de segmentos, no UDP eles são chamados de datagramas), o que facilita a transmissão bem-sucedida da mensagem.

## Camada 3- Rede:
A camada de rede é responsável por localizar o destino da sua solicitação. Por exemplo, a Internet é uma rede enorme; quando você deseja solicitar informações de uma página da web, é a camada de rede que pega o endereço IP da página e descobre o melhor caminho a seguir. Nesta fase, estamos trabalhando com o que é conhecido como endereçamento lógico (ou seja, endereços IP), que ainda são controlados por software. Endereços lógicos são usados para ordenar as redes, categorizando-as e permitindo-nos classificá-las adequadamente. Atualmente, a forma mais comum de endereçamento lógico é o formato IPV4, com o qual você provavelmente já está familiarizado (ou seja, 192.168.1.1 é um endereço comum para um roteador doméstico).

## Camada 2- Enlace:
A camada de enlace de dados concentra-se no endereçamento físico da transmissão. Ele recebe um pacote da camada de rede (que inclui o endereço IP do computador remoto) e adiciona o endereço físico (MAC) do terminal receptor. Dentro de cada computador habilitado para rede há uma placa de interface de rede (NIC) que vem com um endereço MAC (Media Access Control) exclusivo para identificá-lo.

Os endereços MAC são definidos pelo fabricante e literalmente gravados no cartão; eles não podem ser alterados - embora possam ser falsificados. Quando as informações são enviadas através de uma rede, na verdade é o endereço físico que é usado para identificar exatamente para onde enviar as informações.

Além disso, também é função da camada de enlace de dados apresentar os dados em um formato adequado para transmissão.

A camada de enlace de dados também desempenha uma função importante ao receber dados, pois verifica as informações recebidas para ter certeza de que não foram corrompidas durante a transmissão, o que pode acontecer quando os dados são transmitidos pela camada 1: a camada física.

## Camanda 1- Física


