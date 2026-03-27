# Синтаксис языка Astra

Этот документ описывает синтаксис языка Astra, включая:
* структуру программы
* объявления
* операторы
* выражения
* приоритет и ассоциативность операторов
* полную грамматику в ISO EBNF

Astra — императивный язык программирования со строгой блочной структурой и явными объявлениями.

## 1. Операторы

Описание операторов

| Написание | Семантика                         | Особенности                  |
|-----------|-----------------------------------|------------------------------|
| \+        | Сложение чисел                    | Левая ассоциативность        |
| \-        | Вычитание чисел или унарный минус | Левая ассоциативность        |
| \*        | Умножение чисел                   | Левая ассоциативность        |
| \/        | Деление чисел                     | Левая ассоциативность        |
| ==        | Равно                             | Нет ассоциативности          |
| !=        | Не равно                          | Нет ассоциативности          |
| \>        | Больше                            | Нет ассоциативности          |
| \<        | Меньше                            | Нет ассоциативности          |
| \>\=      | Больше или равно                  | Нет ассоциативности          |
| \<\=      | Меньше или равно                  | Нет ассоциативности          |
| &&        | Логическое «И»                    | Левая ассоциативность        |
| \|\|      | Логическое «ИЛИ»                  | Левая ассоциативность        |
| =         | Присваивание                      | Правая ассоциативность       |
| !         | Логическое "НЕ"                   | Правая ассоциативность       |

Приоритеты операторов (в порядке убывания приоритета):

1. Группировки, вызов функций : `()`, `[]`
2. Унарные операторы: `-`, `!`
3. Умножение и деление: `*`, `/`
4. Плюс и минус: `+`, `-`
5. Операторы сравнения: `<`, `>`, `<=`, `>=`
6. Операторы равенства: `==` , `!=`
7. Логическое "И": `&&`
8. Логическое "ИЛИ": `||`
9. Присаивание: `=`

## 2. Общая структура программы

Программа состоит из:
1. Объявлений переменных, констант и функций (в любом порядке)
2. Исполняемого блока start ... end, который является точкой входа

Пример:

```Astra

let x = 10;

func add(a: int, b: int) -> int
start
    return a + b;
end

start
    show add(x, 5);
end
```

## 3. Объявление переменной

Объявление переменной выполняется с помощью ключевого слова `let`.

Правила:

* переменная изменяема
* переменная должна быть инициализирована при объявлении
* тип переменной определяется из выражения (вывод типа)
* повторное объявление переменной с тем же именем в одной области видимости запрещено

Примеры:

```Astra
let x = 10;
let name = "Astra";
let result = a + b;
```

## 4. Объявление константы

Объявление константы выполняется с помощью ключевого слова `const`.

Правила:

* создаёт неизменяемую переменную
* значение должно быть задано при объявлении
* изменение константы после объявления запрещено
* тип определяется автоматически

Пример:

```Astra
const PI = 3.14;
const MAX = 100;
```

## 5. Объявление функции

Функция объявляется с помощью ключевого слова `func`.

Правила:
* объявляет новую функцию
* функция имеет имя, параметры и возвращаемый тип
* тело функции представляет собой блок
* функция может возвращать значение с помощью return
* функции могут вызывать другие функции, включая самих себя (рекурсия разрешена)

Пример:

```Astra
func add(a: int, b: int) -> int
start
    return a + b;
end
```

Функция без параметров:

```Astra
func hello() -> void
start
    show "Hello";
end
```
## 6. Условный оператор
Условный оператор `if` позволяет выполнить один из блоков кода в зависимости от условия.

Правила:
* условие — выражение, которое приводится к логическому значению (`true` или `false`)
* если условие истинно, выполняется блок после условия
* необязательная ветка `else` выполняется, если условие ложно
* допускается каскадирование `else if` с помощью вложенных `if` в ветке `else` (синтаксически отдельной конструкции `else if` нет, но можно использовать вложенные `if`)

Примеры:

```Astra
if x > 0
start
    show "Положительное";
end

if x > 0
start
    show "Положительное";
end
else
start
    show "Неположительное";
end
```

## 8. Цикл while

Цикл `while` выполняет блок кода многократно, пока условие истинно.

Правила:

* перед каждой итерацией вычисляется условие
* если условие истинно, выполняется тело цикла
* если условие ложно, выполнение цикла прекращается
* тело цикла может быть пустым

Пример:

```Astra
let i = 0;
while i < 5
start
    show i;
    i = i + 1;
end
```

## 9. Операторы break и continue

Внутри цикла `while` можно использовать операторы `break` и `continue` для управления выполнением.

Правила:

* `break` — немедленно завершает выполнение текущего цикла; управление передаётся на инструкцию, следующую за циклом
* `continue` — завершает текущую итерацию цикла и переходит к проверке условия для следующей итерации
* использование вне цикла запрещено (семантическая ошибка)

Примеры:

```Astra
let i = 0;
while i < 10
start
    i = i + 1;
    if i == 3
    start
        continue;  // пропустить вывод для i = 3
    end
    if i == 8
    start
        break;     // завершить цикл при i = 8
    end
    show i;
end
```

## 10. Индексация 

Индексация позволяет получить элемент коллекции по индексу. Синтаксически это выражение, за которым следует индекс в квадратных скобках.

Правила:

* индексируемое выражение должно обозначать коллекцию (например: строку)
* индекс — выражение, которое должно приводиться к целому числу
* результат индексации может использоваться как значение

Пример:

```Astra
let str = "Astra";
let first = str[0];      // "A"
let third = str[2];      // "t"
let last = str[len(str)-1]; // "a"
```

## Грамматика в нотации  ISO EBNF:

```ebnf

program = { declaration }, block ;

declaration =
      variable_declaration
    | constant_declaration
    | function_declaration ;

variable_declaration =
    "let",
    identifier,
    "=",
    expression,
    ";" ;

constant_declaration =
    "const",
    identifier,
    "=",
    expression,
    ";" ;

function_declaration = "func",
    identifier,
    "(",
    [ parameter_list ],
    ")",
    [ "->",
    type ],
    block ;

parameter_list =
    parameter,
    { ",", parameter } ;

parameter =
    identifier,
    ":",
    type ;

type =
    identifier ;

block =
    "start",
    { statement },
    "end" ;

statement =
      variable_declaration
    | constant_declaration
    | return_statement
    | show_statement
    | if_statement
    | while_statement
    | break_statement
    | continue_statement
    | expression_statement
    | block ;

return_statement =
    "return",
    [ expression ],
    ";" ;

show_statement =
    "show",
    expression,
    ";" ;

if_statement =
    "if",
    expression,
    block,
    [ "else", block ] ;

while_statement =
    "while",
    expression,
    block ;

break_statement =
    "break",
    ";" ;

continue_statement =
    "continue",
    ";" ;

expression_statement =
    expression,
    ";" ;

expression =
    assignment_expression ;

assignment_expression =
      logical_or_expression
    | identifier,
      "=",
      assignment_expression ;

logical_or_expression =
    logical_and_expression,
    { "||", logical_and_expression } ;

logical_and_expression =
    equality_expression,
    { "&&", equality_expression } ;

equality_expression =
    relational_expression,
    { ( "==" | "!=" ), relational_expression } ;

relational_expression =
    additive_expression,
    { ( "<" | ">" | "<=" | ">=" ), additive_expression } ;

additive_expression =
    multiplicative_expression,
    { ( "+" | "-" ), multiplicative_expression } ;

multiplicative_expression =
    unary_expression,
    { ( "*" | "/" ), unary_expression } ;

unary_expression =
      primary_expression
    | "-", unary_expression
    | "!", unary_expression ;

function_call =
    identifier,
    "(",
    [ argument_list ],
    ")" ;

argument_list =
    expression,
    { ",", expression } ;

primary_expression =
 literal
| qualified_identifier 
| function_call 
| "(", expression, ")" ;

postfix_expression =
 primary_expression, { "[", expression, "]" } ;

unary_expression = 
postfix_expression 
| "-", unary_expression 
| "!", unary_expression ;

literal =
      integer_literal
    | float_literal
    | string_literal
    | "true"
    | "false" ;

```

