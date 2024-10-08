# Практическое занятие №1.
## Задача 1. Вывести отсортированный в алфавитном порядке список имен пользователей в файле passwd (вам понадобится grep).
```
localhost:~# cut -d: -f1 /etc/passwd | sort

```
![image](https://github.com/user-attachments/assets/2b17e8ea-39f9-4412-b5b2-4b7dd46798ec)

## Задача 2. Вывести данные /etc/protocols в отформатированном и отсортированном порядке для 5 наибольших портов, как показано в примере.

```
localhost:~# cat /etc/protocols | awk '{print $2, $1}' | sort -n -r | head -n 5
```
![image)](https://github.com/user-attachments/assets/b874378e-6ffe-4c32-a4fc-64834d38f00f)

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
![image](https://github.com/user-attachments/assets/b8d6d3a1-55d4-4010-bdc6-4a4eb33bf8a1)

## Задача 4. Написать программу для вывода всех идентификаторов (по правилам C/C++ или Java) в файле (без повторений).
![image](https://github.com/user-attachments/assets/00ff8300-61c6-4721-92a1-dbf47a5a09e2)

## Задача 5. Написать программу для регистрации пользовательской команды (правильные права доступа и копирование в /usr/local/bin).

```
#!/bin/bash
chmod u+rwx $1
cp $1 /usr/local/bin


localhost:~# sudo ./regger.sh mama.sh
localhost:~# cd /usr/local/bin
localhost:/usr/local/bin# ls
```
![image](https://github.com/user-attachments/assets/cea5a708-655f-44a0-95c7-fa901dc33e69)
![image](https://github.com/user-attachments/assets/890d2601-6864-4e7b-b389-2149eafded6b)

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
![image](https://github.com/user-attachments/assets/c7bd0b1e-b45f-41f7-8b61-b8dc035e260b)
![image](https://github.com/user-attachments/assets/44105f5c-8ec6-444f-b6a1-298d132277e6)
![image](https://github.com/user-attachments/assets/1746c3cb-210e-4450-8bab-06d05612aa6f)
![image](https://github.com/user-attachments/assets/ca80647d-f769-49d3-ae10-3e3c2c9e1fc0)


## Задача 7. Написать программу для нахождения файлов-дубликатов (имеющих 1 или более копий содержимого) по заданному пути (и подкаталогам).
```
#!/bin/bash
if [ $# -ne 1 ]; then
    echo "Использование: $0 <Путь к каталогу>"
    exit 1
fi
directory="$1"
 
find "$directory" -type f -print0 | xargs -0 md5sum | sort | uniq -d -w 32 | se>
    echo "Дубликат: $duplicate"
done
```


![image](https://github.com/user-attachments/assets/aef3ed18-378d-42fb-a1df-950c290676c8)
![image](https://github.com/user-attachments/assets/47cba418-831f-4bb4-a3a3-efd8f51aeeb2)

## Задача 8. Написать программу, которая находит все файлы в данном каталоге с расширением, указанным в качестве аргумента и архивирует все эти файлы в архив tar.
![image](https://github.com/user-attachments/assets/d07cc140-5057-4d39-9d7a-5309ef2ba1a4)

## Задача 9. Написать программу, которая заменяет в файле последовательности из 4 пробелов на символ табуляции. Входной и выходной файлы задаются аргументами.
```
#!/bin/bash
input_file="$1"
output_file="$2"
 
sed 's/ /\t/g' "$input_file" > "$output_file"
echo "Замена завершена. Результат сохранен в $output_file."
```

![image](https://github.com/user-attachments/assets/75fa7a43-d093-4cd3-bbed-a3b89a5d7a8f)

![image](https://github.com/user-attachments/assets/8ed98f24-e602-42ce-83fd-0bcc30d851e9)

![image](https://github.com/user-attachments/assets/4db8f23e-f0ad-4bcd-95f3-65f91fc6cec1)
![image](https://github.com/user-attachments/assets/bf374406-0ad6-4483-a79f-b545f97963a2)

## Задача 10. Написать программу, которая выводит названия всех пустых текстовых файлов в указанной директории. Директория передается в программу параметром.

```
#!/bin/bash
directory="$1"
find $1 -type f -size 0 -maxdepth 1
```
![image](https://github.com/user-attachments/assets/68fc69ac-7049-418f-82de-f827441fbd81)
![image](https://github.com/user-attachments/assets/5e728003-fd25-49cb-9113-9b0da639fcd9)
