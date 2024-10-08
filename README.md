# Домашнее задание к занятию 3 «Резервное копирование» - `Александра Бужор`

## Задание 1
- Составьте команду rsync, которая позволяет создавать зеркальную копию домашней директории пользователя в директорию /tmp/backup
- Необходимо исключить из синхронизации все директории, начинающиеся с точки (скрытые)
- Необходимо сделать так, чтобы rsync подсчитывал хэш-суммы для всех файлов, даже если их время модификации и размер идентичны в источнике и приемнике.
- На проверку направить скриншот с командой и результатом ее выполнения

## Ответ:
```
rsync -av --delete --exclude '.*' /home/chistov/ /tmp/backup
```
![image](https://github.com/user-attachments/assets/63f93210-a324-4254-8a28-971735d335d7)

## Задание 2
- Написать скрипт и настроить задачу на регулярное резервное копирование домашней директории пользователя с помощью rsync и cron.
- Резервная копия должна быть полностью зеркальной
- Резервная копия должна создаваться раз в день, в системном логе должна появляться запись об успешном или неуспешном выполнении операции
- Резервная копия размещается локально, в директории /tmp/backup
- На проверку направить файл crontab и скриншот с результатом работы утилиты.
  
## Ответ:
```
#!/bin/sh
rsync -av --delete --exclude '.*' /home/chistov/ /tmp/backup >> /var/log/crontab.log
```
Софержание crontab:

![image](https://github.com/user-attachments/assets/da87b56b-7482-463d-857c-f9d0c1a12e4e)

Проверка скрипта:

![image](https://github.com/user-attachments/assets/5536209c-b7b8-4f5c-9cdd-82581dcddc5c)

Проверка логов:
tail /var/log/crontab.log

![image](https://github.com/user-attachments/assets/ef7004f5-88d8-45f5-8b8d-216a94fe8743)




