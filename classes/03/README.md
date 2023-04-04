<!--
author:   Andrea Charão

email:    andrea@inf.ufsm.br

version:  0.0.1

language: PT-BR

narrator: Brazilian Portuguese Female

comment:  Material de apoio para a disciplina
          ELC106 - Algoritmo e Programação,
          da Universidade Federal de Santa Maria

translation: English  translations/English.md

link:     custom.css
          https://fonts.googleapis.com/css?family=Quattrocento%20Sans
-->
<!--
liascript-devserver --input README.md --port 3001 --live
link:     https://cdn.jsdelivr.net/gh/liascript/custom-style/custom.min.css
          https://cdn.jsdelivr.net/gh/andreainfufsm/elc106-2023a/classes/03/custom.css
          https://fonts.googleapis.com/css?family=Abril%20Fatface

-->


# Aula 03

- Requisito: exercícios da aula anterior.

- Inicie visualizando a seção de Revisão.

- Novos conteúdos: números pseudoaleatórios, comandos if/else, variáveis contadoras


## Revisão

Principais assuntos da aula passada:

- Primeiro contato com Python no ambiente Repl.it

- Uso e definição de funções em Python


### Ambiente Repl.it

A seguir, algumas imagens de interação com o Repl.it para tarefas frequentes.

#### Entrada no grupo da disciplina

![](img/anim-entrada-replit.gif)

#### Visualização de instruções

![](img/anim-instructions-replit.gif)

#### Edição e execução na console

![](img/anim-edit-run-replit.gif)

#### Submissão (envio) de exercício

![](img/anim-submit-replit.gif)


#### Visualização de comentários de revisão

![](img/anim-threads-replit.gif)



### Funções



1. Funções são códigos genéricos, reusáveis, parametrizáveis
2. Inspiração em funções matemáticas: $f(x) = x + 3$
3. Aumentam o poder de uma linguagem
4. Podemos definir nossas próprias funções
5. Momentos distintos: definir uma função **é diferente de** usar uma função
6. Funções recebem argumentos e retornam um resultado


> Avance os slides para alguns testes rápidos sobre funções em Python!


                 {{1}}
************************************************

Qual das definições de função abaixo vai ser processada sem erros pelo interpretador Python?

Primeira

```python
def func(a,b):
  return a+b
```

Segunda

```python
def func(a,b):
  retorne a + b
```

- [(x)] Primeira
- [( )] Segunda


************************************************



                 {{2}}
************************************************

Suponha que o código abaixo está no arquivo `main.py` no Repl.it. Ao clicarmos no botão `Run`, o que será mostrado na Console?

```python
def func(a):
  x = a + 5
  return x

print(func(2))
```

- [( )] 5
- [(x)] 7


************************************************


                 {{3}}
************************************************

Suponha que o código abaixo está no arquivo `main.py` no Repl.it. Ao clicarmos no botão `Run`, o que será mostrado na Console?

```python
def func(a):
  print('Eu sou uma função')
  x = a + 5
  return x
```

- [( )] Será mostrada a mensagem 'Eu sou uma função'
- [(x)] Nada será mostrado na tela


<details>
  <summary>Clique para saber mais</summary>
O código acima apenas define a função, mas não faz uso dela nas linhas seguintes.
Como a função não é chamada/usada, ela não será executada e o programa não mostrará nada na tela.
</details> 





************************************************



## Funções: geração de números pseudoaleatórios

Você consegue prever a saída deste código?

```python
from random import randint
n = randint(1,6)
print(n)
```

Teste no **interpretador**!

<iframe src="https://trinket.io/embed/python3/d52f952885?outputOnly=true&runOption=console&runMode=console" width="100%" height="300" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

### Considerações gerais
- Funções de **geração de números pseudoaleatórios** são muito usadas em estatística, engenharias, data science, computação científica, jogos, etc.

- Por que **pseudo?**

  - sequências de números podem ser reproduzidas
  - portanto não são verdadeiramente aleatórias

- Encontradas em várias bibliotecas: [`random`](https://docs.python.org/3/library/random.html), [`numpy.random`](https://numpy.org/doc/1.16/reference/routines.random.html), [`scipy.stats`](https://docs.scipy.org/doc/scipy/reference/stats.html), etc.


### Algumas funções da biblioteca `random`

- Grande coleção de funções
- Veremos apenas algumas, mas você pode descobrir outras
- Saiba mais em:  https://docs.python.org/3/library/random.html

??[Documentação da biblioteca random](https://docs.python.org/pt-br/3/library/random.html)

#### Antes de usar: `import`

- Lembre que precisamos indicar que vamos usar funções pré-definidas em bibliotecas
- Do contrário, teremos erro `undefined`
- Python tem as instruções `import`/`from` para indicar a(s) biblioteca(s) e a(s) função(ões) que desejamos usar
- Boa prática: coloque nas primeiras linhas do programa todas as bibliotecas e funções que você vai usar (não é necessário repetir ao longo do programa)

Exemplos

1. Função `randint` da biblioteca `random`

   ```python
   from random import randint
   n = randint(1,6)
   ```

2. Função `random` da biblioteca `random` (!)

   ```python
   from random import random
   n = random()
   ```

3. A biblioteca `random` (neste caso, temos que usar o nome da biblioteca antes do nome da função)

   ```python
   import random
   n = random.randint(1,6)
   ```

4. Todas as funções da biblioteca `random`

   ```python
   from random import *
   n = randint(1,6)
   ```

5. Algumas funções da biblioteca `random`

   ```python
   from random import randint, random
   a = randint(1,6)
   b = random()
   ```

#### Função `random()`

- Retorna número fracionário no intervalo `[0, 1)`
- Sendo `[0,1) = {x | 0 <= x < 1}`

```python
from random import random
n = random()        # gera número entre [0,1)
print(n)            # mostra número 
m = n*10            # multiplica por 10
print(round(m, 1))  # arredonda para 1 casa decimal e mostra
print(int(m))       # converte para número inteiro e mostra
```

Teste no **interpretador interativo**!

<iframe src="https://trinket.io/embed/python3/d52f952885?outputOnly=true&runOption=console&runMode=console" width="100%" height="300" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>


#### Função `randint(a,b)`

- Retorna número inteiro no intervalo `[a, b]`
- Sendo `[a,b] = {x | a <= x <= b}`.


```python
from random import randint
d1 = randint(1,6)  # gera número entre [1,6]
d2 = randint(1,6)  # gera número entre [1,6]
print('Primeiro número:', d1)
print('Segundo número:', d2)
```

Teste no **interpretador interativo**!

<iframe src="https://trinket.io/embed/python3/d52f952885?outputOnly=true&runOption=console&runMode=console" width="100%" height="300" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>



#### Função `seed(s)`

- Inicializa o gerador de números aleatórios
- Permite reproduzir sequências
- Útil para experimentos científicos
- Mesma seed = mesma sequência


```python
from random import randint, seed
seed(1)                  # inicializa gerador  
primeiro = randint(1,6)  # primeira chamada da função retornará 2
segundo = randint(1,6)   # segunda chamada da função retornará 5
print('Primeiro número:', primeiro)
print('Segundo número:', segundo)
```

Teste no **interpretador interativo**!

<iframe src="https://trinket.io/embed/python3/d52f952885?outputOnly=true&runOption=console&runMode=console" width="100%" height="300" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>


#### Distribuições

- Há funções para gerar distribuições específicas usadas em estatística
- Resultado geralmente é um valor real (com casas decimais, também chamado de número de "ponto flutuante")
- Saiba mais em: https://docs.python.org/pt-br/3/library/random.html

Exemplos: 

- Função `uniform(a,b)`: retorna um número de ponto flutuante  N de forma que `a <= N <= b` para `a <= b` e `b <= N <= a` para `b < a`.
- Função `gauss(mu, sigma)`: retorna um número em uma distribuição normal, sendo mu a média e sigma o desvio padrão
- Função `pareto(alpha)`: retorna um número na distribuição de Pareto, sendo alpha o parâmetro de forma









## Estruturas de controle: seleção / decisão / condicionais

- Até agora, só tínhamos trabalhado com **sequências de comandos**:

  - todas as linhas executadas

    ```python
    print('Primeira linha')
    print('Segunda linha')
    print('Terceira linha')
    ```

- Em muitos casos, queremos controlar (decidir) quais comandos serão executados, de acordo com alguma **condição**

- Para isso, precisamos conhecer mais algumas instruções/comandos da linguagem!

### Usando `if`

Ativa a execução de um bloco de comandos se uma condição for satisfeita 


Você consegue prever o resultado deste programa?

```python
from random import randint
sorteado = randint(1,6)
print('Número sorteado:', sorteado)
if sorteado == 6:
   print('Conseguimos o maior número!')
   print('Temos muita sorte!')
print('Fim do programa')
```

Forma geral:

```python
if condição:
   comando a executar se condição verdadeira
   outro comando a executar se condição verdadeira
```

Observações:

- Recuo obrigatório!
- Bloco não é executado se a condição não for verdadeira
- Execução continua em sequência depois do bloco
- Condição geralmente usa operadores relacionais

### Operadores relacionais

<!-- data-type="none" -->
| Operador   | Significado    | Exemplo    | Resultado   |
| :--------- | :------------  | :--------- | :--------- |
| `==`       | Igual          | `1 == 2`     | False     |
| `!= `      | Diferente      | `1 != 2`     | True     |
| `>`        | Maior          | `1 > 2`      | False |
| `<`        | Menor          | `1 < 2`      | True  |
| `>=`       | Maior ou igual | `1 >= 2`     | False |
| `<=`       | Menor ou igual | `1 <= 2`     | False |


- Valores `True`/`False` são definidos na linguagem para representar resultados de expressões lógicas: verdadeiro ou falso
- Podemos manipular estes valores com operadores relacionais (acima) ou lógicos (veremos mais adiante: and, or, etc.)


### Mais exemplos


1) Você consegue prever o resultado deste programa?

```Python
from random import randint

x = randint(1, 100)
print('Idade:', x)
if x >= 18:
  print('Maior de idade')
if x < 18:
  print('Menor de idade')
print('Fim do programa')  
```

2) E deste outro?

```Python
from random import randint

a = randint(1, 10)
b = randint(1, 10)
print('Valores:', a, b)
if a > b:
  print('Primeiro valor é maior')
if a <= b:
  print('Primeiro valor é menor ou igual')
```

3) E este exemplo com `if` dentro de uma função?

```Python
from random import randint

def parouimpar(n):
  if n % 2 == 0:
    return "par"
  if n % 2 == 1:
    return "impar"

n = randint(1, 100)
print('O número', n, 'é', parouimpar(n))
```

### Usando `if`/`else`



- Quando a segunda condição é o inverso da primeira, podemos usar `else` ("senão", em inglês)
- Simplifica o programa, pois não temos que escrever a condição inversa

```Python
from random import randint

a = randint(1, 10)
b = randint(1, 10)
print('Valores:', a, b)
if a > b:
  print('Primeiro valor é maior')
else:
  print('Primeiro valor é menor ou igual')
```

```Python
from random import randint

def parouimpar(n):
  if n % 2 == 0:
    return "par"
  else:
    return "impar"

n = randint(1, 100)
print('O número', n, 'é', parouimpar(n))
```


## Variáveis 

- Variáveis servem dar nome a um dado armazenado na memória
- Analogia com gavetas e etiquetas
- Podem conter dados diferentes durante a execução do programa

### Regras para nomes

- Sequência de uma ou mais letras (a → z, A → Z), podendo conter números (0 → 9)
- Deve sempre começar com uma letra
- Não pode conter espaços nem caracteres especiais como $, #, @, +, -, etc. 
- Pode conter o caracter `_` (sublinhado/underline)
- Evite usar caracteres acentuados
  
### Variáveis contadoras

Você consegue prever o resultado deste código?

```python
n = 0
print(n)
n = 1
print(n)
n = n + 1
print(n)
```

                 {{1}}
************************************************

- Operador `=` atribui um valor à variável
- No caso de `n = n + 1`, o valor atual de n é incrementado de 1 e atribuído novamente à variável
- **Atenção:** Antes de incrementar é preciso atribuir um valor inicial (inicializar)

************************************************

## Exercícios no Repl.it

- Entre no grupo da disciplina no Repl.it: https://replit.com/teams/join/bzmdfmvrldnyymssuydqhwpkmoidivlo-elc106-2023a

- Em `Projects`, selecione a `aula03` 

- Veja as `Instructions` e preencha os exercícios no arquivo `main.py`

- Use `Run` com frequência para testar seu código

- Clique em `Submit` para enviar os exercícios para a professora

- Mais adiante, use a aba `Threads` para visualizar comentários da professora sobre seu código
