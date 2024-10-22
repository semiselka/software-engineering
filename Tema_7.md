# ТЕМА 7. Работа с файлами (ввод, вывод)
Отчет по Теме #7 выполнила:
- Балахнина Евгения Николаевна
- АИС-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |
| Задание 6 | + | - |
| Задание 7 | + | - |
| Задание 8 | + | - |
| Задание 9 | + | - |
| Задание 10 | + | - |

знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
Составьте текстовый файл и положите его в одну директорию с программой на Python. Текстовый файл должен состоять минимум из двух строк.

```python
hello everyone!
it's me!
```
### Результат.
![](/screenshot/7L1.PNG)

## Лабораторная работа №2
Напишите программу, которая выведет только первую строку из вашего файла, при этом используйте конструкцию open()/close().

```python
file = open('input.txt', 'r')
print(file.readline())
file.close()
```
### Результат.
![](/screenshot/7L2.PNG)

## Выводы
Программа выводит первую строку файла: "hi, everyone!"

## Лабораторная работа №3
Напишите программу, которая выведет все строки из вашего файла в массиве, при этом используйте конструкцию open()/close(). 

```python
file = open('input.txt', 'r')
print(file.readlines())
file.close()
```
### Результат.
![](/screenshot/7L3.PNG)

## Лабораторная работа №4
Напишите программу, которая выведет все строки из вашего файла в массиве, при этом используйте конструкцию with open().

```python
with open('input.txt', 'r') as f:
  print(f.readlines())
```
### Результат.
![](/screenshot/7L4.PNG)

## Лабораторная работа №5
Напишите программу, которая выведет каждую строку из вашего файла отдельно, при этом используйте конструкцию with open().

```python
with open('input.txt', 'r') as f:
  print(f.read())
```
### Результат.
![](/screenshot/7L5.PNG)

## Лабораторная работа №6
Напишите программу, которая будет добавлять новую строку в ваш файл, а потом выведет полученный файл в консоль. Вывод можно осуществлять любым способом. Обязательно проверьте сам файл, чтобы изменения в нем тоже отображались.

```python
with open('input.txt', 'a') as f:
  f.write('\nAdditional line')

with open('input.txt', 'r') as r:
  print(r.readlines())
```
### Результат.
![](/screenshot/7L6.PNG)

## Выводы
Файл теперь включает новую строку. Все изменения сохраняются и отображаются. 

## Лабораторная работа №7
Напишите программу, которая перепишет всю информацию, которая была у вас в файле до этого, например напишет любые данные из произвольно вами составленного списка. Также не забудьте проверить что измененная вами информация сохранилась в файле. 

```python
new_lines = ['one', 'two', 'one']

with open('input.txt.txt', 'w') as f:
  f.writelines(new_lines)

with open('input.txt.txt', 'r') as r:
  print('Done', r.read())
```
### Результат.
![](/screenshot/7L7.PNG)

## Лабораторная работа №8
Выберите любую папку на своем компьютере, имеющую вложенные директории. Выведите на печать в терминал ее содержимое, как и всех подкаталогов при помощи функции print_docs(directory).

```python
import os
def print_docs(directory):
    for root, dirs, files in os.walk(directory):
        for name in files:
            print(os.path.join(root, name))
print_docs(r'C:\Users\User\PycharmProjects')
```
### Результат.
![](/screenshot/7L8.PNG)

## Лабораторная работа №9
Документ «input.txt» содержит следующий текст:

Приветствие
Спасибо 
Извините 
Пожалуйста 
До свидания 
Ты готов?
Как дела?
С днем рождения! 
Удача!
Я тебя люблю.

Требуется реализовать функцию, которая выводит слово, имеющее максимальную длину (или список слов, если таковых несколько).
Проверьте работоспособность программы на своем наборе данных.

```python
def max_l(filename):
  with open(filename, 'r', encoding='utf-8') as file:
    words = file.read().split()
  max_length = max(len(word) for word in words)
  return [word for word in words if len(word) == max_length]


print(max_l('input.txt'))
```
### Результат.
![](/screenshot/7L9.PNG)



## Лабораторная работа №10
Требуется создать csv-файл «rows_300.csv» со следующими столбцами:
•	№ - номер по порядку (от 1 до 300);
•	Секунда – текущая секунда на вашем ПК;
•	Микросекунда – текущая миллисекунда на часах.
Для наглядности на каждой итерации цикла искусственно приостанавливайте скрипт на 0,01 секунду.

```python
import csv
import time
with open('file_csv.csv', 'w', newline='') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow(['№', 'Секунда', 'Микросекунда'])
    for i in range(1, 301):
        seconds = time.localtime().tm_sec
        microseconds = int(time.time() * 1e6) % 1e6
        print(f"Строка {i}: Секунды - {seconds}, Микросекунды - {microseconds}")
        writer.writerow([i, seconds, microseconds])
        time.sleep(0.01)
```
### Результат.
![](/screenshot/7L10.PNG)


## Самостоятельная работа №1
Найдите в интернете любую статью (объем статьи не менее 200 слов), скопируйте ее содержимое в файл и напишите программу, которая считает количество слов в текстовом файле и определит самое часто встречающееся слово. Результатом выполнения задачи будет: скриншот файла со статьей, листинг кода, и вывод в консоль, в котором будет указана вся необходимая информация.

```python
def number_of_words(file):
    words = []
    summa = []
    word_count = {}

    with open(file, 'r', encoding='utf-8') as f:
        for line in f:
            line = line.lower().split()
            len_of_line = len(line)
            words.append((line, len_of_line))

            for word in line:
                if word in word_count:
                    word_count[word] += 1
                else:
                    word_count[word] = 1
        for i, v in words:
            summa.append(v)
        print(f'Всего слов в статье: {sum(summa)}')
    word_with_maximus = max(word_count, key=word_count.get)
    maximus = max(word_count.values())
    print(f'самое часто повторяющееся слово в тексте: {word_with_maximus}\nОно повторяется: {maximus} раз')
number_of_words('input.txt')
```
### Результат.
![](/screenshot/7S1.PNG)
![](/screenshot/TEXT.PNG)

## Выводы
Программа показывает общее количество слов и самое частое слово с его частотой. В этой программе я освоила новый метод представления списка, который включает создание кортежа. Получить доступ к его элементам можно с помощью индексов. Кроме того, я повторила вызовы значений по ключам.

## Самостоятельная работа №2
У вас появилась потребность в ведении книги расходов, посмотрев все существующие варианты вы пришли к выводу что вас ничего не устраивает и нужно все делать самому. Напишите программу для учета расходов. Программа должна позволять вводить информацию о расходах, сохранять ее в файл и выводить существующие данные в консоль. Ввод информации происходит через консоль. Результатом выполнения задачи будет: скриншот файла с учетом расходов, листинг кода, и вывод в консоль, с демонстрацией работоспособности программы.

```python
def add_expense():
    description = input("Введите описание расходов: ")
    amount = input("Введите сумму расходов: ")
    with open('input.txt.txt', 'a', encoding='utf-8') as file:
        file.write(f'{description}: {amount}\n')
def show_expenses():
    print("Записи расходов:")
    with open('input.txt.txt', 'r', encoding='utf-8') as file:
        for line in file:
            print(line.strip())
while True:
    action = input("Введите 'добавить' для добавления расхода или 'показать' для вывода всех расходов: ").strip()
    if action.lower() == 'добавить':
        add_expense()
    elif action.lower() == 'показать':
        show_expenses()
    else:
        print("Неверный ввод. Попробуйте снова.")
```
### Результат.
![](/screenshot/7S2.PNG)

## Выводы
Программа позволяет добавить и показать записи расходов. 

## Самостоятельная работа №3
Имеется файл input.txt с текстом на латинице. Напишите программу, которая выводит следующую статистику по тексту: количество букв латинского алфавита; число слов; число строк.
•	Текст в файле: Beautiful is better than ugly. Explicit is better than implicit. Simple is better than complex.
Complex is better than complicated.
•	Ожидаемый результат: Input file contains:
108 letters
20 words
4 lines

```python
def text_statistics(filename):
    with open(filename, 'r', encoding='utf-8') as file:
        text = file.read()
    letters_count = sum(c.isalpha() for c in text)
    words_count = len(text.split())
    lines_count = text.count('\n') + 1
    print(f"Input file contains:")
    print(f"{letters_count} letters")
    print(f"{words_count} words")
    print(f"{lines_count} lines")
text_statistics('aaa.txt')
```
### Результат.
![](/screenshot/7S3.PNG)

## Выводы
Программа выводит количество букв, слов и строк из файла. 

## Самостоятельная работа №4
Напишите программу, которая получает на вход предложение, выводит его в терминал, заменяя все запрещенные слова звездочками * (количество звездочек равно количеству букв в слове). Запрещенные слова, разделенные символом пробела, хранятся в текстовом файле input.txt. Все слова в этом файле записаны в нижнем регистре. Программа должна заменить запрещенные слова, где бы они ни встречались, даже в середине другого слова. Замена производится независимо от регистра: если файл input.txt содержит запрещенное слово exam, то слова exam, Exam, ExaM, EXAM и exAm должны быть заменены на ****.
•	Запрещенные слова:
hello email python the exam wor is
•	Предложение для проверки:
Hello, world! Python IS the programming language of thE future. My EMAIL is i@ebalahnina.ru
PYTHON is awesome!!!!
•	Ожидаемый результат:
*****, ***ld! ****** ** *** programming language of *** future. My ***** ** i@ebalahnina.ru

```python
import re
def censor_text(input_text, banned_words):
    for word in banned_words:
        input_text = re.sub(word, '*' * len(word), input_text, flags=re.IGNORECASE)
    return input_text
with open('input.txt', 'r', encoding='utf-8') as file:
    banned_words = file.read().strip().split()
sentence = input("Введите предложение для проверки: ")
censored_sentence = censor_text(sentence, banned_words)
print(censored_sentence)

```
### Результат.
![](/screenshot/7S4.PNG)

## Выводы
Программа заменяет запрещенные слова на ***

## Самостоятельная работа №5
Самостоятельно придумайте и решите задачу, которая будет взаимодействовать с текстовым файлом.
Подсчет строк в файле и вывод их на экран.

```python
filename = 'input.txt'
with open(filename, 'r') as file:
    lines = file.readlines()
    for line in lines:
        print(line.strip())
print(f'Количество строк в файле: {len(lines)}')
```
### Результат.
![](/screenshot/7S5.PNG)
## Выводы
Данная программа считает количество строк в текстовом файле и выводит их и количество строк.

## Общие выводы по теме
Были изучены основные операции с текстовыми файлами в Python, а именно:

1. Создание и запись в файл - создавать текстовые файлы и добавлять в них данные.
   
2. Чтение из файла: с помощью readline(), readlines() и read(), я научилась извлекать данные из файлов. Используя конструкцию with open(), можно автоматическое закрывать файлов.

3. Добавление и редактирование содержимого файла: можно добавлять строки в существующий файл и переписывать информацию, используя w и a режимы доступа.

4. Работа с директориями: научилась извлекать и выводить содержимое каталогов с помощью модуля os.

5. Реализовала функции для анализа текста, в частности, для нахождения слова с максимальной длиной.

6. Создание CSV файлов.

Все выполненные задания помогли углубить понимание принципов работы с файлами и управления данными в Python. 
