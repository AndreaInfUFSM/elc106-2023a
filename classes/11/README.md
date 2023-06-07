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
          https://cdn.jsdelivr.net/gh/andreainfufsm/elc106-2023a/classes/11/custom.css

-->


# Aula 11



- Hoje: mais manipulação de dados em arquivos
  
  



## Manipulando dados em arquivos



### Arquivos CSV

- Formato *Comma Separated Values* (CSV)
- Dados tabulares
- "Separados por vírgula" (mas podem ter outros delimitadores)

![](https://peltiertech.com/images/2017-02/csv-data-1.png)


#### Bibliotecas

Muitas bibliotecas em Python facilitam a manipulação deste tipo de arquivo:

- Standard Library: https://docs.python.org/pt-br/3/library/csv.html
- NumPy: https://numpy.org/doc/stable/user/how-to-io.html
- Pandas: https://pandas.pydata.org/docs/reference/io.html
- Standard x Pandas: https://realpython.com/python-csv/

> Pandas é a melhor opção para grandes volumes de dados e uso profissional com pouca escrita de código.

> Para quem é iniciante em lógica de programação, vale treinar com a biblioteca CSV (built-in, standard).

#### Funções reader e writer

- Usamos essas funções depois de abrir arquivos para leitura / escrita (ver Aula 10)
- Função `writer` retorna um tipo de variável com capacidade de escrita em arquivo CSV
- Função `reader` retorna um tipo de variável com capacidade de leitura

```python
import csv

f = open('notas.csv', 'w')
w = csv.writer(f)
w.writerow(['matricula', 'nota'])
w.writerow(['1234', '9'])
w.writerow(['1235', '10'])
w.writerow(['1236', '8.5'])
f.close()

f = open("notas.csv", "r")
r = csv.reader(f)
for row in r:
  print(row)
f.close()
```
@LIA.python3()

#### Cabeçalho

E se quisermos "pular" o cabeçalho?



 <details>
  <summary>Saiba como...</summary>
  <p>Podemos usar next(), uma função que se aplica a "iteráveis" em Python. 
Saiba mais em: https://cienciaprogramada.com.br/2021/08/iteradores-e-iteraveis-em-python/
  </p>
</details>



```python
import csv

f = open('notas.csv', 'w')
w = csv.writer(f)
w.writerow(['matricula', 'nota'])
w.writerow(['1234', '9'])
w.writerow(['1235', '10'])
w.writerow(['1236', '8.5'])
f.close()

f = open("notas.csv", "r")
r = csv.reader(f)
next(r)
for row in r:
  print(row)
f.close()
```
@LIA.python3()



### Exemplos com CSV



#### Escrita e leitura de arquivo

Escrita e leitura de arquivo usando biblioteca `csv`

```python
import csv

f = open('matrix.csv', 'w')
w = csv.writer(f)
w.writerow(['x', 'y', 'z'])
for i in range(5):
  for j in range(4):
    w.writerow([i, j, i+j])
f.close()

f = open("matrix.csv", "r")
r = csv.reader(f)
matrix = []
for row in r:
  matrix.append(row)
f.close()
print(f'This matrix has {len(matrix)} rows and {len(matrix[0])} columns')

```
@LIA.python3()

#### Download de CSV pela rede

Combinando CSV com a biblioteca `requests`

```python
import requests
import csv

url = "http://www.inf.ufsm.br/~andrea/DATA.csv"

# Download the CSV file
response = requests.get(url)
content = response.text 

f = open("DATA.csv", "w")
f.write(content)
f.close()
print("Arquivo salvo com sucesso!")
```
@LIA.python3()

Saiba mais em...

- Oficial: https://requests.readthedocs.io/en/latest/
- Simplificado: https://www.hashtagtreinamentos.com/biblioteca-requests-no-python


#### Download e processamento

- Sem salvar arquivo em disco
- Trabalhando com delimitadores

```python
import requests
import csv

url = "http://www.inf.ufsm.br/~andrea/DATA.csv"

# Download the CSV file
response = requests.get(url)
content = response.content.decode("utf-8").splitlines()


# Read the CSV content using csv module
reader = csv.reader(content, delimiter=';')
for row in reader:
  print(row[0]) ## primeira coluna, índice 0
```
@LIA.python3()






## Exercícios no Repl.it

- Entre no grupo da disciplina no Repl.it: https://replit.com/teams/join/bzmdfmvrldnyymssuydqhwpkmoidivlo-elc106-2023a

- Em `Projects`, selecione a `aula11` 

- Veja as `Instructions` e preencha os exercícios nos arquivos indicados

- Use `Run` com frequência para testar seu código

- Clique em `Submit` para enviar os exercícios para a professora

- Mais adiante, use a aba `Threads` para visualizar comentários da professora sobre seu código

