
## [Back](https://github.com/ifanzilka/Statistic_for_R/blob/main/Module%201:%20basic%20structures%20and%20concepts/readme.md)

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
