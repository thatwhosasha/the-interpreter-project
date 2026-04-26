# Синтаксис языка Astra

## Операторы

|Приоритет(по возрастанию) | Написание | Семантика | Ассоциативность|
|--------------------------|-----------|-----------|--------|
|    1     | `=`        | присваивание                  | Правая       |
|    2     | `+`, `-`        | Сложение, вычитание                 | Левая        |
|    3     | `*`, `/`       | Умножение, деление                    | Левая       |
|    4     | `-`(унарный)       | Унарный минус                          | Нет          |
|    5     | `[]`     | Индексация                | Левая      |

```EBNF
program = { statement, ";" } ;

type = "int" | "float" | "string" ;

statement =
      variable_declaration
    | constant_definition
    | assignment
    | output_statement
    | compound_statement
    | expression ;

variable_declaration = "let", identifier,
    ( ":" type, [ "=", expression ]
    | "=", expression ) ;

constant_definition = "const", identifier, ":", type, "=", expression ;

assignment = identifier, "=", expression ;

input_statement = "input", identifier ;

output_statement = "show", expression ;

compound_statement = "start", { statement, ";" }, "end" ;

expression = additive_expression ;

additive_expression = multiplicative_expression,
    { ( "+" | "-" ), multiplicative_expression } ;

multiplicative_expression = unary_expression,
    { ( "*" | "/" ), unary_expression } ;

unary_expression = "-", unary_expression
                 | postfix_expression ;

postfix_expression = primary_expression,
    { "[", expression, "]" } ;

primary_expression = identifier
                   | literal
                   | "len", "(", expression, ")"
                   | "(", expression, ")" ;

literal = integer_literal | float_literal | string_literal ;
```