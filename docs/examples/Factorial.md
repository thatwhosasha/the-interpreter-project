```
namespace Factorial;

func factorial(n: int) -> int
start
    if n <= 1
    start
        return 1;
    end
    else
    start
        return n * factorial(n - 1);
    end
end

start
    let n = 7;
    let result = factorial(n);
    show "Факториал числа ";
    show n;
    show " равен:";
    show result;
end
```