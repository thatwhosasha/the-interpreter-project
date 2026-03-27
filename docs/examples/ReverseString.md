```
func reverse(str: string) -> string
start
    let length = len(str);
    let result = "";
    let i = length - 1;
    while i >= 0
    start
        result = result + str[i];
        i = i - 1;
    end
    return result;
end

start
    let input = "Hello world!";
    let reversed = reverse(input);
    show "Исходная строка: ";
    show input;
    show "Перевёрнутая строка: ";
    show reversed;
end
```