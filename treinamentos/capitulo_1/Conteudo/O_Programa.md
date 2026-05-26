# O PROGRAMA (Python)

A estrutura ideal é transformar o circuito em um **simulador lógico**, não em um simulador elétrico real. Ou seja: o Python não “calcula eletricidade”; ele avalia **estados booleanos**.

A base fica assim:

```text
Disjuntor fechado?      True / False
Interruptor fechado?    True / False
Continuidade correta?   True / False
Existe falha?           True / False

Lâmpada ligada?         True / False
```

E usamos os símbolos para representar visualmente o estado.

---

# 1. Convenção visual

Para as chaves:

```text
🟢 ── / ── 🔴 = chave aberta  = ❌
🟢 ────── 🔴 = chave fechada = ⚡
```

Para a lâmpada:

```text
⚫ = lâmpada desligada
🟡 = lâmpada ligada
```

Na lógica:

```python
chave_fechada = True   # ⚡
chave_aberta = False   # ❌
```

---

# 2. Estrutura conceitual do programa

A arquitetura simples pode ter:

```text
1. Funções de renderização visual
2. Funções de lógica booleana
3. Função de diagnóstico
4. Função principal do simulador
5. Laço de repetição para testar combinações
```

A regra principal do circuito correto seria:

```python
lampada_ligada = (
    disjuntor_fechado
    and interruptor_fechado
    and continuidade_correta
    and not existe_falha
)
```

---

# 3. Código-base em Python

```python
def renderizar_chave(nome: str, fechada: bool) -> str:
    """
    Representa visualmente uma chave do circuito.

    fechada = True  -> 🟢 ────── 🔴 = ⚡
    fechada = False -> 🟢 ── / ── 🔴 = ❌
    """
    if fechada:
        return f"{nome}: 🟢 ────── 🔴  ⚡ FECHADA"
    return f"{nome}: 🟢 ── / ── 🔴  ❌ ABERTA"


def renderizar_lampada(ligada: bool) -> str:
    """
    Representa visualmente a lâmpada.
    """
    if ligada:
        return "Lâmpada: 🟡 LIGADA"
    return "Lâmpada: ⚫ DESLIGADA"


def circuito_funciona(
    disjuntor_fechado: bool,
    interruptor_fechado: bool,
    continuidade_correta: bool,
    existe_falha: bool
) -> bool:
    """
    Regra lógica principal:

    A lâmpada só liga se:
    - o disjuntor estiver fechado;
    - o interruptor estiver fechado;
    - houver continuidade correta;
    - não existir falha crítica.
    """
    return (
        disjuntor_fechado
        and interruptor_fechado
        and continuidade_correta
        and not existe_falha
    )


def diagnosticar(
    disjuntor_fechado: bool,
    interruptor_fechado: bool,
    continuidade_correta: bool,
    existe_falha: bool
) -> list[str]:
    """
    Retorna uma lista de mensagens explicando por que o circuito
    funciona ou não funciona.
    """
    problemas = []

    if not disjuntor_fechado:
        problemas.append("O disjuntor está aberto. Não há alimentação útil no circuito.")

    if not interruptor_fechado:
        problemas.append("O interruptor está aberto. O comando não fecha o caminho.")

    if not continuidade_correta:
        problemas.append("A continuidade está interrompida. O caminho elétrico não se completa.")

    if existe_falha:
        problemas.append("Existe falha crítica. O sistema não deve operar.")

    if not problemas:
        problemas.append("Circuito correto: alimentação, comando, continuidade e ausência de falha.")

    return problemas


def simular_circuito(
    disjuntor_fechado: bool,
    interruptor_fechado: bool,
    continuidade_correta: bool,
    existe_falha: bool
) -> None:
    """
    Mostra o estado completo do circuito.
    """
    lampada_ligada = circuito_funciona(
        disjuntor_fechado,
        interruptor_fechado,
        continuidade_correta,
        existe_falha
    )

    print("=" * 60)
    print("SIMULADOR LÓGICO DE CIRCUITO")
    print("=" * 60)

    print(renderizar_chave("Disjuntor", disjuntor_fechado))
    print(renderizar_chave("Interruptor", interruptor_fechado))

    print()

    print(f"Continuidade correta: {'✅ SIM' if continuidade_correta else '❌ NÃO'}")
    print(f"Existe falha crítica: {'❌ SIM' if existe_falha else '✅ NÃO'}")

    print()

    print(renderizar_lampada(lampada_ligada))

    print()
    print("Diagnóstico:")

    for mensagem in diagnosticar(
        disjuntor_fechado,
        interruptor_fechado,
        continuidade_correta,
        existe_falha
    ):
        print(f"- {mensagem}")

    print("=" * 60)
```

---

# 4. Exemplo dos 3 plays do circuito correto

```python
# PLAY 1
# Disjuntor aberto + interruptor aberto
simular_circuito(
    disjuntor_fechado=False,
    interruptor_fechado=False,
    continuidade_correta=True,
    existe_falha=False
)

# PLAY 2
# Disjuntor fechado + interruptor aberto
simular_circuito(
    disjuntor_fechado=True,
    interruptor_fechado=False,
    continuidade_correta=True,
    existe_falha=False
)

# PLAY 3
# Disjuntor fechado + interruptor fechado
simular_circuito(
    disjuntor_fechado=True,
    interruptor_fechado=True,
    continuidade_correta=True,
    existe_falha=False
)
```

Resultado lógico esperado:

```text
PLAY 1 -> ⚫ lâmpada desligada
PLAY 2 -> ⚫ lâmpada desligada
PLAY 3 -> 🟡 lâmpada ligada
```

---

# 5. Exemplo com erro crítico

Agora podemos simular o caso do segundo infográfico.

```python
# Circuito aparentemente fechado, mas com falha crítica
simular_circuito(
    disjuntor_fechado=True,
    interruptor_fechado=True,
    continuidade_correta=True,
    existe_falha=True
)
```

Resultado esperado:

```text
Disjuntor: fechado
Interruptor: fechado
Continuidade: correta
Falha crítica: sim
Lâmpada: ⚫ desligada
```

Porque a regra é:

```python
lampada_ligada = True and True and True and not True
```

Ou seja:

```python
lampada_ligada = False
```

---

# 6. Versão com tipos de falha

Para ficar mais próximo do infográfico, em vez de usar só `existe_falha`, podemos separar os erros:

```python
def existe_falha(
    curto_circuito: bool,
    ponto_incorreto: bool,
    circuito_aberto: bool,
    sobrecarga: bool
) -> bool:
    """
    Uma única falha já torna o sistema inseguro.
    """
    return (
        curto_circuito
        or ponto_incorreto
        or circuito_aberto
        or sobrecarga
    )
```

Agora a regra fica mais completa:

```python
def circuito_funciona_com_falhas(
    disjuntor_fechado: bool,
    interruptor_fechado: bool,
    continuidade_correta: bool,
    curto_circuito: bool,
    ponto_incorreto: bool,
    circuito_aberto: bool,
    sobrecarga: bool
) -> bool:
    falha_detectada = existe_falha(
        curto_circuito,
        ponto_incorreto,
        circuito_aberto,
        sobrecarga
    )

    return (
        disjuntor_fechado
        and interruptor_fechado
        and continuidade_correta
        and not falha_detectada
    )
```

Em forma lógica:

```text
FUNCIONAMENTO_CORRETO =
D ∧ I ∧ C ∧ ¬CC ∧ ¬PI ∧ ¬CA ∧ ¬SB
```

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

---

# 7. Programa completo com menu simples

Aqui está uma versão didática, pronta para aula:

```python
def ler_booleano(pergunta: str) -> bool:
    """
    Lê uma resposta simples do usuário.
    Aceita S/s para sim e N/n para não.
    """
    while True:
        resposta = input(f"{pergunta} [s/n]: ").strip().lower()

        if resposta == "s":
            return True

        if resposta == "n":
            return False

        print("Resposta inválida. Digite apenas 's' ou 'n'.")


def renderizar_chave(nome: str, fechada: bool) -> str:
    if fechada:
        return f"{nome}: 🟢 ────── 🔴  ⚡ FECHADA"
    return f"{nome}: 🟢 ── / ── 🔴  ❌ ABERTA"


def renderizar_lampada(ligada: bool) -> str:
    if ligada:
        return "Lâmpada: 🟡 LIGADA"
    return "Lâmpada: ⚫ DESLIGADA"


def existe_falha(
    curto_circuito: bool,
    ponto_incorreto: bool,
    circuito_aberto: bool,
    sobrecarga: bool
) -> bool:
    return (
        curto_circuito
        or ponto_incorreto
        or circuito_aberto
        or sobrecarga
    )


def circuito_funciona(
    disjuntor_fechado: bool,
    interruptor_fechado: bool,
    continuidade_correta: bool,
    curto_circuito: bool,
    ponto_incorreto: bool,
    circuito_aberto: bool,
    sobrecarga: bool
) -> bool:
    falha_detectada = existe_falha(
        curto_circuito,
        ponto_incorreto,
        circuito_aberto,
        sobrecarga
    )

    return (
        disjuntor_fechado
        and interruptor_fechado
        and continuidade_correta
        and not falha_detectada
    )


def diagnosticar(
    disjuntor_fechado: bool,
    interruptor_fechado: bool,
    continuidade_correta: bool,
    curto_circuito: bool,
    ponto_incorreto: bool,
    circuito_aberto: bool,
    sobrecarga: bool
) -> list[str]:
    diagnosticos = []

    if not disjuntor_fechado:
        diagnosticos.append("Disjuntor aberto: o circuito não recebe alimentação útil.")

    if not interruptor_fechado:
        diagnosticos.append("Interruptor aberto: o comando não fecha o caminho.")

    if not continuidade_correta:
        diagnosticos.append("Continuidade incorreta: existe caminho interrompido.")

    if curto_circuito:
        diagnosticos.append("Curto-circuito: falha crítica semelhante a crash imediato.")

    if ponto_incorreto:
        diagnosticos.append("Ponto incorreto: semelhante a estado inválido ou lógica incorreta.")

    if circuito_aberto:
        diagnosticos.append("Circuito aberto: semelhante a referência ausente ou fluxo interrompido.")

    if sobrecarga:
        diagnosticos.append("Sobrecarga: semelhante a esgotamento de recursos ou out of memory.")

    if not diagnosticos:
        diagnosticos.append("Circuito lógico correto: sistema pode operar.")

    return diagnosticos


def exibir_resultado(
    disjuntor_fechado: bool,
    interruptor_fechado: bool,
    continuidade_correta: bool,
    curto_circuito: bool,
    ponto_incorreto: bool,
    circuito_aberto: bool,
    sobrecarga: bool
) -> None:
    lampada_ligada = circuito_funciona(
        disjuntor_fechado,
        interruptor_fechado,
        continuidade_correta,
        curto_circuito,
        ponto_incorreto,
        circuito_aberto,
        sobrecarga
    )

    print()
    print("=" * 70)
    print("SIMULADOR LÓGICO: CIRCUITO ELÉTRICO E FALHAS DE PROGRAMAÇÃO")
    print("=" * 70)

    print(renderizar_chave("Disjuntor", disjuntor_fechado))
    print(renderizar_chave("Interruptor", interruptor_fechado))

    print()
    print(f"Continuidade correta: {'✅ SIM' if continuidade_correta else '❌ NÃO'}")
    print(f"Curto-circuito: {'❌ SIM' if curto_circuito else '✅ NÃO'}")
    print(f"Ponto incorreto: {'❌ SIM' if ponto_incorreto else '✅ NÃO'}")
    print(f"Circuito aberto: {'❌ SIM' if circuito_aberto else '✅ NÃO'}")
    print(f"Sobrecarga: {'❌ SIM' if sobrecarga else '✅ NÃO'}")

    print()
    print(renderizar_lampada(lampada_ligada))

    print()
    print("Diagnóstico:")

    for item in diagnosticar(
        disjuntor_fechado,
        interruptor_fechado,
        continuidade_correta,
        curto_circuito,
        ponto_incorreto,
        circuito_aberto,
        sobrecarga
    ):
        print(f"- {item}")

    print("=" * 70)


def main() -> None:
    print("Simulador lógico de circuito")
    print("Use este programa apenas como analogia didática entre circuitos e programação.")
    print()

    disjuntor_fechado = ler_booleano("O disjuntor está fechado?")
    interruptor_fechado = ler_booleano("O interruptor está fechado?")
    continuidade_correta = ler_booleano("A continuidade do circuito está correta?")

    print()
    print("Agora informe se há falhas didáticas no sistema.")
    print()

    curto_circuito = ler_booleano("Existe curto-circuito?")
    ponto_incorreto = ler_booleano("Existe fase, neutro ou retorno em ponto incorreto?")
    circuito_aberto = ler_booleano("Existe circuito aberto?")
    sobrecarga = ler_booleano("Existe sobrecarga?")

    exibir_resultado(
        disjuntor_fechado,
        interruptor_fechado,
        continuidade_correta,
        curto_circuito,
        ponto_incorreto,
        circuito_aberto,
        sobrecarga
    )


if __name__ == "__main__":
    main()
```

---

# 8. Exemplo de execução esperada

Entrada:

```text
O disjuntor está fechado? [s/n]: s
O interruptor está fechado? [s/n]: s
A continuidade do circuito está correta? [s/n]: s

Existe curto-circuito? [s/n]: n
Existe fase, neutro ou retorno em ponto incorreto? [s/n]: n
Existe circuito aberto? [s/n]: n
Existe sobrecarga? [s/n]: n
```

Saída:

```text
Disjuntor: 🟢 ────── 🔴  ⚡ FECHADA
Interruptor: 🟢 ────── 🔴  ⚡ FECHADA

Continuidade correta: ✅ SIM
Curto-circuito: ✅ NÃO
Ponto incorreto: ✅ NÃO
Circuito aberto: ✅ NÃO
Sobrecarga: ✅ NÃO

Lâmpada: 🟡 LIGADA

Diagnóstico:
- Circuito lógico correto: sistema pode operar.
```

---

# 9. Estrutura ideal para explicar em aula

O programa ensina estes blocos ao mesmo tempo:

| Conceito elétrico  | Conceito lógico   | Conceito em Python |
| ------------------ | ----------------- | ------------------ |
| Disjuntor fechado  | condição booleana | `True`             |
| Interruptor aberto | condição falsa    | `False`            |
| Lâmpada ligada     | saída lógica      | variável calculada |
| Curto-circuito     | falha crítica     | `or` em falhas     |
| Circuito correto   | conjunção         | `and`              |
| Ausência de erro   | negação           | `not`              |
| Diagnóstico        | tomada de decisão | `if`               |
| Simulação          | fluxo completo    | funções            |

A frase central para os alunos é:

```text
Quando todas as condições necessárias são verdadeiras e nenhuma falha está ativa, o sistema funciona.
```

Em Python:

```python
funciona = condicao_1 and condicao_2 and condicao_3 and not falha
```

Essa é a ponte entre:

```text
circuito elétrico → tabela verdade → Karnaugh → lógica booleana → programa Python
```
