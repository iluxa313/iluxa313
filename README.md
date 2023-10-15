# БГУИР Лабораторная работа №1
Условие программы (вариант 74):
Создать файл sh и bat, который выполняет следующее: 
##На вход пакетному файлу приходит абсолютный путь к папке и формат файла (например, doc) (как параметры пакетного файла). В папке найти все файлы указанного формата, вывести в консоль их количество. Если число четное, то вывести в консоль сообщение о количестве активных процессов в ОС в формате “Число активных процессов - Х”. Если число нечетное - завершить выполнение программы через 7 секунд.

## Работа файла bat
Как выглядит код:
```bash
@echo off
set /p folder=Введите путь к папке:
set /p format=Введите формат файлов: 
set /a count=0
for /f %%i in ('dir /b /a-d "%folder%\*.%format%" ^| find /c /v ""') do set "count=%%i"
echo Число файлов формата %format%: %count%
for /f %%P in ('tasklist /NH /FO CSV ^| find /c /v ""') do set "process_count=%%P"
set /a "remainder=count %% 2"
if %remainder% equ 0 echo Количество активных процессов: %process_count%
if %remainder% equ 0 pause
if %remainder% neq 0 echo Завершение программы через 7 секунд...
timeout /t 7 >nul
```
Переменные, которые использовались:

folder - переменная, которая принимает и хранит в себе введённый пользователем путь  

format - переменная, которая принимает и хранит в себе введенный пользователем формат файла

count - переменная, которая сохраняет полученное количество файлов

process_count - переменная, которая сохраняет полученное количество процессов 

remainder - переменная, которая сохраняет в себе полученный остаток от деления значения переменной count на 2

+ @echo off: Эта команда отключает вывод команд в командной строке. Таким образом, все команды в файле .bat выполняются без отображения в окне командной строки.

+ set /p folder=Введите путь к папке:: Эта команда запрашивает у пользователя ввод пути к папке и сохраняет его в переменной %folder%. Пользователю будет предложено ввести путь к папке.

+ set /p format=Введите формат файлов:: Эта команда запрашивает у пользователя ввод формата файлов и сохраняет его в переменной %format%. Пользователю будет предложено ввести формат файлов.

+ set /a count=0: Эта команда инициализирует переменную %count% со значением 0. Переменная %count% будет использоваться для подсчета количества файлов.

+ for /f %%i in ('dir /b /a-d "%folder%\*.%format%" ^| find /c /v ""') do set "count=%%i": Этот цикл for выполняет команду dir для получения списка файлов с указанным форматом в указанной папке. Результаты команды dir передаются в команду find, которая подсчитывает количество строк вывода (то есть количество файлов) и передает это значение в переменную %count%.

+ echo Число файлов формата %format%: %count%: Эта команда выводит количество файлов с указанным форматом (%format%) в указанной папке. Она использует значения переменных %format% и %count%.

+ for /f %%P in ('tasklist /NH /FO CSV ^| find /c /v ""') do set "process_count=%%P": Этот цикл for выполняет команду tasklist, которая получает список всех запущенных процессов. Результаты команды tasklist передаются в команду find, которая подсчитывает количество строк вывода (то есть количество процессов) и передает это значение в переменную %process_count%.

+ set /a "remainder=count %% 2": Эта команда вычисляет остаток от деления переменной %count% на 2 и сохраняет его в переменную %remainder%. Остаток от деления используется для определения того, является ли количество файлов четным или нечетным.

+ if %remainder% equ 0 echo Количество активных процессов: %process_count%: Эта команда проверяет, равен ли %remainder% нулю (т.е. количество файлов четное). Если это так, то выводится сообщение "Количество активных процессов: %process_count%", где %process_count% - это количество активных процессов.

+ if %remainder% equ 0 pause: Эта команда приостанавливает выполнение скрипта и ожидает, пока пользователь нажмет любую клавишу, если количество файлов оказывается четным.

+ if %remainder% neq 0 echo Завершение программы через 7 секунд...: Эта команда проверяет, не равен ли %remainder% нулю (т.е. количество файлов нечетное). Если это так, то выводится сообщение "Завершение программы через 7 секунд...".

+ timeout /t 7 >nul: Эта команда задерживает выполнение скрипта на 7 секунд (время ожидания) и подавляет вывод времени ожидания (>nul). После этого скрипт завершается.

![image](https://github.com/iluxa313/iluxa313/assets/146937077/3619955c-8ca8-4da7-a69f-5af7b1e07674)
![image](https://github.com/iluxa313/iluxa313/assets/146937077/745f7668-c7be-4591-babf-dbd0b3fe13a8)
![image](https://github.com/iluxa313/iluxa313/assets/146937077/1f549bb1-c2a1-49fd-b350-b393ac0d1682)
![image](https://github.com/iluxa313/iluxa313/assets/146937077/574397f5-f4b9-4c87-8a1c-0dbfe35e48e4)




