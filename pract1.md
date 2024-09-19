# Практическое занятие №1.
## Задача 1. Вывести отсортированный в алфавитном порядке список имен пользователей в файле passwd (вам понадобится grep).
```
localhost:~# cut -d: -f1 /etc/passwd | sort

```
![Снимок экрана (44)](https://github.com/user-attachments/assets/2b17e8ea-39f9-4412-b5b2-4b7dd46798ec)

## Задача 2. Вывести данные /etc/protocols в отформатированном и отсортированном порядке для 5 наибольших портов, как показано в примере.

```
localhost:~# cat /etc/protocols | awk '{print $2, $1}' | sort -n -r | head -n 5
```
![Снимок экрана (45)](https://github.com/user-attachments/assets/b874378e-6ffe-4c32-a4fc-64834d38f00f)

## Задача 3.Написать программу banner средствами bash для вывода текстов, как в следующем примере (размер баннера должен меняться!).

```
nano banner.sh                                          
#!/bin/bash
text=$1
length=${#text}
line="+-"
for ((i=0;i<length;i++))
do
line+="-"
done
line+="-+"
echo $line
echo "|" $text "|"
echo $line

localhost:~# chmod +x banner.sh

localhost:~# ./banner.sh "Hello from RTU MIREA!"
+-----------------------+
| Hello from RTU MIREA! |
+-----------------------+
```
![Снимок экрана (46)](https://github.com/user-attachments/assets/b8d6d3a1-55d4-4010-bdc6-4a4eb33bf8a1)

## Задача 4. Написать программу для вывода всех идентификаторов (по правилам C/C++ или Java) в файле (без повторений).
![Снимок экрана (47)](https://github.com/user-attachments/assets/00ff8300-61c6-4721-92a1-dbf47a5a09e2)

## Задача 5. Написать программу для регистрации пользовательской команды (правильные права доступа и копирование в /usr/local/bin).

```
#!/bin/bash
chmod u+rwx $1
cp $1 /usr/local/bin


localhost:~# sudo ./regger.sh mama.sh
localhost:~# cd /usr/local/bin
localhost:/usr/local/bin# ls
```
![Снимок экрана (48)](https://github.com/user-attachments/assets/cea5a708-655f-44a0-95c7-fa901dc33e69)
![Снимок экрана (49)](https://github.com/user-attachments/assets/890d2601-6864-4e7b-b389-2149eafded6b)

## Задача 6. Написать программу для проверки наличия комментария в первой строке файлов с расширением c, js и py.
```
#!/bin/bash
line=$(head -1 $1)
if [[$line == "//"* ]] || [[$line == "#"* ]]; then
echo "First line have comment"
else
echo "First line dont have comment"
fi
```
