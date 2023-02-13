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
  
    Se tratando de `Erlang`, sua alta disponibilidade se dá por diversos tipos de fatores, dentre eles: `tolerância à falhas`, `escalabilidade`, `distribuição`, `tempo de resposta` e `atualização ininterrupta`. Tais funções transformam a linguagem em algo perfeito e resiliente nas mais diversas circunstâncias, mas dizer tudo isso é muito fácil, a primeira camada das coisas é a mais bonita, no entanto, temos diversos desafios técnicos nos fatores acima para fornecer um sistema que esteja disponível 100% do tempo:

    * ***Tolerância à falhas:*** Um sistema **tem** que se manter funcionando mesmo diante de imprevistos. Componentes podem falhas, bugs podem surgir do absoluto nada e infinitos erros podem acontecer, isso sem falar da rede caindo e do pior dos casos: ***A BEAM MORRER***. Independente de tudo isso, é necessário encontrar o ponto de impacto, se recuperar e manter o sistema de pé.

    * ***Escalabilidade:*** Essa é a questão mais polêmica de toda a tecnologia, entre arquiteturas de código, boas práticas e afins, o tópico sempre se converge com "o quão escalável isso é?". Um sistema deveria estar apto para lidar com ***QUALQUER*** tipo de carga. Mas dito isso, é claro que você não vai comprar uma quantidade absusiva de hardware só para o caso de, ocasionalmente, o planeta todo decidir utilizar algo seu. Mas o sistema deve estar apto para responder ao aumento repentino de carga adicionando recursos de hardware aos poucos e sem nenhuma intervenção de softwares. Idealmente deveria ser possível sem a necessidade de interromper o sistema, aumentar a capacidade para só então subí-lo novamente. 

    * ***Distribuição:*** Para fazer um sistema que nunca para, é necessário rodá-lo em diversas máquinas. Isso promove uma estabilidade geral, em que se uma máquina para por algum motivo, outra pode continuar, por assim em diante e simultaneamente também. Além disso, Isso lhe dá poder para escalar horizontalmente - você pode aumentar a taxa de processamento apenas adicionando mais máquinas juntamente com suas unidades de trabalho ao sistema para suportar a alta demanda.

    * ***Tempo de resposta:*** Nem é preciso dizer que um sistema deve ser sempre rápido e responsivo. O tempo de processamento das requisições não pode aumentar drasticamente do nada, mesmo se a carga aumentar ou erros acontecerem. Particularmente, tarefas grandes ocasionalmente geradas não devem bloquear o resto do sistema ou gerar um grande efeito na performance.

    * ***Atualização ininterrupta:*** Em alguns casos, você precisa atualizar seu software para uma nova versão sem ter a necessidade de resetar todo o seu servidor, por exemplo: Em um sistema telefônico, você não quer disconectar todos os seus usuários de suas chamadas enquanto atualiza o software. 

    Se você conseguir lidar com esses desafios, seu sistema conseguirá se manter disponível o tempo todo, independente de qualquer coisa que possa acontecer. Dito isso, `Erlang` possui todas as ferramentas para lidar com isso - **foi para isso que ele foi criado afinal**. Um sistema pode se manter altamente disponível por meio do poder do ***Modelo de concorrência do Erlang***.

    #### **2. Concorrência em Erlang**

    Concorrência está intriseca em **todos** os sistemas baseados em **Erlang**. Quase qualquer aplicação baseada em erlang possui uma alta carga de concorrência, e até mesmo a própria linguagem às vezes é denominada como uma linguagem **orientada a concorrência**. Ao invés de se limitar à threads pesadas e processos no SO, erlang lida com a concorrência sozinho:

    ![erlang-concurrency-model](/images/erlang-concurrency-model.png)

    O básico da concorrência em Erlang é chamado de **Processo erlang (Erlang Process)**, o que é diferente de Processos no SO e threads. Um típico sistema em Erlang roda milhares ou até milhões desses processos. A máquina virtual do Erlang, a BEAM *(Bogdan/Björn’s Erlang Abstract Machine)* , utiliza seus próprios **schedulers** para distribuir a execução dos processos em cima dos núcleos da CPU disponíveis naquele momento, paralelizando a execução o máximo possível. O jeito que os processos são implementados proporcionam diversos benefícios:

    1. **Tolerância à falhas**: Processos em Erlang são completamente isolados uns dos outros. Eles não compartilham memória, e a ocasional quebra de algum processo não afeta os outros processos que estão rodando ao mesmo tempo ou rodarão posteriormente. Isso ajuda a isolar os efeitos de algum erro inesperado, ocasionando em apenas um erro local. Além disso, Erlang proporciona ao usuário os meios de detectar processos que não estão performando como deveriam, e com isso, possibilita uma tomada de decisão em cima do problema, normalmente, você inicia um novo processo no lugar do processo defeituoso.

    2. **Escalabilidade**: Não compartilhar memória juntamente com comunicação entre processos feita por meio de mensagens assíncronas. Isso significa que Erlang não necessita de mecânismos de síncronização complexos, tais como locks ou mutexes. Consequentemente, a interação entre as entidades concorrentes é muito simples de desenvolver e entender.

    3. **Distribuição**: A comunicação entre processos funcionam da mesma forma, independentemente de estarem na mesma instância da BEAM, no mesmo computador ou em outros. Portanto, um típico sistema altamente concorrente baseado em Erlang está automaticamente apto para ser distribuido entre diversas máquinas. Isso em tese possibilita ao usuário escalar sua aplicação, de modo que o mesmo consiga rodar um cluster com diversas máquinas que compartilham a carga total do sistema. Adicionalmente, rodar uma aplicação em múltiplas máquinas pode tornar o sistema mais eficiente num geral - **se uma máquina quebrar, as outras podem tomar conta** 

    4. **Tempo de resposta**: O runtime é feito para promover o melhor tempo de resposta do sistema. Foi mencionado que Erlang toma a execução de múltiplos processos para si mesmo, empregando schedulers que executam diversos Processos Erlang cadencialmente. Um scheduler é precavido, abre pequenas janelas de execução para o processo rodar, e em seguida as pausa para dar andamento à outros processos. Por conta da janela de execução não possuir tanto tempo, um único processo longo não pode bloquear os outros que ainda precisam performar suas designadas funções. Portanto, operações de entrada e saída de dados são internamente designadas a threads específicas ou a um kernel-poll do sistema operacional. Isso significa que quaisquer processos que necessitem esperar por uma entrada ou saída de dados para serem finalizados não serão bloqueantes para os outros processos.

        Até mesmo o garbage collection é especialmente feito para promover tal tempo de resposta ao executar novamente processos que são completamente isolados e que não compartilham memória. Isso possibilita um carbage collector por processo, em que, ao invés de parar todo o sistema, cada processo é coletado individualmente caso necessário for. Tais coletas não muito mais rápidas e não bloqueiam o sistema inteiro por muito tempo. Na verdade, em um sistema com diversos núcleos, é possível apenas um núcleo da CPU rodar um pequeno garbage collector enquanto os cores remanescentes executam processos básicos.

      E como é possível observar, a concorrência é um elemento importante em Erlang, e vai além de apenas paralelismo. Graças a sua implementação, a concorrência de Erlang promove todos os 4 pontos acima de maneira exemplar. Sistemas típicos da linguagem conseguem executar diversas tarefas concorrentes, utilizando milhares ou até milhões de processos. Isso é consideravelmente útil quando você está desenvolvendo sistemas que renderizam no servidor, e que podem ser completamente implementados em Erlang, mas isso é assunto para outro dia!

### Elixir!

Agora que você já sabe toda a base em que foi construído o Elixir, podemos dizer **o que é** essa linguagem maravilhosa!

Elixir é uma linguagem alternativa para a máquina virtual do Erlang, a BEAM, e possibilita ao usuário a escrita de um código limpo, compacto e que seja mais legível para os desenvolvedores que o fazem. Todos os programas escritos em elixir rodam na BEAM.

A linguagem é um projeto open-source escrito pelo brasileiro José Valim em meados de 2012, e, ao contrário de Erlang, Elixir é um esforço colaborativo de diversos desenvolvedores / entusiastas e simpatizantes, não sendo algo de apenas uma empresa / pessoa. Atualmente possui mais de 1.100 contribuintes no código do [github](https://github.com/elixir-lang/elixir). 

Todas as discussões de features podem ser vistas nas issues do repositório e são muito bem vindas para a linguagem e comunidade.

Elixir tem como alvo o runtime do Erlang. O resultado de compilar códigos Elixir são arquivos compatíveis com a BEAM e que podem rodar na instância da máquina virtual, podendo também cooperar com códigos Erlang nativos, ou seja, arquivos `.ex` podem executar códigos em erlang tranquilamente. É possível utilizar libs do erlang no elixir e vice-versa. Não há nada que você faça em erlang que não consiga ser feito em elixir, e normalmente ambos os códigos possuem a mesma performance.

Elixir é semânticamente parecido com erlang, quase todas as estruturas de elixir apontam para um correspondente em erlang. No entanto, Elixir providencia estruturas adicionais que possibilitam imensamente reduzir boilerplates e duplicações. Além disso, apresenta na lib básica diversas melhoras sintáticas e ferramentais para criar e lidar com sistemas.

Dessa forma, tendo entendido as bases do Elixir, o erlang, o desenvolvedor pode se apaixonar por esses 2 lados que trabalham muito bem juntos!
