# Operadores

Os operadores em elixir se dividem em 3 tipos: `Operadores de atribuição`, `Operadores de comparação`,  `Operadores lógicos` e `Operadores aritméticos`. 

## Operadores de atribuição

O operador de atribuição em elixir pode ser utilizado por meio do símbolo `=` para atribuir valores à variáveis, assim como dito em capítulos anteriores.

```elixir
iex(1)> um = 1
1
iex(2)> um
1
```

## Operadores aritméticos

Elixir possui os operadores aritméticos comuns bem como funções que performam suas operações. Dessa forma temos:

### Operador de adição (`+`):

O operador de adição comum em todas as linguagens de programação:

```elixir
iex(1)> 1 + 1
2
iex(2)> 2 + 2
4
iex(3)> [1, 2] ++ [3, 4]
[1, 2, 3, 4]
```

  * `Notas:` 
    * É possível utilizar 2 operadores de adição para concatenar listas, tal como no exemplo 3.

### Operador de subtração (`-`):

O operador de subtração comum em todas as linguagens de programação:

```elixir
iex(1)> 1 - 1
0
iex(2)> 6 - 2
4
iex(3)> [1, 2, 3, 4] -- [3, 4]
[1, 2]
```

  * `Notas:` 
    * É possível utilizar 2 operadores de subtração para remover valores comuns entre duas listas, tal como no exemplo 3.

### Operador de multiplicação (`*`):

O operador de multiplicação também é comum nas linguagens de programação:

```elixir
iex(1)> 1 * 1
1
iex(2)> 6 * 2
12
iex(3)> 2 ** 2
4
```

  * `Notas:` 
    * É possível executar uma operação de `exponenciação` utilizando dois operadores de multiplicação, tal como no exemplo 3, sendo o correspondende às expressões _`2²`_ ou _`2^2`_, que não existem em elixir mas existem em outras linguagens e na matemática formal.

### Operador de divisão (`/`):
O operador de divisão é também comum entre a maioria das linguagens de programação, no entanto, cabe ressaltar que em elixir **todo resultado de uma operação utilizando o operador `/`, será um número em ponto flutuante**

```elixir
iex(1)> 1 / 1
0.0
iex(2)> 6 / 2
3.0
iex(3)> div(6, 2)
3
iex(4)> rem(6, 2)
0
iex(5)> rem(5, 2)
1
```

  * `Notas:` 
    * Para se obter um resultado de uma divisão em inteiro, utiliza-se a função `div()` para a operação.

    * É possível obter o resto de uma divisão por meio da função `rem()`.


## Operadores lógicos
