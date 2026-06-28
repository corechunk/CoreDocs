# 📜 Extended Backus-Naur Form (EBNF) Formalism

## 1. Context-Free Grammars
A formal grammar specifies valid syntax sequences using production rules.

## 2. EBNF Syntax Rules
- `::=` Production assignment
- `|` Alternation (OR)
- `[ ... ]` Optional element (0 or 1)
- `{ ... }` Repetition (0 or more)
- `"..."` Terminal symbol

```ebnf
Expression ::= Term { ("+" | "-") Term } ;
Term       ::= Factor { ("*" | "/") Factor } ;
Factor     ::= Identifier | Literal | "(" Expression ")" ;
```
