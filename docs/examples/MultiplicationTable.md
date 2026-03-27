```
start
    let N = 5;
    let i = 1;
    show "Таблица умножения от 1 до ";
    show N;
    show ":";
    while i <= N
    start
        let j = 1;
        let line = "";
        while j <= N
        start
            let product = i * j;
            line = line + product;
            if j < N
            start
                line = line + " ";
            end
            j = j + 1;
        end
        show line;
        i = i + 1;
    end
end
```