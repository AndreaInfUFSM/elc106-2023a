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
-->
<!--
liascript-devserver --input README.md --port 3001 --live
-->

# Aula 00

> Este material serve de referência para o primeiro encontro com a turma e para consultas durante o andamento da disciplina.

## Vamos nos conhecer!

Queremos que cada colega de turma se apresente para o grupo (nome, curso, naturalidade, etc.). Como fazer isso?

Você consegue entender as instruções abaixo? Vamos tentar segui-las para conhecer a turma!

```
M = total de mesas na sala
x = primeira mesa da fila mais próxima à porta
visitadas = 0
repita até visitadas == M:
  se x tem estudante:
    - convide estudante a se apresentar
  incremente visitadas
  se visitadas < M:
    se houver mesa atrás de x:
      - x = classe atrás de x
    senão:
      - x = primeira classe da fila à esquerda de x
```

## Vamos conhecer a disciplina!


Na sequência temos as informações gerais sobre a disciplina e o plano de ensino.

### Objetivos

Ao final desta disciplina, os estudantes deverão ser capazes de:

- Formular soluções para problemas, visando a obtenção dos resultados por computador. 
- Escrever programas utilizando uma linguagem de programação.


### Programa

Programa da disciplina no site da UFSM:
https://www.ufsm.br/ementario/disciplinas/ELC106

**IMPORTANTE**: As unidades da disciplina serão abordadas seguindo as melhores práticas da atualidade, conforme a tabela abaixo.

| Unidade | Observações |
| ------- | ----------- | 
| UNIDADE 1 - INTRODUÇÃO AO ESTUDO DO PROCESSAMENTO DE DADOS | Esta unidade trata da composição e do funcionamento básico dos computadores. Será abordada na primeira aula para destacar os elementos que têm grande influência na programação.  |
| UNIDADE 2 - CONCEITOS DE ANÁLISE DE SISTEMAS | Esta unidade diferencia algoritmo de programa e trata de uma abordagem metódica e estruturada para resolução de problemas. Será abordada na primeira aula e mesclada com as outras unidades.  |
| UNIDADE 3 - SOLUÇÕES DE PROBLEMAS UTILIZANDO O COMPUTADOR | Esta unidade introduz conceitos para aconstrução de algoritmos estruturados, independentemente de linguagem. Será abordada gradualmente junto com a unidade seguinte. |
| UNIDADE 4 - ESTRUTURA DOS PROGRAMAS | Esta unidade trata da elaboração de programas em uma linguagem de programação específica. Será abordada gradualmente ao longo do semestre, desde a segunda aula.   |

### Estratégias de ensino e aprendizagem

A disciplina utilizará estratégias de aprendizagem ativa, com a maior parte da carga horária dedicada a práticas de resolução de problemas com programação.
As aulas serão predominantemente estruturadas segundo a abordagem pedagógica PRIMM (Predict, Run, Investigate, Modify, Make)[1].

[1] Sentance, S., Waite, J., & Kallia, M. (2019) Teaching computer programming with PRIMM: a sociocultural perspective. Computer Science Education. 29 (2–3), 136–176.
DOI: 10.1080/08993408.2019.1608781.

### Avaliação

A avaliação vai considerar a produção dos estudantes a cada bimestre, nas seguintes modalidades e com os seguintes pesos:

Primeiro bimestre:

- Exercícios práticos (entregues durante a aula ou até antes da aula seguinte): peso 2.5
- Avaliação prática extraclasse - 03/05/2023: peso 2.5
- Avaliação prática em aula - 10/05/2023: peso 5.0

Segundo bimestre:

- Exercícios práticos (entregues durante a aula ou até antes da aula seguinte): peso 2.5
- Avaliação prática extraclasse: peso 2.5
- Apresentação de projeto final personalizado de programação - 05/07/2023: peso 5.0

Avaliação final (exame): 19/07/2023

A fim de incentivar um comportamento ativo e auto-regulado dos estudantes com o aprendizado, algumas avaliações poderão, **opcionalmente**, ser complementadas ou substituídas conforme:

- **Plano individual de recuperação**: para estudantes que identificarem dificuldades na realização de atividades avaliativas (atrasos justificados, problemas de compreensão, imprevistos com recursos computacionais, etc.)
- **Plano individual de aprofundamento**: para estudantes que possuírem um conhecimento prévio do conteúdo da disciplina e/ou interesse em ir além do conteúdo do programa

Estes planos serão elaborados pelos estudantes interessados, sob orientação da professora, e preenchidos em formulários a serem fornecidos durante o semestre.

### Bibliografia

Vamos priorizar livros disponíveis online gratuitamente ou acessíveis via portal de E-Books Minha Biblioteca da UFSM:
http://portal.ufsm.br/biblioteca/leitor/minhaBiblioteca.html

#### Livros

- Paiva, Fábio A. P. e outros. **Introdução a Python** com aplicações de sistemas operacionais. Editora IFRN, 2021. Disponível em: https://memoria.ifrn.edu.br/handle/1044/2090


- Banin, Sérgio L. **Python 3 - Conceitos e Aplicações - Uma abordagem didática**. Editora Saraiva, 2018. ISBN 9788536530253. Disponível em: https://integrada.minhabiblioteca.com.br/books/9788536530253/

- Barry, Paul. **Use a Cabeça! Python**. Editora Alta Books, 2018. ISBN 9786555207842. Disponível em: https://integrada.minhabiblioteca.com.br/books/9786555207842/

- Piva Jr., Dilermando e outros. **Algoritmos e Programação de Computadores**. Grupo GEN, 2019. ISBN 9788595150508. Disponível em: https://integrada.minhabiblioteca.com.br/books/9788595150508/

- Menéndez, Andrés. **Simplificando Algoritmos**. Grupo GEN, 2023. ISBN 9788521638339. Disponível em: https://integrada.minhabiblioteca.com.br/books/9788521638339/





#### Vídeos

- Curso de Python 3 - Mundo 1: Fundamentos. Curso em Vídeo. Gustavo Guanabara. https://www.youtube.com/watch?v=S9uPNppGsGo&list=PLHz_AreHm4dlKP6QQCekuIPky1CiwmdI6

- Curso de Python 3 - Mundo 2: Estruturas de Controle. Curso em Vídeo. Gustavo Guanabara. https://www.youtube.com/watch?v=nJkVHusJp6E&list=PLHz_AreHm4dk_nZHmxxf_J0WRAqy5Czye

- Python para Zumbis. Fernando Masanori. https://www.youtube.com/watch?v=YO58tXerKDc&list=PLUukMN0DTKCtbzhbYe2jdF4cr8MOWClXc


## Perguntas e respostas

Apresentação da disciplina na forma de perguntas e respostas:

<hr> 

- P: O que vou aprender nesta disciplina?
- R: Vai aprender a expressar a solução de problemas por computador, usando uma linguagem de programação.

<hr> 

- P: Por que aprender a programar?
- R: Computadores e algoritmos estão presentes por toda parte na sociedade moderna. Entender de programação é a chave para compreender como tudo isso funciona e também para assumir um papel de protagonismo (você pode criar programas, não só usá-los). Isso é muito valorizado no mercado.

<hr>
- P: Que linguagem de programação vou aprender?
- R: Python

<hr>

- P: Por que Python foi escolhida?
- R: Por que é uma linguagem muito usada no mundo todo para introdução à programação, além de ser uma das mais importantes em aplicações de ciência de dados.

<hr>
- P: Python é melhor que R? 
- R: Isso depende do critério de comparação. Python é uma linguagem de propósito mais geral que R, por isso pode ser considerada mais versátil.


<hr>

- P: Como serão as aulas?
- R: Vão ser presenciais e predominantemente práticas.

<hr>

- P: Posso fazer a disciplina à distância?
- R: Não. Embora existam muitos cursos online sobre o assunto e seja possível aprender muito com eles, esta disciplina pretende aproveitar a interação presencial para diversificar as atividades e assim "turbinar" o aprendizado.

<hr>

- P: Onde encontro o material das aulas?
- Q: No Moodle.

<hr>



## Você no comando: programa seu colega!


A seguir, uma atividade de programação sem computadores!

Material:

- Colegas! :-)
- Piso quadriculado
- Instruções (a seguir)
- Objetivos (a seguir)

### Instruções (linguagem)

Instruções entendidas pelo colega (linguagem):

- avance um passo para frente (A)
- gire 90 graus à esquerda (GE)
- gire 90 graus à direita (GD)

### Objetivos dos programas

Exemplos de objetivos:

- Partindo da posição atual, chegar até colega/professora
- Partindo de um ponto da sala, chegar à porta/janela
- Partindo da posição atual, percorrer todos os quadrados do piso (!)



