# O Mapa de Karnaugh

## 1. Caso simples: disjuntor + interruptor

Variáveis:

```text
D = disjuntor fechado
I = interruptor fechado
L = lâmpada acesa
```

Regra:

```text
L = D ∧ I
```

Tabela verdade:

|   D |   I |   L |
| --: | --: | --: |
|   0 |   0 |   0 |
|   0 |   1 |   0 |
|   1 |   0 |   0 |
|   1 |   1 |   1 |

Mapa de Karnaugh com 2 variáveis:

| D \ I |   0 |   1 |
| ----- | --: | --: |
| 0     |   0 |   0 |
| 1     |   0 |   1 |

Só existe um `1`, na posição:

```text
D = 1
I = 1
```

Logo, não há o que simplificar além de:

```text
L = D ∧ I
```

Em português lógico:

```text
A lâmpada acende somente se o disjuntor estiver fechado E o interruptor estiver fechado.
```

---

# 2. Circuito com continuidade correta

Agora adicionamos:

```text
C = continuidade correta do circuito
```

Regra:

```text
L = D ∧ I ∧ C
```

Tabela verdade:

|   D |   I |   C |   L |
| --: | --: | --: | --: |
|   0 |   0 |   0 |   0 |
|   0 |   0 |   1 |   0 |
|   0 |   1 |   0 |   0 |
|   0 |   1 |   1 |   0 |
|   1 |   0 |   0 |   0 |
|   1 |   0 |   1 |   0 |
|   1 |   1 |   0 |   0 |
|   1 |   1 |   1 |   1 |

Mapa de Karnaugh com 3 variáveis:

Usamos `D` nas linhas e `IC` nas colunas.
A ordem das colunas deve seguir **código Gray**, para mudar apenas um bit por vez:

```text
IC = 00, 01, 11, 10
```

| D \ IC |  00 |  01 |  11 |  10 |
| ------ | --: | --: | --: | --: |
| 0      |   0 |   0 |   0 |   0 |
| 1      |   0 |   0 |   1 |   0 |

O único `1` está em:

```text
D = 1
I = 1
C = 1
```

Resultado:

```text
L = D ∧ I ∧ C
```

Também não há simplificação, porque só existe uma combinação válida.

---

# 3. Circuito correto com ausência de erro crítico

Agora a regra fica mais próxima do nosso infográfico dos erros:

```text
D = disjuntor fechado
I = interruptor fechado
C = continuidade correta
E = erro crítico presente
L = lâmpada acesa
```

Regra:

```text
L = D ∧ I ∧ C ∧ ¬E
```

Ou seja:

```text
A lâmpada só acende se:
- o disjuntor estiver fechado;
- o interruptor estiver fechado;
- houver continuidade;
- não houver erro crítico.
```

Tabela verdade resumida:

|   D |   I |   C |   E |   L |
| --: | --: | --: | --: | --: |
|   0 |   0 |   0 |   0 |   0 |
|   0 |   0 |   0 |   1 |   0 |
|   0 |   0 |   1 |   0 |   0 |
|   0 |   0 |   1 |   1 |   0 |
|   0 |   1 |   0 |   0 |   0 |
|   0 |   1 |   0 |   1 |   0 |
|   0 |   1 |   1 |   0 |   0 |
|   0 |   1 |   1 |   1 |   0 |
|   1 |   0 |   0 |   0 |   0 |
|   1 |   0 |   0 |   1 |   0 |
|   1 |   0 |   1 |   0 |   0 |
|   1 |   0 |   1 |   1 |   0 |
|   1 |   1 |   0 |   0 |   0 |
|   1 |   1 |   0 |   1 |   0 |
|   1 |   1 |   1 |   0 |   1 |
|   1 |   1 |   1 |   1 |   0 |

Mapa de Karnaugh com 4 variáveis:

Vamos organizar assim:

```text
Linhas: DI
Colunas: CE
```

Com ordem Gray:

```text
DI = 00, 01, 11, 10
CE = 00, 01, 11, 10
```

| DI \ CE |  00 |  01 |  11 |  10 |
| ------- | --: | --: | --: | --: |
| 00      |   0 |   0 |   0 |   0 |
| 01      |   0 |   0 |   0 |   0 |
| 11      |   0 |   0 |   0 |   1 |
| 10      |   0 |   0 |   0 |   0 |

O único `1` está em:

```text
D = 1
I = 1
C = 1
E = 0
```

Resultado:

```text
L = D ∧ I ∧ C ∧ ¬E
```

Aqui também não há simplificação, porque a lâmpada só acende em uma única condição.

---

# 4. Mapa de Karnaugh para “sistema seguro”

Agora vem a parte mais interessante.

No infográfico dos erros, temos:

```text
CC = curto-circuito
PI = ponto incorreto
CA = circuito aberto
SB = sobrecarga
OK = sistema seguro
```

Regra:

```text
OK = ¬CC ∧ ¬PI ∧ ¬CA ∧ ¬SB
```

Ou seja: o sistema só está seguro se **nenhuma falha estiver presente**.

Mapa de Karnaugh:

```text
Linhas: CC PI
Colunas: CA SB
```

Ordem Gray:

```text
CCPI = 00, 01, 11, 10
CASB = 00, 01, 11, 10
```

| CCPI \ CASB |  00 |  01 |  11 |  10 |
| ----------- | --: | --: | --: | --: |
| 00          |   1 |   0 |   0 |   0 |
| 01          |   0 |   0 |   0 |   0 |
| 11          |   0 |   0 |   0 |   0 |
| 10          |   0 |   0 |   0 |   0 |

O único `1` está em:

```text
CC = 0
PI = 0
CA = 0
SB = 0
```

Logo:

```text
OK = ¬CC ∧ ¬PI ∧ ¬CA ∧ ¬SB
```

Também não há simplificação, porque só existe uma condição plenamente segura.

---

# 5. Mapa de Karnaugh para “há falha”

Agora fica mais rico, porque a saída será `1` para qualquer falha.

Variáveis:

```text
CC = curto-circuito
PI = ponto incorreto
CA = circuito aberto
SB = sobrecarga
F = há falha
```

Regra:

```text
F = CC ∨ PI ∨ CA ∨ SB
```

Ou seja: se qualquer falha existir, o sistema está em falha.

Tabela lógica:

|  CC |  PI |  CA |  SB |   F |
| --: | --: | --: | --: | --: |
|   0 |   0 |   0 |   0 |   0 |
|   0 |   0 |   0 |   1 |   1 |
|   0 |   0 |   1 |   0 |   1 |
|   0 |   0 |   1 |   1 |   1 |
|   0 |   1 |   0 |   0 |   1 |
|   0 |   1 |   0 |   1 |   1 |
|   0 |   1 |   1 |   0 |   1 |
|   0 |   1 |   1 |   1 |   1 |
|   1 |   0 |   0 |   0 |   1 |
|   1 |   0 |   0 |   1 |   1 |
|   1 |   0 |   1 |   0 |   1 |
|   1 |   0 |   1 |   1 |   1 |
|   1 |   1 |   0 |   0 |   1 |
|   1 |   1 |   0 |   1 |   1 |
|   1 |   1 |   1 |   0 |   1 |
|   1 |   1 |   1 |   1 |   1 |

Mapa de Karnaugh:

| CCPI \ CASB |  00 |  01 |  11 |  10 |
| ----------- | --: | --: | --: | --: |
| 00          |   0 |   1 |   1 |   1 |
| 01          |   1 |   1 |   1 |   1 |
| 11          |   1 |   1 |   1 |   1 |
| 10          |   1 |   1 |   1 |   1 |

Aqui o mapa mostra que **tudo é falha, exceto a célula 0000**.

A expressão simplificada é:

```text
F = CC ∨ PI ∨ CA ∨ SB
```

Ou, de forma equivalente:

```text
F = ¬OK
```

Como:

```text
OK = ¬CC ∧ ¬PI ∧ ¬CA ∧ ¬SB
```

Então, pela Lei de De Morgan:

```text
F = ¬(¬CC ∧ ¬PI ∧ ¬CA ∧ ¬SB)
```

Aplicando De Morgan:

```text
F = CC ∨ PI ∨ CA ∨ SB
```

Essa é uma das melhores pontes para explicar lógica booleana.

---

# 6. Mapa de Karnaugh final do funcionamento correto

Agora podemos unir tudo:

```text
D = disjuntor fechado
I = interruptor fechado
C = continuidade correta
CC = curto-circuito
PI = ponto incorreto
CA = circuito aberto
SB = sobrecarga
FC = funcionamento correto
```

Regra final:

```text
FC = D ∧ I ∧ C ∧ ¬CC ∧ ¬PI ∧ ¬CA ∧ ¬SB
```

Essa expressão tem 7 variáveis. Para aula inicial, **não é recomendável montar um Karnaugh completo de 7 variáveis**, porque ele teria:

```text
2⁷ = 128 combinações
```

Didaticamente, é melhor quebrar em blocos:

```text
Comando = D ∧ I
Integridade = C
SemFalhas = ¬CC ∧ ¬PI ∧ ¬CA ∧ ¬SB
FC = Comando ∧ Integridade ∧ SemFalhas
```

Assim:

```python
comando = disjuntor_fechado and interruptor_fechado

sem_falhas = (
    not curto_circuito
    and not ponto_incorreto
    and not circuito_aberto
    and not sobrecarga
)

funcionamento_correto = comando and continuidade_correta and sem_falhas
```

---

# 7. Como eu explicaria isso para os alunos

A frase didática seria:

> A tabela verdade mostra todas as possibilidades. O mapa de Karnaugh mostra onde estão os resultados verdadeiros e ajuda a simplificar a regra lógica.

No nosso caso, a maioria das regras tem apenas **um estado correto**:

```text
Tudo fechado, contínuo e sem falhas.
```

Por isso, os mapas do funcionamento correto ficam com apenas um `1`.

Já o mapa da falha é o contrário:

```text
Qualquer erro já torna a saída verdadeira para falha.
```

Então o mapa de falha fica quase todo preenchido com `1`.

Essa diferença é muito boa para aula:

```text
Funcionamento correto → condição restritiva → poucos 1
Falha detectada → condição ampla → muitos 1
```

---

# 8. Resumo final

| Situação                       | Expressão                                | Mapa de Karnaugh         |
| ------------------------------ | ---------------------------------------- | ------------------------ |
| Lâmpada simples                | `L = D ∧ I`                              | um único `1`             |
| Lâmpada com continuidade       | `L = D ∧ I ∧ C`                          | um único `1`             |
| Lâmpada sem erro               | `L = D ∧ I ∧ C ∧ ¬E`                     | um único `1`             |
| Sistema seguro                 | `OK = ¬CC ∧ ¬PI ∧ ¬CA ∧ ¬SB`             | um único `1`             |
| Há falha                       | `F = CC ∨ PI ∨ CA ∨ SB`                  | todos `1`, exceto 0000   |
| Funcionamento correto completo | `FC = D ∧ I ∧ C ∧ ¬CC ∧ ¬PI ∧ ¬CA ∧ ¬SB` | melhor dividir em blocos |

A leitura pedagógica principal é:

```text
Sistema correto exige conjunção: tudo precisa estar certo.
Sistema em falha aceita disjunção: basta uma coisa estar errada.
```
