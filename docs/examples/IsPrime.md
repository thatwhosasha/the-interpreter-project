```
namespace IsPrime;

func is_prime(n: int) -> bool
start
    if n <= 1
    start
        return false;
    end
    let i = 2;
    while i * i <= n
    start
        if (n - (n / i) * i) == 0
        start
            return false;
        end
        i = i + 1;
    end
    return true;
end

start
    let numbers = 17;
    let result = is_prime(numbers);
    show "Число ";
    show numbers;
    if result
    start
        show " является простым";
    end
    else
    start
        show " не является простым";
    end
end
```