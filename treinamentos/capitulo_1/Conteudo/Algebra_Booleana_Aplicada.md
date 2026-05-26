# APLICANDO A ÁLGEBRA BOOLEANA

A aplicação da **Álgebra Booleana** entra como a ponte formal entre:

```text
circuito elétrico → tabela verdade → mapa de Karnaugh → regra lógica → programa Python
```

No nosso caso, ela serve para transformar estados como **aberto/fechado**, **ligado/desligado**, **com falha/sem falha** em expressões lógicas que o aluno consegue calcular, simplificar e implementar.

---

# 1. Primeiro conhecimento aplicado: estados binários

A Álgebra Booleana trabalha com dois valores:

```text
0 = falso / desligado / aberto / ausente
1 = verdadeiro / ligado / fechado / presente
```

No circuito:

| Elemento            | Estado físico         | Estado booleano |
| ------------------- | --------------------- | --------------: |
| Disjuntor aberto    | não permite passagem  |               0 |
| Disjuntor fechado   | permite passagem      |               1 |
| Interruptor aberto  | circuito interrompido |               0 |
| Interruptor fechado | circuito fechado      |               1 |
| Lâmpada apagada     | saída falsa           |               0 |
| Lâmpada acesa       | saída verdadeira      |               1 |
| Falha ausente       | condição segura       |               0 |
| Falha presente      | condição de erro      |               1 |

Então a representação visual vira lógica:

```text
🟢 ── / ── 🔴 = 0
🟢 ────── 🔴 = 1

⚫ = 0
🟡 = 1
```

---

# 2. Segunda aplicação: operador E / AND

No circuito correto, a lâmpada só acende quando **todas as condições necessárias** estão verdadeiras.

Variáveis:

```text
D = disjuntor fechado
I = interruptor fechado
C = continuidade correta
L = lâmpada ligada
```

Regra:

L = D \land I \land C

Leitura:

```text
A lâmpada liga se D E I E C forem verdadeiros.
```

Em Python:

```python
lampada_ligada = (
    disjuntor_fechado
    and interruptor_fechado
    and continuidade_correta
)
```

Essa é uma aplicação direta da operação **conjunção**.

---

# 3. Terceira aplicação: operador NÃO / NOT

Quando entra o contexto dos erros, a lâmpada só deve ligar se **não houver falha**.

Variáveis de falha:

```text
CC = curto-circuito
PI = ponto incorreto
CA = circuito aberto
SB = sobrecarga
```

Para o sistema estar seguro:

OK = \neg CC \land \neg PI \land \neg CA \land \neg SB

Leitura:

```text
O sistema está OK se NÃO houver curto,
E NÃO houver ponto incorreto,
E NÃO houver circuito aberto,
E NÃO houver sobrecarga.
```

Em Python:

```python
sistema_ok = (
    not curto_circuito
    and not ponto_incorreto
    and not circuito_aberto
    and not sobrecarga
)
```

Aqui o aluno aprende que `not` inverte o valor lógico:

```text
not True  = False
not False = True
```

---

# 4. Quarta aplicação: operador OU / OR

Para detectar falha, basta **uma condição de erro** ser verdadeira.

F = CC \lor PI \lor CA \lor SB

Leitura:

```text
Há falha se existir curto OU ponto incorreto OU circuito aberto OU sobrecarga.
```

Em Python:

```python
falha_detectada = (
    curto_circuito
    or ponto_incorreto
    or circuito_aberto
    or sobrecarga
)
```

Esse ponto é excelente para explicar a diferença entre **AND** e **OR**:

| Operador | Ideia                       | Exemplo             |
| -------- | --------------------------- | ------------------- |
| `and`    | tudo precisa ser verdadeiro | para funcionar      |
| `or`     | basta um ser verdadeiro     | para detectar falha |
| `not`    | inverte o valor             | para negar erro     |

---

# 5. Quinta aplicação: expressão completa do funcionamento correto

Agora juntamos tudo:

```text
O circuito funciona se:
- disjuntor está fechado;
- interruptor está fechado;
- há continuidade correta;
- não há curto;
- não há ponto incorreto;
- não há circuito aberto;
- não há sobrecarga.
```

Expressão:

FC = D \land I \land C \land \neg CC \land \neg PI \land \neg CA \land \neg SB

Em Python:

```python
funcionamento_correto = (
    disjuntor_fechado
    and interruptor_fechado
    and continuidade_correta
    and not curto_circuito
    and not ponto_incorreto
    and not circuito_aberto
    and not sobrecarga
)
```

Essa é a expressão central do nosso simulador.

---

# 6. Sexta aplicação: Lei de De Morgan

A Lei de De Morgan é muito importante aqui, porque mostra que:

```text
“não há nenhuma falha”
```

é equivalente a:

```text
“não existe curto, nem ponto incorreto, nem circuito aberto, nem sobrecarga”
```

Se:

```text
F = CC ∨ PI ∨ CA ∨ SB
```

Então:

OK = \neg(CC \lor PI \lor CA \lor SB)

Pela Lei de De Morgan:

\neg(CC \lor PI \lor CA \lor SB) = \neg CC \land \neg PI \land \neg CA \land \neg SB

Em Python, estas duas formas são equivalentes:

```python
falha_detectada = (
    curto_circuito
    or ponto_incorreto
    or circuito_aberto
    or sobrecarga
)

sistema_ok = not falha_detectada
```

Ou:

```python
sistema_ok = (
    not curto_circuito
    and not ponto_incorreto
    and not circuito_aberto
    and not sobrecarga
)
```

Essa é uma aplicação prática excelente para mostrar que a Álgebra Booleana não é teoria solta: ela muda a forma como escrevemos código.

---

# 7. Sétima aplicação: simplificação lógica

Podemos organizar o programa em blocos menores.

Em vez de escrever tudo em uma única expressão grande:

```python
funcionamento_correto = (
    disjuntor_fechado
    and interruptor_fechado
    and continuidade_correta
    and not curto_circuito
    and not ponto_incorreto
    and not circuito_aberto
    and not sobrecarga
)
```

Podemos decompor:

```python
comando_ok = disjuntor_fechado and interruptor_fechado

integridade_ok = continuidade_correta

falha_detectada = (
    curto_circuito
    or ponto_incorreto
    or circuito_aberto
    or sobrecarga
)

sistema_ok = not falha_detectada

funcionamento_correto = (
    comando_ok
    and integridade_ok
    and sistema_ok
)
```

Essa decomposição aplica três ideias da Álgebra Booleana:

```text
1. Agrupamento
2. Reuso de expressões
3. Clareza lógica
```

E também ensina uma prática profissional: **nomear condições complexas**.

---

# 8. O que o aluno aprende com isso

A aplicação do conhecimento de Álgebra Booleana nesse projeto permite ensinar:

| Conhecimento      | Aplicação no circuito      | Aplicação em Python     |
| ----------------- | -------------------------- | ----------------------- |
| Variável booleana | chave aberta/fechada       | `True` / `False`        |
| AND               | tudo precisa estar correto | `and`                   |
| OR                | qualquer erro gera falha   | `or`                    |
| NOT               | ausência de erro           | `not`                   |
| Tabela verdade    | combinações possíveis      | testes de entrada       |
| Karnaugh          | simplificação visual       | refatoração lógica      |
| De Morgan         | negar grupo de falhas      | `not (a or b)`          |
| Diagnóstico       | identificar a causa        | `if`, `elif`, mensagens |

---

# 9. Estrutura ideal para aula

A sequência pedagógica ficaria assim:

```text
1. Mostrar o circuito com chave aberta e fechada
2. Converter aberto/fechado em 0 e 1
3. Montar a tabela verdade
4. Escrever a expressão booleana
5. Montar o mapa de Karnaugh
6. Simplificar ou confirmar a expressão
7. Implementar em Python
8. Exibir diagnóstico textual
```

A frase principal da aula pode ser:

```text
A Álgebra Booleana é a linguagem formal que permite transformar estados físicos, decisões lógicas e condições de erro em regras computáveis.
```

---

# 10. Aplicação final no simulador

O coração lógico do programa fica assim:

```python
def circuito_funciona(
    disjuntor_fechado: bool,
    interruptor_fechado: bool,
    continuidade_correta: bool,
    curto_circuito: bool,
    ponto_incorreto: bool,
    circuito_aberto: bool,
    sobrecarga: bool
) -> bool:
    comando_ok = disjuntor_fechado and interruptor_fechado

    integridade_ok = continuidade_correta

    falha_detectada = (
        curto_circuito
        or ponto_incorreto
        or circuito_aberto
        or sobrecarga
    )

    sistema_ok = not falha_detectada

    return comando_ok and integridade_ok and sistema_ok
```

Essa função é a representação direta da Álgebra Booleana aplicada:

```text
comando_ok = D ∧ I
integridade_ok = C
falha_detectada = CC ∨ PI ∨ CA ∨ SB
sistema_ok = ¬falha_detectada
funcionamento = comando_ok ∧ integridade_ok ∧ sistema_ok
```

Em uma frase:

```text
O programa é uma tabela verdade executável.
```
