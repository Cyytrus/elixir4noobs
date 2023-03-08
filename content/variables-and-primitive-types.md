# Variáveis e tipos primitivos

Neste tópico será explicado as diferenças das variáveis em elixir, como também os tipos que a linguagem possui.

## Variáves

Elixir é uma linguagem de programação dinâmica, isso significa que não é necessário declarar a variável ou seu tipo. Ao invés disso, os tipos das variáveis são definidos por meio dos dados nelas contidos. Em elixir, chamamos de `atribuição` ou `binding` o ato de atribuir um valor à uma variável. Quando você inicializa uma variável, a mesma estará vinculada ao seu valor definido:

```elixir
iex(1)> melhor_repositorio = "4noobs" #=> atribui um valor à variável
"4noobs" #=> resultado da última expressão
```

Cada expressão em elixir possui um resultado. No caso do operador `=`, o resultado é o que quer que esteja à direita do operador. Depois da expressão ser processada, o terminal retorna o resultado na tela:

```elixir
iex(2)> melhor_repositorio #=> expressão que retorna o valor da variável
"4noobs" #=> valor da variável
```

Em elixir, as variáveis devem estar em _lowercase_ sempre, e caso precisem de separação, utiliza-se `underscores ( _ )`.

Os nomes das variàveis também podem terminar com `?` e `!`, e por convenção significam:

  - `?` -> A função / expressão retornará um valor `booleano`
  
  - `!` -> A função retornará apenas o valor da expressão, fugindo das tuplas. 

Além disso, as variáveis podem ser reatribuídas para diferentes valores:

```Elixir
iex(1)> melhor_repositorio = "4noobs" #=> atribui o valor inicial
"4noobs"
iex(2)> melhor_repositorio #=> verifica
"4noobs"
iex(3)> melhor_repositorio = "elixir4noobs" #=> reatribui a variável
"elixir4noobs"
iex(4)> melhor_repositorio #=> verifica o efeito da reatribuição
"elixir4noobs"
```

Reatribuição não fará mutação na localização do dado em memória. É designado um novo espaço na mesma, atribuindo o nome da variável ao novo espaço.

- `Nota:` Tenha sempre em mente que os dados em Elixir são ***imutáveis***. Uma vez que o espaço em memória é ocupado com dados, não poderá ser modificado até ser liberado. Mas variáveis podem ser reatribuídas, o que as fazem apontar para um novo espaço na memória. Assim, variáveis são mutáveis, mas os dados para que elas apontam não são.

Elixir é uma linguagem que possui `garbage collector`, isso significa que não é necessário liberar dados de memória manualmente. Quando uma variável não é utilizada, o seu campo correspondente na memória se torna elegível para ser coletado e liberado pela ferramenta.

## Tipos primitivos

Por ser uma linguagem dinamicamente tipada, isto é, uma linguagem que não necessita que os tipos sejam declarados e/ou atribuídos a uma variável, sendo a mesma responsável por identificar o tipo com base no dado recebido, elixir conta com os seguintes tipos considerados básicos ou primitivos:

### Integer

Os integers compreendem todo o espectro dos números inteiros, ou seja, números sem componente fracional que podem ser tanto negativos como também positivos:

```elixir
iex(1)> 1
1
iex(2)> -9876
-9876
iex(3)> 1_00
100
iex(4)>1_000_000
1000000
iex(5)> 1_987_098_999_987_877
1987098999987877
iex(6)> 0b111
7
iex(7)> 0o123
83
iex(8)> 0x1E2
482
```
* `Notas:` 
  * Em elixir, é possível separar os números com underscores (`_`) para facilitar a leitura de números grandes, como no exemplo acima.

  * Elixir também possui suporte para números binários, octais e hexadecimais, exemplificados nos inputs 6, 7 e 8, respectivamente.

### Float

Tendo passado pelos números inteiros, o próximo valor que temos em Elixir é o float, que compreende os números decimais, ou seja, que possuam componentes fracionais, exemplificados em elixir com um ponto (`.`) após um número. 

```elixir
iex(1)> 3.1452
3.1452
iex(2)> 0.14
0.14
iex(3)> 1.0e10
1.0e10
iex(4)> 1.0e-100
1.0e-100
iex(5)> 1.0e-2
0.01
```
* `Notas:`

  * Os floats em elixir possuem dupla precisão de 64-bits.

  * O tipo suporta `e` para exemplificar valores exponenciais, como exemplificados nos inputs 3 e 4 acima.

  * Os floats **devem**, obrigatóriamente, possuir um número antes do ponto, do contrário acontecerá um erro de síntaxe.

### Átomos

Os átomos são valores constantes em que seu valor está no próprio nome, e são úteis quado utilizados para identificar valores distintos. É possível identificá-los quando começam com o símbolo `:`.

No runtime, o texto mantido no átomo (aquilo que está escrito após o `:`) é guardado na tabela interna de átomos do elixir. E o valor atribuído à esse átomo ficaria dentro da variável, que serviria apenas para referenciar o átomo. Isso explica o porquê dos átomos serem a melhor opção para nomear constantes em elixir, sendo eficientes tanto em performance, como também em memória. e quando vc utiliza

```elixir
variavel = :atomo_foda
```
a variável não contém todo o texto do átomo, ela apenas referencia à tabela de átomos. Dessa forma, o consumo de memória é baixo, com comparações rápidas e que ainda mantém o código legível.

Abaixo seguem outros exemplos:

```elixir
iex(1)> :he4rt
:he4rt
iex(2)> :he4rtdevs
:he4rtdevs
iex(3)> :he4rt == :he4rtdevs
false
iex(4)> :very_good_atom
:very_good_atom
iex(5)> :"very good atom"
:"very good atom"
```

* `Notas:`

  * Átomos só serão iguais quando seus nomes forem iguais, e normalmente são utilizados para expressar o estado de uma operação, como: `:error` e `:ok`
  
  * A convenção é utilizar _underscores_ (`_`) quando necessitar espaçar o nome do átomo, no entanto, conforme o exemplo 5, com a síntaxe de string é possível também utilizar espaço, mas não é uma boa prática e devemos evitá-la.

### Booleanos ou átomos como booleanos

É bem surpreendente como elixir lida com booleanos, visto que os mesmos são também átomos, não havendo um tipo dedicado apenas para booleanos. Nesse caso, temos `:true` e `:false` para sinalizar tais valores. No entanto, para não causar estranheza aos novos desenvolvedores, elixir conta com um pequeno sugar sintático, deixando a critério do desenvolvedor utilizar ou não os booleanos com dois pontos:

```elixir
iex(1)> :true == true
true
iex(2)> false == false
true
```

O termo `booleano` é utilizado em elixir para se referir aos valores `true` ou `false`, mas é sempre bom lembrar que no fundo eles também são átomos.

### Átomo nil

O `nil`, assim como `true` e `false`, é também um átomo e pode ser comparado ao `null` de outras linguagens, ele pode ser escrito tanto na forma de àtomo (`:nil`), como também na forma comum.

O nil é um valor-suporte para lidar com comparações/checagens. Ambos os valores `nil` e `false` são tratados como valores falsos, visto que são valores contrários a `true`.

### Binários e bitstrings

Um binário é um aninhado de bytes. Você pode criar binários utilizando uma sequencia de bytes entre os operadores `<<` e `>>`. O exemplo a seguir será de um binário de 6 bytes:

```elixir
iex(1)> <<1, 2, 3, 9, 8, 7>>
<<1, 2, 3, 9, 8, 7>>
```

Cada número representa o valor correspondente em byte. Se o valor do byte for maior que 255, a contagem recomeça, ou seja:

```elixir
iex(1)> <<256>> 
<<0>>
iex(2)> <<257>>
<<1>>
```

  * `Notas:`
    * Estrutura:
      * `1, 2, 3, 9, 8, 7` -> sequência de bytes
      * `<<` `>>` -> operadores

Sobre bytes e bitstring imagino que já seja o suficiente para entendermos o próximo assunto, as `Strings`

### Strings

Assim como a grande surpresa de que não temos booleanos como tipo dedicado, as strings não poderiam ser diferentes, em Elixir temos strings como strings binárias, onde uma string é um agregado também de binários, dessa forma, podemos inferir strings normalmente como:

```elixir
iex(1)> "Isso é uma string massa"
"Isso é uma string massa"
iex(2)> <<73, 115, 115, 111, 32, 195, 169, 32, 117, 109, 97, 32, 115, 116, 114, 105, 110, 103, 32, 109, 97, 115, 115, 97>>
"Isso é uma string massa"
```

O resultado do exemplo 1 é printado como uma string normal, mas por baixo dos panos na verdade é apenas um agregado de bytes, tal como no exemplo 2, legal né?

Elixir também permite, além da concatenação, a interpolação de string por meio da síntaxe `#{}` dentro de aspas duplas, na interpolação é possível chamar funções, realizar operações e recuperar valores, assim como nos exemplos abaixo:

```elixir
iex(1)> "a soma de 1+1 é #{1 + 1}"
"a soma de 1+1 é 2"
iex(2)> nome = "Elixitrus"
"Elixitrus"
iex(3)> "esse 4noobs foi iniciado por #{nome}!"
"esse 4noobs foi iniciado por Elixitrus!
```
As strings em elixir também possuem compatibilidade com os caracteres de escape comuns:

```
iex(1)> "
...(1)> A
...(1)> He4rt
...(1)> é
...(1)> foda
...(1)> "
"\nA\nHe4rt\né\nfoda\n"
```

Acima, no exemplo 1 é possível perceber que o `iex` suporta quebra de linhas, portanto o elixir também, e todas as quebras são convertidas para o caractere de escape `\n`.

Elixir também provê uma forma única para se criar strings e outros tipos de dados, os `sigils`, no entanto isso será abordado mais a frente desse 4noobs.

Além de tudo isso, elixir possui uma síntaxe especial, o `heredoc`, ele foi pensado para strings que precisem de múltiplas linhas, tais como: documentações, explicações e... desenhos? Elas são constituídas pelo formato de três aspas duplas (`"""`) isoladas no começo e três isoladas no final:

```
iex(1)> """
...(1)> doc foda do "elixir4noobs"
...(1)> """
"doc foda do \"elixir4noobs\"\n"
```

As strings, além de interpoladas como já exemplificadas em exemplos anteriores, também podem ser `concatenadas`, pois como são binários, tal operação se torna possível:

```elixir
iex(1)> "he4rt" <> " " <> "4noobs"
"he4rt 4noobs"
```

### Lista de caracteres

Uma maneira alternativa de representar strings é por meio das listas de caracteres

```elixir
iex(1)> 'salve'
'salve'
```

Isso cria uma lista de caracteres, que se consiste em uma lista de inteiros, onde cada número representa um caractere:

```elixir
iex(1)> [115, 97, 108, 118, 101]
'salve'
```

Mas isso é meio confuso, como você pode ver, o runtime não consegue distinguir uma lista de caracteres e uma lista de inteiros. Quando uma lista se consiste de inteiros que podem corresponder a um caractere, então o caractere será priorizado.

Assim como nas strings, podemos fazer as mesmas coisas com as listas de caracteres, com exceção da concatenação:

```
iex(1)> 'Interpolacao: #{1+1}'
'Interpolacao: 2'
iex(2)> '''
...(2)> heredoc
...(2)> '''
'heredoc\n'
```

E para identificarmos qual inteiro corresponde a um caractere, basta utilizarmos a sintaxe `?`:

```elixir
iex(1)> ?a
97
iex(2)> ?b
98
iex(3)> ?c
99
iex(4)> ?;
59
```

Dessa forma, entendendo os tipos básicos de elixir, é possível ir para o próximo tópico: [Operadores]()