# Uma breve história...

  _Caso queira pular diretamente para o conteúdo, esse tópico é apenas para contextualizar o leitor acerca do que é a linguagem Elixir, desde o seu princípio no Erlang até o nascimento da linguagem que será o foco desse 4noobs. O conteúdo prático encontra-se [no próximo tópico](/content/primitive-types.md)_

`Elixir` é uma linguagem de programação moderna, focada e especializada na construção de sistemas escaláveis em larga escala, de forma distribuída e tolerante à falhas para a `máquina virtual do Erlang`, a `BEAM`.

### ***Espera! Antes de entrar a fundo no que é o Elixir, vamos entender o que é o Erlang!***

  * `Erlang` é uma linguagem criada pela empresa de `Telecom` Ericsson, visando ajudar os desenvolvedores a lidarem com os desafios de construir um sistema de alta disponibilidade e com downtime quase nulo, visto que: Um telefone deve sempre operar independente do número de chamadas simultâneas que estejam ocorrendo e também independente de bugs inesperados ou upgrades de hardware e software.

  * Originalmente, imaginava-se que a utilidade da linguagem se dava apenas nos sistemas de telecomunicações, mas foi um equívoco gigantesco, visto que nos dias de hoje, os sistemas se baseiam em comunicação, colaboração, servidores e processos em tempo real! Dito isso, a linguagem é utilizada direta e indiretamente em diversos segmentos da industria, tais como:

    * Sistemas de saúde: `English National Health Service (NHS).`.

      * Com mais de  65 milhões de requisições por dia o NHS manteve-se 99.999% disponível por mais de 5 anos.

    * Jogos multiplayer: `Riot games`.

      * Com mais de 7,5 milhões de jogadores simultâneos, a empresa utiliza `Erlang` para lidar com as filas de mensagens no chat em tempo real e sem interrupções.

    * Videogames: `Nintendo Switch`.

      * Foram vendidas mais de 34 milhões de consoles; o sistema utiliza um sistema de mensageria baseado em `Erlang` para lidar com as milhões de conexões concorrentes.

    * Redes sociais: `WhatsApp`.

      * Fila de mensagens, tolerância à falhas, esse em questão dispensa comentários.

  * Tudo isso só pôde ser possível graças aos pilares da plataforma de desenvolvimento do `Erlang`:

    #### **1. Alta Disponibilidade**
  
    Se tratando de `Erlang`, sua alta disponibilidade se dá por diversos tipos de fatores, dentre eles: `tolerância à falhas`, `escalabilidade`, `distribuição`, `responsividade` e `atualização ininterrupta`. Tais funções transformam a linguagem em algo perfeito e resiliente nas mais diversas circunstâncias, mas dizer tudo isso é muito fácil, a primeira camada das coisas é a mais bonita, no entanto, temos diversos desafios técnicos nos fatores acima para fornecer um sistema que esteja disponível 100% do tempo:

    * ***Tolerância à falhas:*** Um sistema **tem** que se manter funcionando mesmo diante de imprevistos. Componentes podem falhas, bugs podem surgir do absoluto nada e infinitos erros podem acontecer, isso sem falar da rede caindo e do pior dos casos: ***A BEAM MORRER***. Independente de tudo isso, é necessário encontrar o ponto de impacto, se recuperar e manter o sistema de pé.

    * ***Escalabilidade:*** Essa é a questão mais polêmica de toda a tecnologia, entre arquiteturas de código, boas práticas e afins, o tópico sempre se converge com "o quão escalável isso é?". Um sistema deveria estar apto para lidar com ***QUALQUER*** tipo de carga. Mas dito isso, é claro que você não vai comprar uma quantidade absusiva de hardware só para o caso de, ocasionalmente, o planeta todo decidir utilizar algo seu. Mas o sistema deve estar apto para responder ao aumento repentino de carga adicionando recursos de hardware aos poucos e sem nenhuma intervenção de softwares. Idealmente deveria ser possível sem a necessidade de interromper o sistema, aumentar a capacidade para só então subí-lo novamente. 

    * ***Distribuição:*** Para fazer um sistema que nunca para, é necessário rodá-lo em diversas máquinas. Isso promove uma estabilidade geral, em que se uma máquina para por algum motivo, outra pode continuar, por assim em diante e simultaneamente também. Além disso, Isso lhe dá poder para escalar horizontalmente - você pode aumentar a taxa de processamento apenas adicionando mais máquinas juntamente com suas unidades de trabalho ao sistema para suportar a alta demanda.

    * ***Responsividade:*** Nem é preciso dizer que um sistema deve ser sempre rápido e responsivo. O tempo de processamento das requisições não pode aumentar drasticamente do nada, mesmo se a carga aumentar ou erros acontecerem. Particularmente, tarefas grandes ocasionalmente geradas não devem bloquear o resto do sistema ou gerar um grande efeito na performance.

    * ***Atualização ininterrupta:*** Em alguns casos, você precisa atualizar seu software para uma nova versão sem ter a necessidade de resetar todo o seu servidor, por exemplo: Em um sistema telefônico, você não quer disconectar todos os seus usuários de suas chamadas enquanto atualiza o software. 

  * Se você conseguir lidar com esses desafios, seu sistema conseguirá se manter disponível o tempo todo, independente de qualquer coisa que possa acontecer. Dito isso, `Erlang` possui todas as ferramentas para lidar com isso - **foi para isso que ele foi criado afinal**. Um sistema pode se manter altamente disponível por meio do poder do ***Modelo de concorrência do Erlang***.
