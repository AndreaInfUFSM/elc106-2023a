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


# Aula 04

- Requisito: exercícios da aula anterior.

- Inicie visualizando a seção de Revisão.

- Hoje: comentários sobre exercícios entregues, mais sobre condicionais, execução passo-a-passo, exercícios





## Revisão

Principais assuntos da aula passada:

- Geração de números pseudoaleatórios
- Controle de execução com instruções `if`/`else` (condicionais)
- Variáveis contadoras



### Estruturas condicionais

1. Estruturas com instruções `if`/`else`
2. Condições são verificadas com expressões que resultam em `True` (verdadeiro) ou `False` (falso)
3. Blocos de comandos são executados ou não, dependendo da condição verificada




![](https://programming-22.mooc.fi/static/416cb381134e2a6b8d72caecc6260d5a/30f41/1_5_1.webp)

### Sintaxe: `if` e `if`/`else`

**ATENÇÃO**: bloco de comandos deve ser recuado à direita (*indent* obrigatório)

Estrutura `if` (se)

```python
if condição:
   primeiro comando do bloco
   segundo comando do bloco
   outros comandos do bloco
```

Estrutura `if`/`else` (se/senão)

```python
if condição:
   primeiro comando do bloco executado se condição verdadeira
   segundo comando do bloco executado se condição verdadeira
   outros comandos do bloco executado se condição verdadeira
else:
   primeiro comando do bloco executado se condição falsa
   segundo comando do bloco executado se condição falsa
   outros comandos do bloco executado se condição falsa
```

### Vídeo sobre expressões lógicas

*CS Discoveries: Boolean Expressions*

Ative as legendas automáticas em português!


> Expressões booleanas / lógicas: resultam `True` ou `False`

Link: https://www.youtube.com/watch?v=_j9nvYKaOVE

??[](https://www.youtube.com/watch?v=_j9nvYKaOVE)


### Variáveis contadoras


- Pense que uma variável é como uma caixa etiquetada
- A "caixa" é um espaço na memória do computador
- A "etiqueta" é o nome da variável


??[](https://youtu.be/c5lLOHHg50A)



### Exercícios com auto-correção

Teste seu conhecimento!

Para cada uma das 5 questões, marque uma resposta e clique em `Check` para verificá-la!




                 {{1}}
************************************************
Qual será a saída do código abaixo?

```python
n = 5 + 2**2
if (n > 10):
  print('Condição verdadeira!')
else:
  print('Condição falsa!')
```

- [( )] Condição verdadeira!
- [(x)] Condição falsa!

************************************************


                 {{2}}
************************************************

Qual será a saída do código abaixo?

```python
from math import sqrt
x = 10**2
if (sqrt(x) > 9):
  print('Condição verdadeira!')
else:
  print('Condição falsa!')
```

- [(x)] Condição verdadeira!
- [( )] Condição falsa!

************************************************



                 {{3}}
************************************************

Quantas linhas de texto serão mostradas na tela quando o programa abaixo for executado?

Obs.: Aqui temos uma nova função...
<details>
  <summary>Clique para saber sobre ela</summary>
<ul>
<li>A função `len(c)` retorna o número de itens em um conjunto de dados (veremos isso mais adiante)</li>
<li>Textos em Python são conjuntos de caracteres (um tipo de dado)</li>
<li>`len('abracadabra')` retorna o valor `11`, que é a quantidade de caracteres do texto `'abracadabra'`</li>
</ul>
</details>

```python
tamanho = len('mensagem')
if (tamanho > 10):
  print('Condicao verdadeira!')
print('Continuo executando')
print('Cheguei no final')
```



- [(x)] 2 linhas
- [( )] 3 linhas

************************************************



                 {{4}}
************************************************

Qual será o resultado da execução do código abaixo?

```python
def func(x):
  return x * x

n = 5
if (func(n) > 10):
  print(n)
```

- [( )] 25
- [( )] 10
- [(x)] 5

************************************************


                 {{5}}
************************************************

Por que o programa abaixo está errado?

```python
print(round(n, 2))
n = 3.1416
```

- [( )] Porque a função `round` foi usada antes de ser importada
- [(x)] Porque a variável `n` foi usada antes de receber um valor


************************************************

                 {{6}}
************************************************

Considere os trechos de código abaixo:

(a)

```python
x = randint(1,10)
if < 5:
  print('Primeira metade')
```

(b)

```python
x = randint(1,10)
if x < 5:
  print('Primeira metade')
```

Qual código contém um erro?

- [(x)] (a)
- [( )] (b)


************************************************


## Sobre os exercícios entregues


### Enquete

Quando solicitado em aula, siga estas instruções:

- CLique no botão de compartilhamento
- Clique em Classroom
- Selecione o backend informado pela professora
- Preencha o `room` informado pela professora


Você visualizou as informações sobre Avaliação desta disciplina no Moodle?

[(sim)] Sim
[(nao)] Não
[(naosei)] Não sei


### Lembretes

- exercícios fazem parte da avaliação
- prazo de entrega até a aula seguinte (ou plano de recuperação)
- objetivo não é obter nota, é obter experiência com a prática
- revisão pela professora: feedback e andamento da turma
- alertas automáticos de plágio: exercícios podem ficar sem nota e exigir verificação adicional
- se tiver dificuldade, busque ajuda, mas **nunca copie**





## Mais sobre condicionais

O que fazer quando temos que testar muitas condições em um programa?


![Placas com muitas direções](https://thumbs.dreamstime.com/b/road-signs-different-ways-road-signs-different-ways-isolated-white-background-103326906.jpg)

### Um caso com muitas condições

Por exemplo, vejamos esta tabela de classificação do IMC (Índice de Massa Corporal), obtida em: https://www.tuasaude.com/imc/


<!-- data-type="none" -->
| IMC (kg/m**2)   | Classificação   |
| :--------- | :------------  | 
| Menor que 18.5       | Magreza     |
| 18.5 a 24.9      | Peso normal      | 
| 25 a 29.9        | Sobrepeso          | 
| 30 a 34.9        | Obesidade grau I         | 
| 35 a 40       | Obesidade grau II | 
| Maior que 40       | Obesidade grau III | 

### Usando `if`s aninhados

- No exemplo do IMC, precisamos testar progressivamente várias condições
- Uma opção para isso é usar vários `if`/`else` aninhados (blocos recuados contendo mais `if`/`else`)


```python
def classifimc(p, h):
  imc = p/h**2
  if imc < 18.5:
    return "Magreza"
  else:
    if imc <= 24.9:
      return "Peso normal"
    else: 
      if imc <= 29.9:
        return "Sobrepeso"
      else:
        if imc <= 34.9:
          return "Obesidade grau I"
        else:
          if imc <= 40:
            return "Obesidade grau II"
          else:
            return "Obesidade grau III"


peso = 80
altura = 1.70
print(classifimc(peso,altura))
```


### Usando `elif`

- Muitos `if`s aninhados podem deixar um programa difícil de entender
- `elif` combina `else` com `if` em uma única linha de código


Reescrevendo o código anterior: 

```python
def classifimc(p, h):
  imc = p/h**2
  if imc < 18.5:
    return "Magreza"
  elif imc <= 24.9:
    return "Peso normal"
  elif imc <= 29.9:
    return "Sobrepeso"
  elif imc <= 34.9:
    return "Obesidade grau I"
  elif imc <= 40:
    return "Obesidade grau II"
  else:
    return "Obesidade grau III"

peso = 80
altura = 1.70
print(classifimc(peso,altura))
```

Quando um bloco aninhado só tem uma linha, podemos escrevê-lo de forma compactada:

```python
def classifimc(p, h):
  imc = p/h**2
  if imc < 18.5:    return "Magreza"
  elif imc <= 24.9: return "Peso normal"
  elif imc <= 29.9: return "Sobrepeso"
  elif imc <= 34.9: return "Obesidade grau I"
  elif imc <= 40:   return "Obesidade grau II"
  else:             return "Obesidade grau III"

peso = 80
altura = 1.70
print(classifimc(peso,altura))
```


### Operadores lógicos

- Servem para combinar duas ou mais condições
- Operadores: `and`, `or`, `not`
- Cada operando é uma condição que resulta `True` ou `False`

#### Exemplos

Considere `x = 4`:

<!-- data-type="none" -->
| Operador   | Significado    | Exemplo    | Resultado   |
| :--------- | :------------  | :--------- | :--------- |
| `and`       | "e" lógico    | `x > 2 and x < 10`     | `True`    |
| `or`      | "ou" lógico      | `x < 10 or x > 100`     | `False`     |
| `not`        | negação          | `not x < 0`      | `True` |

Teste no **interpretador**!

<iframe src="https://trinket.io/embed/python3/d52f952885?outputOnly=true&runOption=console&runMode=console" width="100%" height="300" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>



#### Tabelas-verdade

Tabela-verdade: combinações para `and` e `or`

<!-- data-type="none" -->
| a   | b    | a and b    | a or b   |
| :-- | :--  | :--------- | :--------- |
| `False`       | `False`    | `False`     | `False`     |
| `True`      | `False`     | `False`     | `True`     |
| `False`        | `True`       | `False`      | `True` |
| `True`        | `True`       | `True`      | `True` |

Tabela-verdade: combinações para `not`

<!-- data-type="none" -->
| a   | not a    | 
| :-- | :--  | 
| `False`       | `True`    | 
| `True`      | `False`     | 



### Jogo: Boolean Game

Pense rápido e resolva estes desafios com expressões booleanas!

https://booleangame.com/

Este jogo não usa Python, mas basta usar esta "tradução" dos operadores lógicos:

- `&&` significa `and`
- `||` significa `or`
- `!` significa `not`



## Execução passo-a-passo

- Visualizar a execução passo-a-passo pode ser útil para:

  - entender um programa
  - depurar o programa: localizar e corrigir erros (bugs)

- Ferramentas: Python Tutor, Debug no Repl.it, etc.

### Python Tutor (1)
Um [exemplo](https://pythontutor.com/visualize.html#code=from%20random%20import%20randint%0A%0A%23%20neste%20ambiente,%20o%20n%C3%BAmero%20vai%20se%20repetir%0An%20%3D%20randint%281,6%29%0Aprint%28'Tirei',%20n%29%0Aif%20%28n%20%3D%3D%206%29%3A%0A%20%20%20%20print%28'Que%20sorte!'%29%0Aprint%28'Fim%20do%20programa'%29%20%20%20%20&cumulative=false&heapPrimitives=true&mode=edit&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false) passo-a-passo com `if`:



<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/visualize.html#code=from%20random%20import%20randint%0A%0A%23%20neste%20ambiente,%20o%20n%C3%BAmero%20vai%20se%20repetir%0An%20%3D%20randint%281,6%29%0Aprint%28'Tirei',%20n%29%0Aif%20%28n%20%3D%3D%206%29%3A%0A%20%20%20%20print%28'Que%20sorte!'%29%0Aprint%28'Fim%20do%20programa'%29%20%20%20%20&cumulative=false&heapPrimitives=true&mode=edit&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>



### Python Tutor (2)

Um [exemplo](https://pythontutor.com/visualize.html#code=from%20random%20import%20randint%0Acontador%20%3D%200%0A%0An%20%3D%20randint%281,6%29%0Aprint%28n%29%0Aif%20n%20%3D%3D%204%3A%0A%20%20%20%20contador%20%3D%20contador%20%2B%201%0A%20%20%20%20%0An%20%3D%20randint%281,6%29%0Aprint%28n%29%0Aif%20n%20%3D%3D%204%3A%0A%20%20%20%20contador%20%3D%20contador%20%2B%201%0A%20%20%20%20%0An%20%3D%20randint%281,6%29%0Aprint%28n%29%0Aif%20n%20%3D%3D%204%3A%0A%20%20%20%20contador%20%3D%20contador%20%2B%201%0A%20%20%20%20%0An%20%3D%20randint%281,6%29%0Aprint%28n%29%0Aif%20n%20%3D%3D%204%3A%0A%20%20%20%20contador%20%3D%20contador%20%2B%201%0A%20%20%20%20%0Aprint%28'Quantas%20vezes%20sorteamos%20o%20n%C3%BAmero%204%3F',%20contador%29&cumulative=false&curInstr=17&heapPrimitives=true&mode=display&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false) passo-a-passo com `if` e variável contadora:

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/visualize.html#code=from%20random%20import%20randint%0Acontador%20%3D%200%0A%0An%20%3D%20randint%281,6%29%0Aprint%28n%29%0Aif%20n%20%3D%3D%204%3A%0A%20%20%20%20contador%20%3D%20contador%20%2B%201%0A%20%20%20%20%0An%20%3D%20randint%281,6%29%0Aprint%28n%29%0Aif%20n%20%3D%3D%204%3A%0A%20%20%20%20contador%20%3D%20contador%20%2B%201%0A%20%20%20%20%0An%20%3D%20randint%281,6%29%0Aprint%28n%29%0Aif%20n%20%3D%3D%204%3A%0A%20%20%20%20contador%20%3D%20contador%20%2B%201%0A%20%20%20%20%0An%20%3D%20randint%281,6%29%0Aprint%28n%29%0Aif%20n%20%3D%3D%204%3A%0A%20%20%20%20contador%20%3D%20contador%20%2B%201%0A%20%20%20%20%0Aprint%28'Quantas%20vezes%20sorteamos%20o%20n%C3%BAmero%204%3F',%20contador%29&cumulative=false&curInstr=17&heapPrimitives=true&mode=display&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>



## Exercícios no Repl.it

- Entre no grupo da disciplina no Repl.it: https://replit.com/teams/join/bzmdfmvrldnyymssuydqhwpkmoidivlo-elc106-2023a

- Em `Projects`, selecione a `aula04` 

- Veja as `Instructions` e preencha os exercícios no arquivo `main.py`

- Use `Run` com frequência para testar seu código

- Clique em `Submit` para enviar os exercícios para a professora

- Mais adiante, use a aba `Threads` para visualizar comentários da professora sobre seu código
