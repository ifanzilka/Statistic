# [Back](https://github.com/ifanzilka/Statistic_for_R/blob/main/Module%202:%20advanced%20structures/module2.md)

  ## Матрица
Матрица – двумерный массив данных одного типа

По сути, это вектор, уложенный по столбцам (!)

Для создания матрицы можно использовать функцию matrix

    matrix(1:6, nrow = 2, ncol = 3)
 #
    ##      [,1] [,2] [,3]
    ## [1,]    1    3    5
    ## [2,]    2    4    6
