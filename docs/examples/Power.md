```
func pow(base: int, exponent: int) -> int
start
    let result = 1;
    let i = 0;
    if exponent < 0
    start
        show "Отрицательная степень не поддерживается";
        return 0;
    end
    while i < exponent
    start
        result = result * base;
        i = i + 1;
    end
    return result;
end

start
    let base = 2;
    let exp = 10;
    let result = pow(base, exp);
    show base;
    show " в степени ";
    show exp;
    show " равно:";
    show result;
end
```