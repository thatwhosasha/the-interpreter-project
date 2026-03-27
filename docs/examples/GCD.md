```
func gcd(a: int, b: int) -> int
start
    while b != 0
    start
        let temp = b;
        b = a % b;
        a = temp;
    end
    return a;
end

start
    let num1 = 48;
    let num2 = 18;
    let result = gcd(num1, num2);
    show "Наибольший общий делитель чисел ";
    show num1;
    show " и ";
    show num2;
    show " равен:";
    show result;
end
```