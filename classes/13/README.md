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

onload
window.CodeRunner = {
    ws: undefined,
    handler: {},

    init(url) {
        this.ws = new WebSocket(url);
        const self = this
        this.ws.onopen = function () {
            self.log("connections established");
            setInterval(function() {
                self.ws.send("ping")
            }, 15000);
        }
        this.ws.onmessage = function (e) {
            // e.data contains received string.

            let data
            try {
                data = JSON.parse(e.data)
            } catch (e) {
                self.warn("received message could not be handled =>", e.data)
            }
            if (data) {
                self.handler[data.uid](data)
            }
        }
        this.ws.onclose = function () {
            self.warn("connection closed")
        }
        this.ws.onerror = function (e) {
            self.warn("an error has occurred => ", e)
        }
    },
    log(...args) {
        console.log("CodeRunner:", ...args)
    },
    warn(...args) {
        console.warn("CodeRunner:", ...args)
    },
    handle(uid, callback) {
        this.handler[uid] = callback
    },
    send(uid, message) {
        message.uid = uid
        this.ws.send(JSON.stringify(message))
    }
}

//window.CodeRunner.init("wss://coderunner.informatik.tu-freiberg.de/")
//window.CodeRunner.init("wss://testing-coderunner.andreaschwertne.repl.co/")
window.CodeRunner.init("wss://pythoncoderunner.andreaschwertne.repl.co/")

//window.CodeRunner.init("wss://ancient-hollows-41316.herokuapp.com/")
//window.CodeRunner.init("ws://127.0.0.1:8000/")

@end


@LIA.python:  @LIA.python3
@LIA.python2: @LIA.eval(`["main.py"]`, `python2.7 -m compileall .`, `python2.7 main.pyc`)
@LIA.python3: @LIA.eval(`["main.py"]`, `none`, `python3 main.py`)


@LIA.eval:  @LIA.eval_(false,`@0`,@1,@2)

@LIA.evalWithDebug: @LIA.eval_(true,`@0`,@1,@2)

@LIA.eval_
<script>
function random(len=16) {
    let chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
    let str = '';
    for (let i = 0; i < len; i++) {
        str += chars.charAt(Math.floor(Math.random() * chars.length));
    }
    return str;
}

const uid = random()
var order = @1
var files = []

if (order[0])
  files.push([order[0], `@'input(0)`])
if (order[1])
  files.push([order[1], `@'input(1)`])
if (order[2])
  files.push([order[2], `@'input(2)`])
if (order[3])
  files.push([order[3], `@'input(3)`])
if (order[4])
  files.push([order[4], `@'input(4)`])
if (order[5])
  files.push([order[5], `@'input(5)`])
if (order[6])
  files.push([order[6], `@'input(6)`])
if (order[7])
  files.push([order[7], `@'input(7)`])
if (order[8])
  files.push([order[8], `@'input(8)`])
if (order[9])
  files.push([order[9], `@'input(9)`])


send.handle("input", (e) => {
    CodeRunner.send(uid, {stdin: e})
})
send.handle("stop",  (e) => {
    CodeRunner.send(uid, {stop: true})
});


CodeRunner.handle(uid, function (msg) {
    switch (msg.service) {
        case 'data': {
            if (msg.ok) {
                CodeRunner.send(uid, {compile: @2})
            }
            else {
                send.lia("LIA: stop")
            }
            break;
        }
        case 'compile': {
            if (msg.ok) {
                if (msg.message) {
                    if (msg.problems.length)
                        console.warn(msg.message);
                    else
                        console.log(msg.message);
                }

                send.lia("LIA: terminal")
                CodeRunner.send(uid, {exec: @3})

                if(!@0) {
                  console.clear()
                }
            } else {
                send.lia(msg.message, msg.problems, false)
                send.lia("LIA: stop")
            }
            break;
        }
        case 'stdout': {
            if (msg.ok)
                console.stream(msg.data)
            else
                console.error(msg.data);
            break;
        }

        case 'stop': {
            if (msg.error) {
                console.error(msg.error);
            }

            if (msg.images) {
                for(let i = 0; i < msg.images.length; i++) {
                    console.html("<hr/>", msg.images[i].file)
                    console.html("<img title='" + msg.images[i].file + "' src='" + msg.images[i].data + "' onclick='window.LIA.img.click(\"" + msg.images[i].data + "\")'>")
                }

            }

            send.lia("LIA: stop")
            break;
        }

        default:
            console.log(msg)
            break;
    }
})


CodeRunner.send(
    uid, { "data": files }
);

"LIA: wait"
</script>
@end
-->
<!--
nvm use v10.23.0
liascript-devserver --input README.md --port 3001 --live
link:     https://cdn.jsdelivr.net/gh/liascript/custom-style/custom.min.css
          https://cdn.jsdelivr.net/gh/andreainfufsm/elc106-2023a/classes/13/custom.css

-->


# Aula 13



Hoje: 

- mais casos com manipulação de dados
- geração de gráficos
  

> Para tudo isso, dependemos de... bibliotecas de **funções**!


## Relembrando funções

- Funções têm um nome
- Funções têm argumentos separados por vírgula
- Para executar função, devemos "chamá-la" (nome seguido de valores para argumentos)
- Funções retornam resultado no ponto em que foram chamadas

### Um poema!

**Funções: Mágicas Criaturas!** (by Prof. Andrea e ChatGPT :-) )

```
Funções, funções, encantos da programação,
Nas linhas de código, és a solução.
Com tuas habilidades, podemos criar,
Transformando problemas em algo a se admirar.

Palavras-chave como "def" e "return",
Em conjunto, formam um poder sem fim.
Dividindo o código em blocos de ação,
A modularidade se torna a nossa lição.

Com funções, evitamos repetição,
Reaproveitando trechos, com precisão.
Parâmetros e argumentos, juntos a passar,
Manipulando dados, sem complicar.

Do fluxo principal, nos afastamos um pouco,
Chamando a função, num momento oportuno.
Ela executa sua tarefa com maestria,
Devolvendo resultados, oh, que alegria!

Funções, funções, mágicas criaturas,
Com suas assinaturas, tão puras.
Nos ajudam a organizar o programa,
Facilitando a vida, como uma brisa suave e calma.

A cada passo, uma função a chamar,
Simplificando o código, sem se atrapalhar.
Dividir para conquistar, esse é o lema,
E com funções, o sucesso nos espera.

Então, jovens aprendizes, não se esqueçam,
Das funções, que são fontes de saber.
Com elas, a programação ganha mais vida,
Despertando a criatividade, na jornada infinita.

Por isso, estudem e pratiquem com afinco,
As funções são a chave, o elo distintivo.
Em cada projeto, deixem seu brilho resplandecer,
E conquistem o mundo da programação, com prazer!
```



### Bibliotecas

- Bibliotecas são coleções de funções (como caixas de ferramentas)
- Algumas bibliotecas conhecidas:

  - `math`
  - `random`
  - `csv`
  - `requests`

- Outras bibliotecas 'famosas':

  - `pandas`
  - `numpy`
  - `matplotlib`


##  Avançando com  `requests` e `csv`

Vamos usar `requests`, `csv` e outras bibliotecas

### Dataset: auto-avaliação

Você sabia que dados no Google Sheets podem ser publicados online para análise?

- Em CSV: https://docs.google.com/spreadsheets/d/e/2PACX-1vT34wBvu7oDIS7p_IxMDGHC5s5Rcgq-WOPVNnGJ8rx1c_KxTnDYf53x5LRHgTEcwXpL8lkf-tJNGV6a/pub?gid=1862471432&single=true&output=csv

- Em HTML: https://docs.google.com/spreadsheets/d/e/2PACX-1vT34wBvu7oDIS7p_IxMDGHC5s5Rcgq-WOPVNnGJ8rx1c_KxTnDYf53x5LRHgTEcwXpL8lkf-tJNGV6a/pub?gid=1862471432&single=true&output=html




### Leitura e inspeção 

Quando queremos inspecionar pequenos datasets...

```python
import requests
import csv

url = "https://docs.google.com/spreadsheets/d/e/2PACX-1vT34wBvu7oDIS7p_IxMDGHC5s5Rcgq-WOPVNnGJ8rx1c_KxTnDYf53x5LRHgTEcwXpL8lkf-tJNGV6a/pub?gid=1862471432&single=true&output=csv"

# Obtém conteúdo do arquivo disponibilizado na URL
response = requests.get(url)
# Transforma o conteúdo para leitura por linhas
# Conteúdo fica na memória principal (não salvo em arquivo)
content = response.content.decode("utf-8").splitlines()

# Lê o conteúdo usando a biblioteca csv
reader = csv.reader(content, delimiter=',')
## Para cada linha...
for row in reader: 
  ## Mostra elemento da primeira coluna (índice 0)
  print(row[0]) 
```
@LIA.python3()


### Download condicional 

- Não é uma boa prática fazer download a cada execução
- Se arquivo não estiver no computador, vamos obtê-lo pela rede
- Caso contrário, vamos ler do arquivo
- Biblioteca `os`:

  - acesso ao sistema operacional / sistema de arquivos
  - exemplos: https://www.geeksforgeeks.org/os-module-python-examples/


```python
import os
import csv
import requests

filename = "data.csv"
url = "https://docs.google.com/spreadsheets/d/e/2PACX-1vT34wBvu7oDIS7p_IxMDGHC5s5Rcgq-WOPVNnGJ8rx1c_KxTnDYf53x5LRHgTEcwXpL8lkf-tJNGV6a/pub?gid=1862471432&single=true&output=csv"

# Verifica se arquivo está presente no computador
if not os.path.isfile(filename):
  print('Fazendo download...')
  response = requests.get(url)
  f = open(filename, "wb")
  f.write(response.content)
  f.close()
  print('Download concluído...')

f = open(filename, "r")
r = csv.reader(f)
for row in r:
  print(row)
f.close()  
```
@LIA.python3()


### Usando `with`

- Forma mais avançada de lidar com arquivos
- Especifica blocos de código que precisam de uma "proteção" contra exceções
- Fecha arquivo automaticamente ao final do bloco (sem close)
- Exemplos em: https://www.geeksforgeeks.org/with-statement-in-python/

Versão com `with`:

```python
import os
import csv
import requests

filename = "data.csv"
url = "https://docs.google.com/spreadsheets/d/e/2PACX-1vT34wBvu7oDIS7p_IxMDGHC5s5Rcgq-WOPVNnGJ8rx1c_KxTnDYf53x5LRHgTEcwXpL8lkf-tJNGV6a/pub?gid=1862471432&single=true&output=csv"

# Verifica se arquivo está presente no computador
if not os.path.isfile(filename):
  print('Fazendo download...')
  response = requests.get(url)
  with open(filename, "wb") as f:
    f.write(response.content)
  print('Download concluído...')

with open(filename, "r") as f:
  r = csv.reader(f)
  for row in r:
    print(row)
```
@LIA.python3()

Versão sem `with`:


```python
import os
import csv
import requests

filename = "data.csv"
url = "https://docs.google.com/spreadsheets/d/e/2PACX-1vT34wBvu7oDIS7p_IxMDGHC5s5Rcgq-WOPVNnGJ8rx1c_KxTnDYf53x5LRHgTEcwXpL8lkf-tJNGV6a/pub?gid=1862471432&single=true&output=csv"

# Verifica se arquivo está presente no computador
if not os.path.isfile(filename):
  print('Fazendo download...')
  response = requests.get(url)
  f = open(filename, "wb")
  f.write(response.content)
  f.close()
  print('Download concluído...')

f = open(filename, "r")
r = csv.reader(f)
for row in r:
  print(row)
f.close()  
```
@LIA.python3()


### Armazenamento em lista


- Para analisar um dataset, é conveniente armazená-lo em alguma estrutura de dados (lista, etc)
- Neste exemplo, armazenamos em lista e processamos uma das colunas para obter o total de elementos que satisfazem uma condição


```python
import os
import csv
import requests

filename = "data.csv"
url = "https://docs.google.com/spreadsheets/d/e/2PACX-1vT34wBvu7oDIS7p_IxMDGHC5s5Rcgq-WOPVNnGJ8rx1c_KxTnDYf53x5LRHgTEcwXpL8lkf-tJNGV6a/pub?gid=1862471432&single=true&output=csv"

# Verifica se arquivo está presente no computador
if not os.path.isfile(filename):
  print('Fazendo download...')
  response = requests.get(url)
  with open(filename, "wb") as f:
    f.write(response.content)
  print('Download concluído...')

# Armazena dados em lista
data = []
with open(filename, "r") as f:
  r = csv.reader(f)
  for row in r:
    data.append(row)

# Processa lista verificando uma condição
count = 0
for row in data:
  to_count = row[1] # coluna de índice 1
  if to_count == '10':
      count += 1
  print(to_count)
print('Total:', count) 
```
@LIA.python3()













## Biblioteca `pandas`

- Abrevia muitas tarefas frequentes de manipulação de datasets
- Veja um resumo em: https://pt.wikipedia.org/wiki/Pandas_(software)
- O exemplo abaixo é semelhante ao anterior, porém bem mais curto
- Não usamos `requests` e `csv` porque `pandas` tem funções equivalentes
- "Pandas torna simples tarefas complicadas, mas pode complicar tarefas simples" 

```python
import pandas as pd

url = "https://docs.google.com/spreadsheets/d/e/2PACX-1vT34wBvu7oDIS7p_IxMDGHC5s5Rcgq-WOPVNnGJ8rx1c_KxTnDYf53x5LRHgTEcwXpL8lkf-tJNGV6a/pub?gid=1862471432&single=true&output=csv"

df = pd.read_csv(url)
total = (df.iloc[:,1] == '10').sum()
print('Total:', total)
```
@LIA.python3()



#### DataFrame

- Um recurso importante em Pandas é uma estrutura de dados chamada `DataFrame`
- Semelhante a uma matriz/tabela, com linhas e colunas rotuladas
- Muito mais sofisticado que "listas de listas"
- Veja uma explicação aqui: https://www.covildodev.com.br/artigo/criar-dataframes-pandas-python

![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/creating_dataframe1.png)

Fonte: https://www.geeksforgeeks.org/creating-a-pandas-dataframe/

#### Para saber mais...

- Há muitos tutoriais e documentação online sobre **Pandas**
- Nessa disciplina não há tempo para ver mais detalhes
- Além disso, o mais importante é saber a base da linguagem, não decorar exemplos e nomes de funções

- Algumas sugestões de material de referência:

  - Python para Estatísticos, capítulo 3.3: :https://tmfilho.github.io/pyestbook/math/04_pand.html
  - Pandas Tutorial W3Schools: https://www.w3schools.com/python/pandas/default.asp (resumido, em inglês)
  - Não sabe inglês? Que tal tentar mesmo assim? Nesta área, é essencial e abre muitas portas!
  - Faça uma busca e selecione materiais que fazem mais sentido para você

## Bibliotecas para visualização


Há uma grande variedade de bibliotecas para visualização de dados em Python

Para citar algumas:

- Matplotlib, Seaborn, ggpy (from ggplot in R)
- Mais "modernas", baseadas em JavaScript: Plotly, Bokeh, Vega


Fonte: https://pyviz.org/overviews/ 

![](https://rougier.github.io/python-visualization-landscape/landscape-colors.png)



### Vídeo

Vídeo: *The Python Visualization Landscape* (PyCon 2017)

https://www.youtube.com/watch?v=FytuB8nFHPQ

??[](https://www.youtube.com/watch?v=FytuB8nFHPQ)


## Usando `matplotlib` 

Tipos de gráficos: https://matplotlib.org/stable/plot_types/index.html
??[](https://matplotlib.org/stable/plot_types/index.html)

### Gráfico de linha

```python
import matplotlib.pyplot as plt

x = [0,1,2,3,4,5,6,7] 
#x = range(8)
y = x

plt.plot(x, y)
plt.xlabel('X')
plt.ylabel('Y')
plt.title('Gráfico X x Y')
plt.show()
```


### Gráfico de dispersão

```python
import matplotlib.pyplot as plt

# Data from:
# https://www.datacamp.com/tutorial/tutorial-datails-on-correlation

experience = [1, 3, 4, 5, 5, 6, 7, 10, 11, 12, 15, 20, 25, 28, 30,35]

salary = [20000, 30000, 40000, 45000, 55000, 60000, 80000, 100000, 130000, 150000, 200000, 230000, 250000, 300000, 350000, 400000]

plt.scatter(experience,salary)
plt.xlabel('Experience')
plt.ylabel('Salary')
plt.title('Experience x Salary')
plt.show()
```

### Gráfico de barras


```python
import matplotlib.pyplot as plt

prova = ['Leitura', 'Escrita']
media = [8.5,7]

plt.bar(prova, media)
#plt.bar(prova, media, color='green')
#plt.barh(prova, media)

plt.xlabel('Prova')
plt.ylabel('Média')
plt.title('Médias por Tipo de Prova')
plt.show()
```


### Com `csv`

```python
import csv
import matplotlib.pyplot as plt

filename = 'prova2cols.csv'

leitura = []
escrita = []
# Obtém dados do do CSV e preenche listas
with open(filename, "r") as f:
  r = csv.reader(f)
  next(r) # salta cabeçalho
  for row in r:
    leitura.append(float(row[0]))
    escrita.append(float(row[1]))

# Plota notas da prova de leitura
# Eixo x = sequência gerada
# Eixo y = notas de leitura
plt.bar(range(len(leitura)), leitura)
# Ordenar: sorted(leitura)

# Alternativa: 
# gerar letras para designar cada estudante
#names = [chr(ord('A')+i) for i in range(len(leitura))]
#plt.bar(names,leitura)

plt.xlabel('Estudante')
plt.ylabel('Nota')
plt.title('Notas em Leitura de Código')
plt.show()
```


### Com `pandas`

```python
import pandas as pd
import matplotlib.pyplot as plt

filename = 'prova2cols.csv'
df = pd.read_csv(filename)

# Plota notas da prova de leitura
# Eixo x = sequência gerada
# Eixo y = notas de leitura
leitura = df.iloc[:,0]
plt.bar(range(len(leitura)), leitura)
# Ordenar: sorted(leitura)

# Alternativa: 
# gerar letras para designar cada estudante
#names = [chr(ord('A')+i) for i in range(len(leitura))]
#plt.bar(names,leitura)

plt.xlabel('Estudante')
plt.ylabel('Nota')
plt.title('Notas em Leitura de Código')
plt.show()
```


## Extra: Plotly e Dash

- Biblioteca Plotly é muito usada para gráficos na Web
- Dash é uma ferramenta que usa Ploty para construir dashboards
- Exemplos: https://plotly.com/examples/ 
- Repl.it: https://dash.elc106-2023a.repl.co
- Veja código-fonte no Repl.it: projeto `dash` na seção `Extras (opcionais)`


## Exercícios no Repl.it

- Entre no grupo da disciplina no Repl.it: https://replit.com/teams/join/bzmdfmvrldnyymssuydqhwpkmoidivlo-elc106-2023a

- Em `Projects`, selecione a `aula13` 

- Preencha os exercícios nos arquivos indicados


- Clique em `Submit` para enviar os exercícios para a professora
