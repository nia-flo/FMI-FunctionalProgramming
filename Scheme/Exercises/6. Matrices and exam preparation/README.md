# Упражнение

- `my-flatten` - представя списък от списъци като един списък с всички елементи
- `sum-of-products ll` - намира сумата от произведенията на всички подсписъци в ll
  - пример: `(sum-of-products '((1 2 3) (4 5) (6)))` -> (6 20 6) -> 32 
- `dimensions m` - връща наредена двойка: броя редове и колони на матрицата m
- `main-diagonal m` - намира главния диагонал на матрицата m
- `second-diagonal m` - намира другия диагонал на матрицата m
- `nth-row m n` - намира n-тия ред на матрицата m
- `nth-column m n` - намира n-тата колона на матрицата m
- `transpose m` - транспонира матрицата m
- `skip-nth-row m n` - маха n-тия ред от матрицата m
- `skip-nth-column m n` - маха n-тата колона от матрицата m
- `sc-multiply m x` - скаларно произведение на матрицата m с числото x
- `multiply a b` - умножава матриците m и n

# Контролно 2019-2020А

## Задача 1. 

- Да се реализира функция `product-digits`, която намира произведението от цифрите на дадено естествено число.
- Нека с {n} означим разликата на n и произведението на цифрите на n. Да се реализира функция `largest-diff`, която намира най-голямата разлика {m} – {n} за m, n ∈ [a; b], където a и b са параметри на функцията.

Пример: 
```
(largest-diff 28 35) → 19  = {30} – {29} = (30 – 0) – (29 – 18))
```

## Задача 2. 

“Метрика” наричаме функция, която приема като параметър списък от числа и връща число като резултат. Да се напише функция `max-metric`, която приема като параметри списък от метрики ml и списък от списъци от числа ll и връща метрика m от ml, за която сумата от стойностите, които m връща над елементите на ll, е максимална в сравнение с останалите метрики от ml.

Примери:
```
(define (prod l) (apply * l))        (define (sum l) (apply + l)) 
(max-metric (list sum prod) '((0 1 2) (3 4 5) (1337 0))) → <sum>
(max-metric (list car sum)  '((1000 -1000) (29 1) (42))) → <car>
```

## Задача 3. 

“Ниво на влагане” на атом в дълбок списък наричаме броя пъти, който трябва да се приложи операцията car за достигане до атома. Да се реализира функция `deep-repeat`, която в подаден дълбок списък заменя всеки атом на ниво на влагане n с n негови повторения.

Пример:
```
(deep-repeat '(1 (2 3) 4 (5 (6)))) → (1 (2 2 3 3) 4 (5 5 (6 6 6)))
```

# Контролно 2021-2022

## Задача 1. 

Едно естествено число наричаме свършено, ако е с 2 по-малко от сумата на всичките си делители по-малки от него.

- Да се реализира функция `done?`, която проверява дали дадено число е свършено.
- Да се реализира функция `sum-almost-done`, която по подадени естествени числа a и b намира сумата на всички числа в интервала [a; b], които са по-близко до свършено число, отколкото до краищата на интервала.

Примери:
```
(done? 20) → #t
(done? 28) → #f

(sum-almost-done 5 24) → 153 ; сумата на числата от 13 до 21
```

## Задача 2.

Разглеждаме стекова машина, която представя паметта си като списък от числа и символи и приема списък от инструкции, които интерпретира по следния начин: - ако поредната инструкция е число или символ, то се добавя на върха на стека - ако поредната инструкция е функция, тя се прилага над всички числа в стека (допуска се, че функцията приема само един параметър), променяйки стойностите им в стека - ако поредната инструкция е наредена двойка от операция (двуместна функция) и число n, то горните две числа на стека се изваждат и обратно на върха на стека се записва резултат от прилагането на операцията над тях. Прилагането се повтаря до изчерпване на стека или достигане до символ, но не повече от n пъти. - всички останали инструкции се игнорират.

Да се реализира функция `run-machine`, която връща като резултат списък, представящ паметта на машината след последователно обработване на всички инструкции. Първоначално машината се инициализира с празен стек.

Примери:
```
(run-machine (list 1 'x 4 'a 9 16 25 sqrt 6))                       → (6 5 4 3 a 2 x 1)
(run-machine (list 1 'x 4 'a 9 16 25 sqrt 6 (cons + 2) (cons * 5))) → (45 a 2 x 1)
```

## Задача 3. 

Казваме, че един списък е подсписък на друг, ако елементите на първия списък се срещат непосредствено последователно във втория. Например, '(2 4) не е подсписък на '(1 2 3 4 5), но '(2 3 4) е. Казваме, че един списък от числа a се мажорира от списъка b, ако двата списъка са с еднаква дължина n и ai ≤ bi за всяко i ∈ [0; n). Списък от списъци ll наричаме мажорен, ако е вярно, че li се мажорира от подсписък на li+1 за всеки два съседни списъка li и li+1 в ll.

Да се реализира функция `is-major?`, която проверява дали даден списък от списъци от числа е мажорен.

Примери:
```
(is-major? '((1 3) (4 2 7) (2 5 4 3 9 12))) → #t
(is-major? '((1 3) (4 2 7) (2 5 3 3 9 12))) → #f
```
