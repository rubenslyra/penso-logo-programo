# Artigo 1 — Estruturas de Dados, Fluxo Lógico e Engenharia de Software

<p align="center">
  <img src="https://img.shields.io/badge/Python-Estruturas_de_Dados-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/RLLabs-Pensamento_Computacional-7f5af0?style=for-the-badge">
  <img src="https://img.shields.io/badge/Foco-Arquitetura_e_Modelagem-00c896?style=for-the-badge">
  <img src="https://img.shields.io/badge/Nível-Fundamentos_Profissionais-ffcc00?style=for-the-badge">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/57891531-1e8e-474f-837f-5098f8fe1253" width="240">
</p>

---

# 01. Estruturas de Dados, Fluxo Lógico e Engenharia de Software

Sua percepção está bastante correta e possui forte amparo:

* acadêmico;
* computacional;
* arquitetural;
* profissional.

Você está entrando exatamente no ponto onde a programação deixa de ser apenas “escrever código” e passa a ser:

* modelagem;
* engenharia;
* organização de informação;
* representação computacional do problema.

---

# 02. Objetivo do Artigo

Este material busca explicar:

* como estruturas de dados surgem;
* por que elas existem;
* como escolher a estrutura correta;
* como o fluxo lógico influencia decisões arquiteturais;
* como a engenharia de software utiliza essas estruturas no mundo real.

---

# 03. Sumário

* [Estruturas surgem do fluxo](#1-estruturas-de-dados-surgem-da-necessidade-do-fluxo)
* [Fluxo antes da estrutura](#2-o-fluxo-vem-antes-da-estrutura)
* [Inicialização manual e aprendizado](#3-por-que-aprendemos-inicializando-manualmente)
* [Pergunta profissional correta](#4-a-pergunta-profissional-correta)
* [Escolha de estruturas](#5-como-escolher-a-melhor-estrutura)
* [Listas](#caso-1--lista-list)
* [Dicionários](#caso-2--dicionário-dict)
* [Conjuntos](#caso-3--conjunto-set)
* [Tuplas](#caso-4--tupla-tuple)
* [Fluxograma e estruturas](#6-o-fluxograma-ajuda-a-escolher-estruturas)
* [Estruturas inadequadas](#7-estrutura-errada-gera-problemas-reais)
* [Conclusão técnica](#10-conclusão-técnica)
* [Referências científicas](#11-referências-científicas-e-bibliográficas)

---

# 1. Estruturas de Dados Surgem da Necessidade do Fluxo

A ideia principal é:

```text
Estruturas de dados não devem ser escolhidas primeiro.
Elas emergem da análise do problema,
das operações necessárias
e da forma como os dados precisam sobreviver,
ser acessados e manipulados.
```

Isso está alinhado com:

* Engenharia de Software;
* Estruturas de Dados;
* Análise de Algoritmos;
* Arquitetura de Sistemas.

---

# 2. O Fluxo Vem Antes da Estrutura

No ambiente profissional normalmente seguimos:

```text
problema
↓
regras de negócio
↓
fluxograma
↓
operações necessárias
↓
forma de acesso aos dados
↓
escolha da estrutura
↓
implementação
```

---

# Exemplo Aplicado — UVVON

Antes de criar:

```python
alunos = []
```

o time precisa responder:

```text
Precisamos guardar muitos alunos?
Precisamos percorrer todos?
Precisamos calcular porcentagens?
Precisamos manter ordem?
Precisamos impedir duplicidade?
```

As respostas praticamente revelam a estrutura correta.

---

# 3. Por Que Aprendemos Inicializando Manualmente?

Exemplo:

```python
aluno = {
    "nome": "Rubens",
    "media": 7
}
```

Isso existe principalmente por motivos pedagógicos:

* simplificação;
* visualização;
* assimilação;
* entendimento inicial.

Mas no mundo profissional essas estruturas normalmente surgem:

* do domínio do problema;
* das entidades do sistema;
* das regras de negócio;
* dos subprocessos.

---

# 4. A Pergunta Profissional Correta

O iniciante pergunta:

```text
Como usar lista?
```

O desenvolvedor mais maduro pergunta:

```text
Como os dados precisam se comportar?
```

Essa mudança altera:

* arquitetura;
* performance;
* manutenção;
* escalabilidade;
* clareza do sistema.

---

# 5. Como Escolher a Melhor Estrutura?

A regra principal é:

```text
A estrutura depende da operação dominante.
```

---

# CASO 1 — LISTA (`list`)

Usamos quando:

* precisamos manter ordem;
* percorremos elementos;
* exibimos relatórios;
* armazenamos múltiplos itens relacionados.

---

## Exemplo UVVON

```python
alunos = []
```

---

> ### Estrutura
>
> ```python
> lista = [1, 2, 3]
> ```
>
> ### Características
>
> * ordenada;
> * mutável;
> * acessível por índice;
> * dinâmica;
> * permite duplicidade.
>
> ### Finalidade
>
> Representar coleções sequenciais.
>
> ### Contexto histórico
>
> Inspirada em arrays dinâmicos e listas lineares da Ciência da Computação clássica.
>
> ### Base conceitual
>
> * memória sequencial;
> * acesso indexado;
> * estruturas lineares.
>
> ### Referências históricas
>
> Influenciada pelos estudos de:
>
> * John von Neumann
> * Donald Knuth

---

# CASO 2 — DICIONÁRIO (`dict`)

Usamos quando:

* cada dado possui significado;
* precisamos de chave → valor;
* modelamos entidades;
* buscamos rapidamente informações específicas.

---

## Exemplo UVVON

```python
aluno = {
    "nome": "Rubens",
    "media": 7,
    "status": "Aprovado"
}
```

---

> ### Estrutura
>
> ```python
> dicionario = {
>     "chave": "valor"
> }
> ```
>
> ### Características
>
> * chave → valor;
> * acesso rápido;
> * mutável;
> * altamente associativo.
>
> ### Finalidade
>
> Representar entidades e registros.
>
> ### Contexto histórico
>
> Baseado em:
>
> * tabelas hash;
> * indexação computacional;
> * mapeamento associativo.
>
> ### Base conceitual
>
> * hashing;
> * dispersão;
> * acesso por chave.
>
> ### Referências históricas
>
> Associado aos trabalhos de:
>
> * Hans Peter Luhn
> * Donald Knuth

---

# CASO 3 — CONJUNTO (`set`)

Usamos quando:

* não queremos repetição;
* precisamos garantir unicidade;
* queremos operações matemáticas de conjuntos.

---

## Exemplo

```python
matriculas = set()
```

---

> ### Estrutura
>
> ```python
> conjunto = {1, 2, 3}
> ```
>
> ### Características
>
> * sem duplicidade;
> * busca rápida;
> * não ordenado;
> * baseado em hashing.
>
> ### Finalidade
>
> Garantir unicidade.
>
> ### Contexto histórico
>
> Baseado diretamente na Teoria dos Conjuntos.
>
> ### Base conceitual
>
> * lógica matemática;
> * pertencimento;
> * teoria dos conjuntos.
>
> ### Referências históricas
>
> Associado aos estudos de:
>
> * Georg Cantor

---

# CASO 4 — TUPLA (`tuple`)

Usamos quando:

* os dados não devem mudar;
* queremos integridade estrutural;
* existe posição fixa.

---

## Exemplo

```python
cor_alerta = (255, 0, 0)
```

---

> ### Estrutura
>
> ```python
> tupla = (1, 2, 3)
> ```
>
> ### Características
>
> * ordenada;
> * imutável;
> * indexada.
>
> ### Finalidade
>
> Representar estruturas fixas.
>
> ### Contexto histórico
>
> Influenciada pela programação funcional.
>
> ### Base conceitual
>
> * imutabilidade;
> * segurança estrutural.
>
> ### Referências históricas
>
> Relacionada à evolução de:
>
> * Functional Programming

---

# 6. O Fluxograma Ajuda a Escolher Estruturas?

SIM. Muito.

---

## Exemplo

Fluxograma:

```text
Ler 100 alunos
↓
Calcular médias
↓
Gerar estatísticas
↓
Exibir relatório
```

Isso sugere automaticamente:

```python
list
dict
contadores
```

---

# 7. Estrutura Errada Gera Problemas Reais

Na engenharia profissional:

* estrutura inadequada destrói performance;
* dificulta manutenção;
* aumenta bugs;
* cria acoplamento;
* dificulta leitura.

---

# Exemplo Clássico

Pessoa usa:

```python
list
```

para algo que exige:

* unicidade;
* validação rápida;
* busca constante.

O correto seria:

```python
set
```

ou:

```python
dict
```

---

# 8. Fórmula Mental Profissional

```text
Fluxo
+
operações
+
regras de negócio
+
tipo de acesso
+
persistência necessária
=
estrutura de dados adequada
```

---

# 9. Aplicação no Projeto UVVON

Entrada simples:

```python
nota = float(input())
```

não exige estrutura complexa.

---

Depois do processamento precisamos:

* armazenar;
* calcular;
* agrupar;
* classificar;
* exibir.

Então surgem naturalmente:

```python
list
dict
```

---

# Estrutura madura para o sistema

```python
alunos = [
    {
        "matricula": 1,
        "media": 7,
        "status": "Aprovado"
    },
    {
        "matricula": 2,
        "media": 4,
        "status": "Recuperação"
    }
]
```

---

# 10. Conclusão Técnica

```text
Estruturas de dados não são escolhidas apenas pela sintaxe da linguagem.
Elas emergem da análise do problema,
das operações necessárias,
do fluxo lógico,
do comportamento esperado dos dados
e das exigências arquiteturais do sistema.
```

Isso está:

* academicamente correto;
* arquiteturalmente correto;
* alinhado com engenharia de software moderna.

---

# 11. Referências Científicas e Bibliográficas

## Livros clássicos

* Introduction to Algorithms
* The Art of Computer Programming
* Algorithms
* Clean Code
* Design Patterns

---

## Fundamentos matemáticos e computacionais

* Set Theory
* Hash Table
* Algorithm Analysis
* Data Structures
* Software Engineering

---

## Pesquisadores e referências históricas

* Donald Knuth
* John von Neumann
* Georg Cantor
* Alan Turing
* Edsger W. Dijkstra
* Barbara Liskov

---

# 12. Redes Oficiais — Rubinho Lyra Labs

<p align="center">
  <a href="https://www.instagram.com/rubinholyralabs/">
    <img src="https://img.shields.io/badge/Instagram-@rubinholyralabs-E4405F?style=for-the-badge&logo=instagram&logoColor=white">
  </a>

  <a href="https://www.youtube.com/@rubinholyralabs">
    <img src="https://img.shields.io/badge/YouTube-@rubinholyralabs-FF0000?style=for-the-badge&logo=youtube&logoColor=white">
  </a>

  <a href="https://www.tiktok.com/@rubinholyralabs">
    <img src="https://img.shields.io/badge/TikTok-@rubinholyralabs-000000?style=for-the-badge&logo=tiktok&logoColor=white">
  </a>
</p>

---

<p align="center">
  <img alt="Rubinho Lyra Labs" src="https://github.com/user-attachments/assets/85615b82-24a7-4f2d-a5d3-52b93a8333a6" width="220">
</p>

<p align="center">
  <strong>Rubinho Lyra Labs</strong><br>
  Pensar • Estruturar • Programar • Transformar
</p>

[← votlar](https://github.com/rubenslyra/penso-logo-programo)
