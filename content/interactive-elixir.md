# Conhecendo o iex, seu melhor amigo!

  Elixir's interactive shell, IEx, ou apenas iex é uma ferramenta de desenvolvimento em Elixir que possibilita o desenvolvedor escrever módulos, funções, códigos simples ou até mesmo buscar ajuda na ***documentação do elixir.***

  É possível utilizá-lo no terminal a partir do seguinte comando:

  ```bash
  $ iex
  ```

 E normalmente o retorno é o seguinte:

  ```bash
  Erlang/OTP 25 [erts-13.0.4] [source] [64-bit] [smp:4:4] [ds:4:4:10] [async-threads:1] [jit:ns]

  Interactive Elixir (1.13.4) - press Ctrl+C to exit (type h() ENTER for help)
  
  iex(1)> 
  ```
  
  O retorno acima dependerá da sua versão do elixir e erlang, podendo variar em cada versão.

  ## Afinal, como isso é útil no dia a dia?

  Imagine que você esteja precisando entender como um código funciona e está com a sua IDE aberta, mas não quer ter todo o trabalho de abrir a documentação da linguagem e procurar em um módulo a função que atenda sua necessidade. Para isso temos o iex!

  Nele é possível testar desde operações básicas de operação, como também comparação, funções e etc

  ```elixir
  iex(1)> 1 + 1
  2
  iex(2)> 1 > 2
  false
  iex(3)> String.upcase("Elixir4noobs")
  "ELIXIR4NOOBS"
  ```
  E se tratando de buscar arquivos na documentação, temos a opção de utilizar o prefixo `h` no módulo e função que queremos utilizar, podemos também utilizar a função de autocomplete da ferramenta para obtermos todas as funções que o módulo possui, para isso digitamos o `nome do módulo` e juntamente com um `ponto (.)`, pressionamos a tecla `tab` para o seguinte resultado:

  ```elixir
  iex(1)> h String.
  Break                 Chars                 Tokenizer             
Unicode               at/2                  bag_distance/2        
capitalize/1          capitalize/2          chunk/2               
codepoints/1          contains?/2           downcase/1            
downcase/2            duplicate/2           ends_with?/2          
equivalent?/2         first/1               graphemes/1           
jaro_distance/2       last/1                length/1              
match?/2              myers_difference/2    next_codepoint/1      
next_grapheme/1       normalize/2           pad_leading/2         
pad_leading/3         pad_trailing/2        pad_trailing/3        
printable?/1          printable?/2          replace/3             
replace/4             replace_leading/3     replace_prefix/3      
replace_suffix/3      replace_trailing/3    reverse/1             
slice/2               slice/3               split/1               
split/2               split/3               split_at/2            
splitter/2            splitter/3            starts_with?/2        
to_atom/1             to_charlist/1         to_existing_atom/1    
to_float/1            to_integer/1          to_integer/2          
trim/1                trim/2                trim_leading/1        
trim_leading/2        trim_trailing/1       trim_trailing/2       
upcase/1              upcase/2              valid?/1    
  ```

  Acima estão todas as funções que o módulo `String` possui na versão 1.13.4

  Agora sobre a documentação, utilizaremos a documentação da função `upcase()` do módulo `String` como exemplo:

  ```elixir
  iex(1)> h String.upcase


            def upcase(string, mode \\ :default)                      

  @spec upcase(t(), :default | :ascii | :greek | :turkic) :: t()

  Converts all characters in the given string to uppercase according to mode.

  mode may be :default, :ascii, :greek or :turkic. The :default mode considers all non-conditional transformations outlined in the Unicode standard. :ascii uppercases only the letters a to z. :greek includes the context sensitive mappings found in Greek. :turkic properly handles the letter i with the dotless
variant.

## Examples

    iex> String.upcase("abcd")
    "ABCD"
    
    iex> String.upcase("ab 123 xpto")
    "AB 123 XPTO"
    
    iex> String.upcase("olá")
    "OLÁ"

The :ascii mode ignores Unicode characters and provides a more performant
implementation when you know the string contains only ASCII characters:

    iex> String.upcase("olá", :ascii)
    "OLá"

And :turkic properly handles the letter i with the dotless variant:

  iex> String.upcase("ıi")
    "II"
    
  iex> String.upcase("ıi", :turkic)
    "Iİ"
  ```

  Esse é o retorno obtido quando utilizamos o prefixo `h` juntamente com `String.upcase()`. Nele é possível observar toda a documentação referente à esse tópico sem sair do terminal do computador! 

  Agora que temos uma noção do funcionamento do `iex`, como saímos desse shell interativo? Existem 3 opções:

  - `Ctrl + C` e logo em seguida apertando `q` e  `enter`
  - Apertando `Ctrl + C` duas vezes
  - Apertando `Ctrl + \`

  Ao longo desse 4noobs é de suma importância que você utilize o `iex` para praticar os códigos que serão apresentados.

  Agora, para colocarmos todo esse conhecimento em prática, aqui estão os [conhecimentos do próximo tópico!](content/../variables-and-primitive-types.md)