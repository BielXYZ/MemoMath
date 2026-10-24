# MemoMath - Memorização Matemática

Aplicativo minimalista para treinar a memorização matemática em alta velocidade com **1.5 segundos por dígito da resposta**.

Inspirado na arquitetura e simplicidade do [AbsolutePitch](https://github.com/BielXYZ/AbsolutePitch).

## Modos e Mecânicas

- **Timer Proporcional ao Tamanho da Resposta**:
  - O tempo disponível é `1.5 segundo × número de dígitos da resposta`, com mínimo de 1.5 segundo.
  - Ex.: `144` → 4.5s, `14159` → 7.5s, `1307674368000` → 19.5s.
  - Ao errar ou esgotar o tempo, somente a resposta correta é exibida no centro da tela por 5 segundos, sem cronômetro apressando.
- **Números Primos (Em Ordem Sequencial: `x -->`)**:
  - A pergunta exibe o primo atual seguido de seta (`2 -->`, `3 -->`, `5 -->`, `7 -->` ...) e você digita o próximo primo.
  - Continua infinitamente até errar, registrando seu recorde de sequência.
- **Dígitos de Pi (Em Ordem Sequencial: `3,14159 -->`)**:
  - Exibe o **último bloco** digitado e pede o próximo bloco de **3 dígitos**.
  - A tela começa em `3,` e depois mostra `3,141`, `...592`, `...653`, `...589`... — o `...` indica que já existe histórico antes do bloco atual.
  - Você digita apenas os próximos 3 dígitos (`141` → `592` → `653` → `589` → ...).
  - Continua infinitamente até errar, registrando seu recorde de blocos.
  - Os dígitos são calculados com o algoritmo de Machin usando `BigInt` (precisão exata) e ficam em cache em memória, que é expandido sob demanda conforme a sequência avança.
- **Todos os Outros Módulos em Modo Aleatório**:
  - **Tabuada (1×1 até 12×12)**: Fases de cada número de 1 a 12 e Desafio Completo, com todas as multiplicações sorteadas sem repetição.
  - **Fatoriais (1! até 9!)**: Todos os 9 fatoriais até 362880 em ordem aleatória.
  - **Quadrados Perfeitos (1² até 32²)**: Todos os 32 quadrados até 1024 em ordem aleatória.
  - **Cubos Perfeitos (1³ até 16³)**: Todos os 16 cubos até 4096 em ordem aleatória.
  - **Potências**:
    - Potências de 2 ($2^1$ até $2^{16} = 65536$).
    - Potências de 3 ($3^1$ até $3^9 = 19683$).
    - Potências de 5 ($5^1$ até $5^5 = 3125$).
    - Potências de 7 ($7^1$ até $7^7 = 823543$).
    - Potências de 13 ($13^1$ até $13^5 = 371293$).
- **Precisão de 100%**:
  - Para concluir qualquer fase aleatória, é necessário acertar 100% das questões.

## Ordem dos Módulos

`Tabuada` → `Primos` → `π` → `Fatoriais` → `Quadrados` → `Cubos` → `Potências`

O módulo **Fatoriais** fica imediatamente abaixo do módulo de **π**.

## Fases Personalizadas (Limite Digitável)

Os módulos **Quadrados** e **Cubos** possuem uma fase extra chamada **"Personalizado (defina o limite)"**.

- O campo **Limite** aparece **somente** nessa fase; nas demais fases ele fica oculto.
- A sequência sempre começa em `1` (1², 1³) e segue até o limite digitado.
- O valor digitado é validado automaticamente e nunca ultrapassa o máximo do módulo:

| Módulo | Limite inicial | Limite máximo |
|---|---|---|
| Quadrados | `1` | `100` (100² = 10000) |
| Cubos | `1` | `100` (100³ = 1000000) |

Os módulos **Fatoriais** e **Potências** não possuem fase personalizada: trabalham apenas com as
fases aleatórias descritas acima.

### Compatibilidade com saves existentes

O progresso é salvo por **id** do módulo (`memomath_progress_<id>`), e não por índice, portanto a
reordenação dos módulos não invalida o progresso de nenhum usuário. Fases removidas deixam de
existir apenas em fases posteriores à última fase válida — o índice salvo é ajustado **em memória**
(sem reescrever o `localStorage`), e índices fora da faixa nunca são gravados.

## Configurações

As constantes de configuração ficam no início do bloco `<script>` em `MemoMath.html`:

| Constante | Valor padrão | Descrição |
|---|---|---|
| `SECONDS_PER_DIGIT` | `1.5` | Segundos concedidos por dígito da resposta. |
| `MIN_RESPONSE_TIME` | `1500` | Tempo mínimo de resposta em ms (teto inferior). |
| `MAX_INPUT_DIGITS` | `20` | Máximo de dígitos aceitos na entrada numérica. |
| `PI_CHUNK_DIGITS` | `3` | Dígitos de π pedidos por questão. |
| `PI_TOTAL_DIGITS` | `1000` | Tamanho inicial do cache de dígitos de π (expande sob demanda). |
| `MAX_SQUARE_BASE` | `100` | Maior base de quadrado (fase personalizada). |
| `MAX_CUBE_BASE` | `100` | Maior base de cubo (fase personalizada). |
| `CORRECTION_TIME` | `5000` | Tempo (ms) com a resposta correta em tela após um erro. |
| `TICK_SOUND_SECONDS` | `3` | Últimos segundos com som de contagem regressiva. |

## Execução

O projeto é estático e offline:

```bash
python3 -m http.server 8000
```

Abra [http://localhost:8000/MemoMath.html](http://localhost:8000/MemoMath.html) no navegador.

### Atalhos de teclado

| Ação | Atalhos |
|---|---|
| Iniciar treino | `F` ou `Enter` |
| Digitar resposta | Teclas `0` a `9` |
| Enviar resposta | Tecla `Enter` (ou auto-avanço ao acertar) |
| Continuar após correção | (desabilitado — tela fixa de 5s) |
| Apagar dígito | Tecla `Backspace` |
| Sair da fase | `Esc` |

## Licença

MIT.
