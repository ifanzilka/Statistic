
## [Back](https://github.com/ifanzilka/Statistic_for_R/blob/main/Module%201:%20basic%20structures%20and%20concepts/readme.md)

# Оглавление

## Fizz - buzz

    # fizz-buzz, imperative style
    y <- vector(mode = "character", length = 100)
    y <- character(100)
    for (i in 1:100) {
      if (i %% 15 == 0) {
        y[i] <- "fizz buzz"
      } else if (i %% 3 == 0) {
        y[i] <- "fizz"
      } else if (i %% 5 == 0) {
        y[i] <- "buzz"
      } else {
        y[i] <- i
      }
    }
    y
2 Способ :
    
    # fizz-buzz, vector-oriented style
    x <- 1:100
    z <- 1:100
    x %% 5
    x %% 5 == 0
    z[x %% 5 == 0]
    z[x %% 5 == 0] <- "buzz"
    z[x %% 3 == 0] <- "fizz"
    z[x %% 15 == 0] <- "fizz buzz"
    z
    all(y == z)
## Прогрессия 

    # Geometric progression
    x <- 2 ^ (0:10)
    x
    log2(x)
    
## Рандом   
Выбираем 50 чисел из вектора (1:100)

    # Some randomness
    set.seed(42)
    x <- sample(1:100, 50)
Теперь найдем два соседних числа, отличающихся на макс. велечину
    
    # Neigbors with greatest diff
    x[-1]
    x[-length(x)]
    x[-1] - x[-length(x)]
    k <- which.max(abs(x[-1] - x[-length(x)]))
    x[c(k, k + 1)]
    
 Выборка с повторением :
 
    # Multiple min/max
    x <- sample(1:100, 50, replace = TRUE)
    min(x)
    which.min(x)
    which(x == min(x))
