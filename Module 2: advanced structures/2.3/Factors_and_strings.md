## [Back](https://github.com/ifanzilka/Statistic_for_R/blob/main/Module%202:%20advanced%20structures/module2.md)


## Строки

Строка (string) – это элемент вектора типа character

Большинство функций, оперирующих на строках, векторизованы

    s <- c("Терпение и труд всё перетрут", 
           "Кончил дело — гуляй смело", 
           "Без труда не вытащишь и рыбку из пруда",
           'Работа не волк, в лес не убежит')

Как правило, для строк используют двойные кавычки

Одинарные кавычки тоже можно использовать: 'Операция "Ы"'

    
    ## [1] "Операция \"Ы\""


## Функции paste/paste0

Выполняют конкатенацию строковых векторов с учётом правил переписывания

Аргумент sep – разделитель между элементами (для paste по умолчанию пробел, для paste0 – пустая строка)

Аргумент collapse – “схлопывает” вектор в одну строку

    paste(c("углекислый", "веселящий"), "газ")
#

    ## [1] "углекислый газ" "веселящий газ"
OR
    
    paste(c("углекислый", "веселящий"), "газ", sep = "_")
#
    ## [1] "углекислый_газ" "веселящий_газ"
OR

    paste(c("углекислый", "веселящий"), "газ", collapse = ", а также ")
#
    ## [1] "углекислый газ, а также веселящий газ"




## Функция strsplit

Выполняет разбиение строкового вектора

Результат – список!

    strsplit(s, " и ", fixed = TRUE)
#
    ## [[1]]
    ## [1] "Терпение"          "труд всё перетрут"
    ## 
    ## [[2]]
    ## [1] "Кончил дело — гуляй смело"
    ## 
    ## [[3]]
    ## [1] "Без труда не вытащишь" "рыбку из пруда"       
    ## 
    ## [[4]]
    ## [1] "Работа не волк, в лес не убежит"
    


## Функция strsplit


Если не указывать аргумент fixed (по умолчанию FALSE), то строка, по которой проводится разбиение, будет рассматриваться как регулярное выражение:

В данном примере разделение по всем знакам препинания

    strsplit(s, "[[:punct:]]")
#
    ## [[1]]
    ## [1] "Терпение и труд всё перетрут"
    ## 
    ## [[2]]
    ## [1] "Кончил дело " " гуляй смело"
    ## 
    ## [[3]]
    ## [1] "Без труда не вытащишь и рыбку из пруда"
    ## 
    ## [[4]]
    ## [1] "Работа не волк"   " в лес не убежит"



## Регулярные выражения

“Метаязык” поиска и манипуляции подстрок
 
 Образец для поиска может включать обычные символы и т.н. wildcards

grep скажет в какие строках есть слово

    grep("труд", s)
#
    ## [1] 1 3
OR
    
    grepl("труд", s)
#
    ## [1]  TRUE FALSE  TRUE FALSE
OR (Замена) Всел слова из 4-5 букв
    
    gsub("\\b[[:alpha:]]{4,5}\\b", "####",  s)
#
    ## [1] "Терпение и #### всё перетрут"        "Кончил #### — #### ####"            
    ## [3] "Без #### не вытащишь и #### из ####" "Работа не ####, в лес не убежит"



## Пакет stringr

    #install.packages("stringr")
    library(stringr)

Пакет содержит множество функций для работы со строками. Эти функции векторизованы и являются consistent:

поиск по шаблону

    str_extract(s, "н.")
#
    ## [1] "ни" "нч" "не" "не"
OR (Поиск по шаблону и замнена)
    
    str_replace(s, "[иа]", "?")
#
    ## [1] "Терпен?е и труд всё перетрут"           "Конч?л дело — гуляй смело"             
    ## [3] "Без труд? не вытащишь и рыбку из пруда" "Р?бота не волк, в лес не убежит"




## Пакет stringr

Ко многим функциям можно добавить _all, чтобы искать все вхождения, а не первое:

    str_extract_all(s, "н.")

    ## [[1]]
    ## [1] "ни"
    ## 
    ## [[2]]
    ## [1] "нч"
    ## 
    ## [[3]]
    ## [1] "не"
    ## 
    ## [[4]]
    ## [1] "не" "не"
#
    str_replace_all(s, "[иае]", "?")
#
    ## [1] "Т?рп?н?? ? труд всё п?р?трут"           "Конч?л д?ло — гуляй см?ло"             
    ## [3] "Б?з труд? н? выт?щ?шь ? рыбку ?з пруд?" "Р?бот? н? волк, в л?с н? уб?ж?т"



## Функции tolower/toupper

Манипулирование регистром:

    tolower(month.name)
#
    ##  [1] "january"   "february"  "march"     "april"     "may"       "june"      "july"      "august"   
    ##  [9] "september" "october"   "november"  "december"
OR

    toupper(month.abb)
#
    ##  [1] "JAN" "FEB" "MAR" "APR" "MAY" "JUN" "JUL" "AUG" "SEP" "OCT" "NOV" "DEC"




## Задача

В память о бедном Йорике я подготовил небольшую тираду и обработал её средствами stringr. Вы не могли бы дать мне небольшой лингвистический обзор этого предложения? Выполните следующий код, чтобы начать работу с фразой в удобной форме:

library(stringr)

hamlet <- "To be, or not to be: that is the question:
Whether 'tis nobler in the mind to suffer
The slings and arrows of outrageous fortune,
Or to take arms against a sea of troubles,
And by opposing end them?"

hamlet <- str_replace_all(hamlet, "[:punct:]", "")
hamlet <- tolower(unlist(str_split(hamlet, "[:space:]")))
 
P.S. Обратите внимание, как я препарировал предложение регулярными выражениями, чтобы вам было удобно. Все ли шаги понятны?
P.P.S. При копировании кода сверху пропадают пробелы. Либо добавьте их обратно в текстовом редакторе, либо сразу возьмите конечный результат:

hamlet <- c("to", "be", "or", "not", "to", "be", "that", "is", "the", "question", 
"whether", "tis", "nobler", "in", "the", "mind", "to", "suffer", 
"the", "slings", "and", "arrows", "of", "outrageous", "fortune", 
"or", "to", "take", "arms", "against", "a", "sea", "of", "troubles", 
"and", "by", "opposing", "end", "them")

Решение.

    sum(hamlet=="to")
    sum(grepl("[fqw]", hamlet))
    sum(grepl("b.", hamlet))
    sum(nchar(hamlet)==7)

## Пути к файлам

У сессии R есть понятие рабочей директории:

    getwd() 
#
    ## [1] "/home/tonytonov/Dropbox/AdvancedR/Main3"
OR

    head(list.files())
#
    ## [1] "0-intro.html"   "0-intro.Rmd"    "1-control.html" "1-control.Rmd"  "1-vectors.html" "1-vectors.R"

OR
    
    list.dirs("..", recursive = FALSE)
#
    ## [1] "../Main"           "../Main2"          "../Main3"          "../stepic-helpers"

Смена рабочей директории – функция setwd.

При создании нового проекта в RStudio рабочим каталогом становится тот, в котором расположен файл проекта, .Rproj

Под Windows разделителями каталогов могут быть либо /, либо \\



## Форматирование чисел

    c(pi, exp(pi))
#

    ## [1]  3.141593 23.140693
#
Три Цифры 

    formatC(c(pi, exp(pi)), digits = 3)
#

    ## [1] "3.14" "23.1"
#
    formatC(c(pi, exp(pi)), digits = 3, format = "e")
#

    ## [1] "3.142e+00" "2.314e+01"



## Функция cat

Обычно для вывода неявно используется функция print
Функция cat печатает объекты “как есть”

    print('Операция "Ы"'); 
    cat('Операция "Ы"')
#

    ## [1] "Операция \"Ы\""
    ## Операция "Ы"
#
    print("Трус\tБалбес\nБывалый"); 
    cat("Трус\tБалбес\nБывалый")
#

    ## [1] "Трус\tБалбес\nБывалый"\
    ## Трус Балбес
    ## Бывалый



## Факторы

В статистике существует деление на количественные и качественные переменные

Для качественных переменных есть factor

Фактор – это гибрид целочисленного (integer) и строкового (character) вектора

    set.seed(1337)
    f <- factor(sample(LETTERS, 30, replace = TRUE))
    f
#
    ##  [1] O O B L J I Y H G D Z Z V F Z A Z Y I G W S B D O Z Y X M Z
    ## Levels: A B D F G H I J L M O S V W X Y Z




## Уровни фактора

    as.numeric(f)
#
    ##  [1] 11 11  2  9  8  7 16  6  5  3 17 17 13  4 17  1 17 16  7  5 14 12  2  3 11 17 16 15 10 17
OR

    as.character(f)
#

    ##  [1] "O" "O" "B" "L" "J" "I" "Y" "H" "G" "D" "Z" "Z" "V" "F" "Z" "A" "Z" "Y" "I" "G" "W" "S" "B" "D" "O" "Z"
    ## [27] "Y" "X" "M" "Z"
OR

    levels(f)
#
    ##  [1] "A" "B" "D" "F" "G" "H" "I" "J" "L" "M" "O" "S" "V" "W" "X" "Y" "Z"
OR

    nlevels(f)
OR
    
    ## [1] 17



## Уровни фактора

Индексирование определено для == и !=:

Замена  A на  Z

    f[f == "A"] <- "Z"
    f
#
    ##  [1] O O B L J I Y H G D Z Z V F Z Z Z Y I G W S B D O Z Y X M Z
    ## Levels: A B D F G H I J L M O S V W X Y Z
OR



    (f <- droplevels(f))
#
    ##  [1] O O B L J I Y H G D Z Z V F Z Z Z Y I G W S B D O Z Y X M Z
    ## Levels: B D F G H I J L M O S V W X Y Z



## Преобразование уровней фактора

Применить ко всем нижний регистр

    levels(f) <- tolower(levels(f))
    #levels(f) <- letters[LETTERS %in% levels(f)]
    f
#

    ##  [1] o o b l j i y h g d z z v f z z z y i g w s b d o z y x m z
    ## Levels: b d f g h i j l m o s v w x y z
OR

    levels(f)[1] <- "bbb"
    f
#

    ##  [1] o   o   bbb l   j   i   y   h   g   d   z   z   v   f   z   z   z   y   i   g   w   s   bbb d   o   z  
    ## [27] y   x   m   z  
    ## Levels: bbb d f g h i j l m o s v w x y z


## Упорядоченные факторы

  Если категории качественной переменной упорядочены, то это порядковая переменная
  
  Упорядоченный фактор: функция ordered либо аргумент ordered = TRUE для factor



    temp <- c("freezing cold", "cold", "comfortable", "hot", "burning hot")
    ft <- ordered(sample(temp, 14, replace = TRUE), temp)
    ft
#

    ##  [1] burning hot   freezing cold hot           cold          hot           hot           burning hot  
    ##  [8] hot           cold          cold          hot           burning hot   comfortable   hot          
    ## Levels: freezing cold < cold < comfortable < hot < burning hot

OR

    ft[ft >= "hot"]
#

    ## [1] burning hot hot         hot         hot         burning hot hot         hot         burning hot
    ## [9] hot        
    ## Levels: freezing cold < cold < comfortable < hot < burning hot


## Преобразование количественной переменной в качественную

cut разбивает numeric вектор на интервалы

table производит подсчёт количества элементов для каждого уровня фактора

    cut(rnorm(10), -5:5)
#

    ##  [1] (-1,0]  (-1,0]  (-2,-1] (1,2]   (0,1]   (0,1]   (-2,-1] (0,1]   (1,2]   (1,2]  
    ## Levels: (-5,-4] (-4,-3] (-3,-2] (-2,-1] (-1,0] (0,1] (1,2] (2,3] (3,4] (4,5]

OR

    table(cut(rnorm(1000), -5:5))
#
Распределение по интервалам
(Нормальное распределение)

    ## 
    ## (-5,-4] (-4,-3] (-3,-2] (-2,-1]  (-1,0]   (0,1]   (1,2]   (2,3]   (3,4]   (4,5] 
    ##       0       3      27     122     353     322     148      20       5       0



## options

   У сессии R есть набор активных настроек, отвечающих за подсчёт и вывод результатов вычислений
   
   ?options :
        digits – количество знаков при печати чисел
        error – поведение при ошибке
        width – длина строки при печати векторов и матриц
   
   По умолчанию, все строковые переменные становятся факторами, отменить такое поведение можно вызовом options(stringsAsFactors = FALSE)



## tapply

  Факторы чаще всего встречаются как переменные в дата фреймах
  
  Одна из наиболее распространённых задач – подсчёт некоторой статистики по группам

    #?warpbreaks
    str(warpbreaks)
#

    ## 'data.frame':    54 obs. of  3 variables:
    ##  $ breaks : num  26 30 54 25 70 52 51 26 67 18 ...
    ##  $ wool   : Factor w/ 2 levels "A","B": 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ tension: Factor w/ 3 levels "L","M","H": 1 1 1 1 1 1 1 1 1 2 ...
OR
   
    tapply(warpbreaks$breaks, warpbreaks$wool, max)
#

    ##  A  B 
## 70 44



