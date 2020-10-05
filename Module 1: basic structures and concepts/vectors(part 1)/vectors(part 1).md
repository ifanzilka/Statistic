## [Back](https://github.com/ifanzilka/Statistic_for_R/blob/main/Module%201:%20basic%20structures%20and%20concepts/readme.md)
Векторы в R индексируются с 1, а не с 0!!!

###  Создание вектора :
  
    x <- vector(length = 2)
    x[1] <- 5
    x[2] <- 8
    x
Результат :    
  
    [1] 5 8

Но обычно используют более компактную запись :

    x <- c(5,8,2)
    x
Результат :    

    [1] 5 8 2
