```
func sum_digits(n: int) -> int
start
    let num = n;
    if num < 0
    start
        num = -num;
    end
    let sum = 0;
    while num > 0
    start
        let digit = num % 10;
        sum = sum + digit;
        num = num / 10;
    end
    return sum;
end

start
    let number = 12345;
    let result = sum_digits(number);
    show "Сумма цифр числа ";
    show number;
    show " равна:";
    show result;
end
```