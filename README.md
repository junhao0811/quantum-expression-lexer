# Quantum Expression Lexer

Lexical analysis and formal-language theory for **quantum-circuit expressions**: expressions built from quantum gates such as `I`, `H`, `X`, `Y`, `Z`, `CNOT` and `TOF`, combined with products (`*`) and tensor products (`(x)`).

## What's inside

| Path | What it is |
|---|---|
| `lexers/quantum_lexer.l` | A **flex** lexer that recognises quantum gates, operators and brackets, prints each token and lexeme, and rejects invalid characters |
| `lexers/quantum_lexer_tokens.l` | The same lexer adapted to **return tokens** to a yacc/bison parser. It's a parser front end, so it can't run on its own without a matching grammar |
| `lexers/support/` | Supporting files the lexer builds against: a header and a starter yacc grammar for simple arithmetic expressions (provided) |
| `turing-machine/machine.tm` | A **Turing machine** design, built in the Tuatara Turing machine simulator |
| `proofs/quantum_expression_grammar.pdf` | A **context-free grammar** that generates valid quantum-circuit expressions |
| `proofs/pumping_lemma_proof.pdf` | A proof by contradiction using the **pumping lemma** and Kleene's theorem that a "universal regular expression" cannot exist |

## Build and run the lexer

Requires `flex`, `bison`/`yacc`, `gcc` and the flex library (on Ubuntu: `sudo apt install flex bison libfl-dev`).

```bash
cd lexers
make
echo "(H(x)I)*CNOT" | ./quantum_lexer
```

Output:
```
Token and Lexeme: (
Token: H;  Lexeme: H
Token: KRONECKERPROD;  Lexeme: (x)
Token: I;  Lexeme: I
Token and Lexeme: )
Token and Lexeme: *
Token: CNOT;  Lexeme: CNOT
```

`make clean` removes the build files.
