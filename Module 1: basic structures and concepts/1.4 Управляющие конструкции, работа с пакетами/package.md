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

#### Пример 1

    ifelse(runif(8) > 0.5 ,"Орел","Решка")

Результат :
    
    [1] "Орел"  "Орел"  "Орел"  "Решка" "Орел"  "Решка" "Орел"  "Решка"
    
#### Пример 2
    
    x <- runif(8)
    ifelse(x > 2/3 ,"Камень",
        ifelse(x > 1/3, "Ножницы","Бумага"))
Результат :
    [1] "Камень"  "Ножницы" "Камень"  "Камень"  "Ножницы" "Камень"  "Камень"  "Бумага" 
## Множественный выбор switch
1  аргумент строка 
Пример :

    switch("factorial",
        sum = 5 + 5,
        product = 5 * 5,
        factorial = factorial(5),
        0)
 Результат:
        
        [1] 120
## Циклы repeat
    
    i <- 0
    repeat {
        i <- i + runif(1)
        print(i)
        if (i > 5) break
    }
## Циклы while
    
    i <- 2^14
    while (i > 1000){
        i <- i / 2
        print(i)
    }
## Циклы for

Пример 1:
    
    for (i in 2:8){
        if(i %% 2 == 0) print(i)
    }
Пример 2:

    for (i in letters){
        if (i == "b") next
        if (i == "d") break
        print(i)
    }

    k <- 0
    for (i in x)
    {
        if (i >= -0.2 && i <= 0.3)
        {
            k <- k + 1
        }
    }

## for против векторизации 
К каждому элементу применяем
    
    v <- 1:1e5
    system.time({
        x <- 0
        for (i in v) x[i] <- sqrt(v[i])        
    })

Сразу к вектору :

    v <- 1:1e5
    system.time({
       y <- sqrt(v)        
    })
