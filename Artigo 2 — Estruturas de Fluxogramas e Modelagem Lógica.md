# Artigo 2 — Estruturas de Fluxogramas e Modelagem Lógica

<p align="center">
  <img src="https://img.shields.io/badge/Fluxograma-Estruturas_e_Modelagem-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/RLLabs-Engenharia_de_Software-7f5af0?style=for-the-badge">
  <img src="https://img.shields.io/badge/Foco-Planejamento_antes_do_Código-00c896?style=for-the-badge">
  <img src="https://img.shields.io/badge/Nível-Fundamentos_Profissionais-ffcc00?style=for-the-badge">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/57891531-1e8e-474f-837f-5098f8fe1253" width="240">
</p>

---

# 01. Estruturas de Fluxogramas

O fluxograma não é apenas desenho.

Ele representa o raciocínio lógico antes da programação e organiza o pensamento para transformar análise em software.

Quando usamos a figura errada:

* o algoritmo fica confuso;
* a manutenção fica mais difícil;
* a conversão para código perde clareza.

---

# 02. Objetivo do Artigo

Este material explica:

* por que usamos fluxogramas;
* como escolher a figura correta;
* quais são as figuras principais e suas funções;
* como aplicar esse raciocínio no projeto UVVON;
* como o fluxograma se conecta com Python.

---

# 03. Sumário

* [Por que usar fluxogramas](#1-por-que-usar-fluxogramas)
* [Pensamento antes da figura](#2-estrutura-de-pensamento-antes-da-figura)
* [Principais figuras](#3-principais-figuras-e-quando-usar)
* [Escolha correta da figura](#4-como-escolher-a-figura-correta)
* [Aplicação no UVVON](#5-aplicando-ao-projeto-uvvon)
* [Fluxograma e Python](#6-fluxogramas-e-relação-com-python)
* [Erros comuns](#7-erros-comuns-em-fluxogramas)
* [Filosofia do time](#8-filosofia-usada-pelo-time)
* [Conclusão técnica](#9-conclusão-técnica)

---

# 1. Por Que Usar Fluxogramas

Antes de programar, precisamos responder:

* o que entra;
* o que acontece;
* o que é calculado;
* o que é decidido;
* o que sai.

O fluxograma transforma isso em:

* visão estrutural;
* sequência lógica;
* rastreamento de decisões;
* prevenção de erros;
* planejamento do código.

---

# 2. Estrutura de Pensamento Antes da Figura

Antes de desenhar qualquer bloco:

```text
Isso é uma ação?
→ PROCESSO

Isso é uma decisão?
→ DECISÃO

Isso é entrada ou saída?
→ ENTRADA/SAÍDA

Isso começa ou termina?
→ TERMINADOR
```

Essa sequência evita ambiguidades e acelera a modelagem.

---

# 3. Principais Figuras e Quando Usar

# FIGURA 1 — TERMINADOR

Forma: oval.

Representa:

* início;
* encerramento;
* parada abrupta;
* saída final.

Exemplos:

* INÍCIO;
* FIM;
* ENCERRADO PELO USUÁRIO.

---

# FIGURA 2 — PROCESSO

Forma: retângulo.

Representa:

* cálculos;
* processamento;
* transformações;
* ações executadas.

Exemplos:

* Calcular média do módulo;
* Gerar tabela;
* Converter texto para decimal;
* Somar AOP1 + AOP2 + AOP3 + PR.

---

# FIGURA 3 — DECISÃO

Forma: losango.

Representa:

* perguntas;
* bifurcações;
* escolhas;
* condicionais.

Exemplos:

* MM >= 7?;
* Nota pertence ao RAID?;
* Usuário deseja sair?.

Saídas típicas:

* SIM / NÃO;
* VERDADEIRO / FALSO.

---

# FIGURA 4 — ENTRADA / SAÍDA

Forma: paralelogramo.

Representa:

* leitura;
* exibição;
* comunicação com o usuário.

Exemplos:

* Ler nota AOP1;
* Digite a nota:;
* Exibir resultado final.

---

# FIGURA 5 — CONECTOR

Forma: círculo pequeno.

Função:

* conectar partes distantes do fluxograma;
* organizar fluxos em múltiplas páginas;
* evitar cruzamento de linhas.

---

# FIGURA 6 — SUBPROCESSO

Forma: retângulo com bordas laterais duplas.

Representa:

* módulo;
* função externa;
* rotina separada.

Exemplos:

* Executar validação de entrada;
* Executar cálculo da recuperação.

---

# 4. Como Escolher a Figura Correta

Método mental rápido:

```text
PASSO 1
Estou PEDINDO algo?
→ Entrada/Saída

PASSO 2
Estou CALCULANDO algo?
→ Processo

PASSO 3
Estou DECIDINDO algo?
→ Decisão

PASSO 4
Estou COMEÇANDO ou TERMINANDO?
→ Terminador

PASSO 5
Isso virou uma função separada?
→ Subprocesso
```

---

# 5. Aplicando ao Projeto UVVON

Etapas do fluxo:

1. Início → **Terminador** (`INÍCIO`)
2. Ler notas → **Entrada/Saída** (`Ler AOP1`)
3. Validar nota → **Decisão** (`Nota pertence ao RAID?`)
4. Calcular MM → **Processo** (`MM = AOP1 + AOP2 + AOP3 + PR`)
5. Aprovação direta → **Decisão** (`MM >= 7?`)
6. Recuperação → **Decisão** (`3 < MM < 7?`)
7. Calcular MG → **Processo** (`MG = (MM + REC) / 2`)
8. Exibir resultado → **Entrada/Saída** (`Exibir status final`)
9. Encerramento → **Terminador** (`FIM`)

---

# 6. Fluxogramas e Relação com Python

Mapeamento prático:

* Processo → cálculo/função;
* Decisão → `if` / `elif` / `else`;
* Repetição → `while` / `for`;
* Entrada → `input()`;
* Saída → `print()`;
* Subprocesso → função;
* Terminador → início/fim.

---

# 7. Erros Comuns em Fluxogramas

## Erro 1 — Usar PROCESSO para pergunta

Errado:

```text
[Calcular] MM >= 7?
```

Correto:

```text
<Decisão> MM >= 7?
```

---

## Erro 2 — Misturar entrada com cálculo

Errado:

```text
Ler e calcular MM
```

Correto:

```text
Ler nota
↓
Calcular MM
```

---

## Erro 3 — Múltiplas decisões no mesmo losango

Errado:

```text
MM >= 7 e usuário quer sair?
```

Regra:

* cada decisão deve possuir responsabilidade clara.

---

# 8. Filosofia Usada pelo Time

```text
pensar
→ desenhar
→ testar no papel
→ validar fluxo
→ modularizar
→ programar
→ testar manualmente
→ integrar
```

Essa prática aproxima o projeto de um processo real de engenharia de software e reduz código sem planejamento lógico.

---

# 9. Conclusão Técnica

```text
O fluxograma organiza o pensamento computacional,
reduz ambiguidades,
melhora a qualidade da modelagem
e acelera a transformação da lógica em código Python.
```

Em contexto profissional, escolher a figura correta significa melhorar:

* legibilidade;
* manutenção;
* validação;
* qualidade arquitetural.

---

# 10. Redes Oficiais — Rubinho Lyra Labs

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

[← voltar](https://github.com/rubenslyra/penso-logo-programo)
