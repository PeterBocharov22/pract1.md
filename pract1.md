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

