# MemoMath - Memorização Matemática

Aplicativo minimalista para treinar a memorização matemática em alta velocidade com resposta em até **2 segundos** por questão.

Inspirado na arquitetura e simplicidade do [AbsolutePitch](https://github.com/BielXYZ/AbsolutePitch).

## Modos e Mecânicas

- **Timer de 2 Segundos**:
  - Responda cada questão em até 2 segundos.
  - Ao errar ou esgotar o tempo, somente a resposta correta é exibida no centro da tela por 10 segundos, sem cronômetro apressando.
- **Números Primos (Em Ordem Sequencial: `x -->`)**:
  - Único módulo que se mantém em ordem contínua.
  - A pergunta exibe o primo atual seguido de seta (`2 -->`, `3 -->`, `5 -->`, `7 -->` ...) e você digita o próximo primo.
  - Continua infinitamente até errar, registrando seu recorde de sequência.
- **Todos os Outros Módulos em Modo Aleatório**:
  - **Tabuada (1×1 até 12×12)**: Fases de cada número de 1 a 12 e Desafio Completo, com todas as multiplicações sorteadas sem repetição.
  - **Quadrados Perfeitos (1² até 32²)**: Todos os 32 quadrados até 1024 em ordem aleatória.
  - **Cubos Perfeitos (1³ até 16³)**: Todos os 16 cubos até 4096 em ordem aleatória.
  - **Fatoriais (1! até 9!)**: Todos os 9 fatoriais até 362880 em ordem aleatória.
  - **Potências**:
    - Potências de 2 ($2^1$ até $2^{16} = 65536$).
    - Potências de 3 ($3^1$ até $3^9 = 19683$).
    - Potências de 5 ($5^1$ até $5^5 = 3125$).
    - Potências de 7 ($7^1$ até $7^7 = 823543$).
    - Potências de 13 ($13^1$ até $13^5 = 371293$).
- **Precisão de 100%**:
  - Para concluir qualquer fase aleatória, é necessário acertar 100% das questões.

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
| Continuar após correção | `Espaço`, `Enter` ou clique |
| Apagar dígito | Tecla `Backspace` |
| Sair da fase | `Esc` |

## Licença

MIT.
