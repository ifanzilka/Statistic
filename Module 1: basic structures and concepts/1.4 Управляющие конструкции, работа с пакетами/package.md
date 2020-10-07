## [Back](https://github.com/ifanzilka/Statistic_for_R/blob/main/Module%201:%20basic%20structures%20and%20concepts/readme.md)

## if и  else
Синатаксис :

    if (<condition>) {<do somthing>} else {<do another thing>}

Здесь condition  логический вектор длины 1.
#### Пример 1:
    if (sqrt(2) > 1.5)
    {
        print("Good")
    }else
    {
        print("Bad")
    }
Результат :
    
    [1] "Bad"
## ifelse
### runif
Для генерации вещественных чисел в диапазоне [min, max] используется функция runif(n, min = 0, max = 1), которая в качестве аргументов принимает:
n — количество генерируемых значений;
min — нижняя граница диапазона; вещественное конечное число;
max — верхняя граница диапазона; вещественное конечное число.
    
    x1 <- runif(1, 5.0, 7.5)
    x1
Результат :    
    
    [1] 6.715697

Cинтаксис ifelse :
    
    ifelse(<логический вектор> , <Условие для TRUE>, <Условие для FALSE>)
