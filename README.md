# Домашнее задание к занятию «SQL. Часть 1»

## Задание 1
### Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

### Решение
### Не совсем правильный вариант решения, С условием сдания вроде сходится, но если подставить другую букву, то он начинает выбивать и названия чрез пробел. 
### Хотелось бы узнать как сделать полностью верное решение
### ![](https://github.com/Berezhok/hw_SQL1/blob/main/img/zad1.png) 
### Вроде сработало,но по факту
### ![](https://github.com/Berezhok/hw_SQL1/blob/main/img/zad1F.png)
###
## Задание 2
### Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года включительно и стоимость которых превышает 10.00.
### Вывел информацию по всем столбцам 
### ![](https://github.com/Berezhok/hw_SQL1/blob/main/img/zad2.png)
###
## Задание 3
### Получите последние пять аренд фильмов.
### Решение
### Если я правильно понял, вывел таблицу аренды, отсортировал по убыванию по дате и взял превые 5 строк.
### ![](https://github.com/Berezhok/hw_SQL1/blob/main/img/zad3.png)
###
## Задание 4
### Одним запросом получите активных покупателей, имена которых Kelly или Willie.

### Сформируйте вывод в результат таким образом:

### все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
### замените буквы 'll' в именах на 'pp'.
### Решение
### ![](https://github.com/Berezhok/hw_SQL1/blob/main/img/zad4.png)
### 


### Дополнительные задания (со звёздочкой*)
### Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

## Задание 5*
### Выведите Email каждого покупателя, разделив значение Email на две отдельных колонки: в первой колонке должно быть значение, указанное до @, во второй — значение, указанное после @.
### Решение
### Вроде получилось. Вывел 20 строк, чтобы не выводить 599.
### ![](https://github.com/Berezhok/hw_SQL1/blob/main/img/zad5.png)

## Задание 6*
### Доработайте запрос из предыдущего задания, скорректируйте значения в новых колонках: первая буква должна быть заглавной, остальные — строчными.
### Не уверен, что это делается так, видимо можно сделать проще, что-то очень замудренное, сам написал и потом с трудом смог разобрать. 
### Конечно можно было доработать чтобы, фамилия после точки была тоже заглавная, но лень уже конечно. 
### Вывел 20 строк
### ![](https://github.com/Berezhok/hw_SQL1/blob/main/img/zad6.png)


### ___________________________________________________________________________________________________


###              Это то как я делал, потому что невозможно .... Путаешься в скобках постоянно

### select concat(left(left(email, position('@' in email)-1), 1), lower(right(left(email, position('@' in email)-1), (char_length(left(email, position('@' in email)-1))-1)))) AS login, concat(upper(left(right(email, char_length(email)-position('@' in email)), 1)), right(right(email, char_length(email)-position('@' in email)), (char_length(right(email, char_length(email)-position('@' in email)))-1))) AS domen from customer limit 3;

### select concat(upper(left(right(email, char_length(email)-position('@' in email)), 1)), right(right(email, char_length(email)-position('@' in email)), (char_length(right(email, char_length(email)-position('@' in email)))-1))) AS domen from customer limit 3; 



### left(email, position('@' in email)-1)  = MARY.SMITH

### left(left(email, position('@' in email)-1), 1) = M

### lower(right(left(email, position('@' in email)-1), (char_length(left(email, position('@' in email)-1))-1))) = ary.smith
###
### right(email, char_length(email)-position('@' in email)) = sakilacustomer.org
###
### upper(left(right(email, char_length(email)-position('@' in email)), 1)) = S
###
### right(right(email, char_length(email)-position('@' in email)), (char_length(right(email, char_length(email)-position('@' in email)))-1)) = akilacustomer.org
###
### right(email, char_length(email)-position('@' in email)) AS domen from customer limit 20;
###
### (char_length(right(email, char_length(email)-position('@' in email)))-1) = длина всего домена -1
###
### concat(upper(left(right(email, char_length(email)-position('@' in email)), 1)), right(right(email, char_length(email)-position('@' in email)), (char_length(right(email, char_length(email)-position('@' in email)))-1))) = Sakilacustomer