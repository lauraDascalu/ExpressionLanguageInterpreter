# Expression Language Interpreter in Haskell

This project implements a simple expression language that supports integer and boolean values, along with basic arithmetic, comparison, and logical operations.
It showcases different approaches to evaluation, typechecking, and simplification of expressions.

## Syntax

The language includes:
- Integer values 
- Boolean values
- Arithmetic expressions: addition (Plus) and multiplication (Mult)
- Comparison expressions (LessThan)
- Logical expressions: boolean OR (Or)

The arithmetic expressions are constructed as Abstract Syntax Trees using the Haskell data type feature. 

## Semantics

### Evaluation
Expressions can be evaluated to produce a result. Since expressions may combine different types or contain errors, evaluation handles these cases carefully:
- imple evaluator: Returns either an integer or boolean result wrapped in a safe container that accounts for possible type errors or invalid expressions.
- Well-typed evaluator: Assumes expressions have been verified as well-formed, enabling a simpler evaluation that does not need error handling.
- GADT evaluator: Uses Generalized Algebraic Data Types (GADTs) to enforce type correctness at the syntax tree level. This guarantees that only valid expressions can be constructed, making evaluation straightforward and type-safe.

### Typechecking
Before evaluation, expressions are checked to confirm their types are consistent:
- Arithmetic operations require integer operands.
- Logical operations require boolean operands.
- Comparison operations require integers but produce boolean results.
If typechecking fails, the expression is considered ill-typed and cannot be evaluated with the well-typed evaluator.

### Simplification
The interpreter includes a simplification step that applies basic rewrite rules to reduce expressions before evaluation, such as:
- Multiplying by zero simplifies to zero immediately.
- Other recursive simplifications apply until the expression can no longer be reduced.
This process improves efficiency by minimizing unnecessary computations during evaluation.
