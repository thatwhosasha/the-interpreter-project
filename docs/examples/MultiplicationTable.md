```
namespace MultiplicationTable;

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
            if product == 1 { line = line + "1 "; }
            elif product == 2 { line = line + "2 "; }
            elif product == 3 { line = line + "3 "; }
            elif product == 4 { line = line + "4 "; }
            elif product == 5 { line = line + "5 "; }
            elif product == 6 { line = line + "6 "; }
            elif product == 7 { line = line + "7 "; }
            elif product == 8 { line = line + "8 "; }
            elif product == 9 { line = line + "9 "; }
            elif product == 10 { line = line + "10 "; }
            elif product == 12 { line = line + "12 "; }
            elif product == 15 { line = line + "15 "; }
            elif product == 16 { line = line + "16 "; }
            elif product == 20 { line = line + "20 "; }
            elif product == 25 { line = line + "25 "; }
            else { line = line + "? "; }
            j = j + 1;
        end
        show line;
        i = i + 1;
    end
end
```