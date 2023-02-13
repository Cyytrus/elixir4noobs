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

Elixir é uma linguagem que possui `garbage collector`, isso significa que não é necessário liberar dados de memória. Quando uma variável não é utilizada, o seu campo correspondente na memória se torna elegível para ser coletado e liberado pela ferramenta.

## Tipos primitivos

