 ## [Back](https://github.com/ifanzilka/Statistic_for_R/blob/main/Module%203:%20advanced%20programming/3advanced_prjgramming.md)


# Функция как объект

Функция в R – объект “первого класса”, её можно:

Использовать как обычный объект


    str(c(mean, max))
#
    ## List of 2
    ##  $ :function (x, ...)  
    ##  $ :function (..., na.rm = FALSE)
#
Храним функции в list


    fun_list <- c(mean, max)
    sapply(fun_list, function(f) f(1:100))
#
    ## [1]  50.5 100.0



## Функция как аргумент

Указывать в качестве аргумента
И вызываем)


    apply_f <- function(f, x) f(x)
    sapply(fun_list, apply_f, x = 1:100)
#
    ## [1]  50.5 100.0

… при этом анонимная функция тоже подойдёт
(Которую тут же определили)
  
    apply_f(function(x) sum(x^2), 1:10)
#
    ## [1] 385

## Функция как return value()

Возвращаем функцию

Использовать как возвращаемое значение

     square <- function() function(x) x^2
     square()
#
     ## function(x) x^2
     ## <environment: 0x1f46498>
#
Вызываем
 
     square()(5)
#
     ## [1] 25

Бинарные операторы

Оператор x %in% y: есть ли вхождения элементов x в y?

1:5 %in% c(1, 2, 5)

## [1]  TRUE  TRUE FALSE FALSE  TRUE

"%nin%" <- function(x, y) !(x %in% y)
1:5 %nin% c(1, 2, 5)

## [1] FALSE FALSE  TRUE  TRUE FALSE

Глоссарий

?"function"

Source code for functions, ?methods

Argument matching, ellipsis (?"...")
Использовать как обычный объект str(c(mean, max)) ## List of 2 ## $ :function (x, ...) ## $ :function (..., na.rm = FALSE) fun_list <- c(mean, max) sapply(fun_list, function(f) f(1:100)) ## [1] 50.5 100.0 
