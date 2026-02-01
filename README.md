# Домашнее задание к занятию "`Работа с данными (DDL/DML)`" - `Столяренко Александр`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw.
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

`Через docker разворачивал mysql8`  

`Выполнил запрос на получение списка пользователей в базе данных:`

![1](https://github.com/Mr-Alex01/sql_ddl_dml/blob/main/img/1.jpg)

`Затем выполнил запрос на получение списка прав для пользователя sys_temp:`

![2](https://github.com/Mr-Alex01/sql_ddl_dml/blob/main/img/2.jpg)

`И использовал команду для получения всех таблиц базы данных после восстановленного дампа:`

![3](https://github.com/Mr-Alex01/sql_ddl_dml/blob/main/img/3.jpg)

`Простыню из команд пришлось использовать такую:`

`CREATE USER 'sys_temp'@'%' IDENTIFIED BY 'password';`

`SELECT user, host FROM mysql.user;`

`GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'%' WITH GRANT OPTION;`  
`FLUSH PRIVILEGES;`

`SHOW GRANTS FOR 'sys_temp'@'%';`

`ALTER USER 'sys_temp'@'%' IDENTIFIED WITH mysql_native_password BY 'password';`

`SELECT USER();`

`USE sakila;`  
`SHOW TABLES;`

---

### Задание 2

`Нашёл такую возможность использовать многосоставной Primary Key, чтобы вытащить нужную информацию:`

SELECT  
    TABLE_NAME AS Название таблицы,  
    GROUP_CONCAT(COLUMN_NAME ORDER BY ORDINAL_POSITION SEPARATOR ', ')  
         AS Название первичного ключа  
FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE  
WHERE TABLE_SCHEMA = 'sakila'  
  AND CONSTRAINT_NAME = 'PRIMARY'  
GROUP BY TABLE_NAME  
ORDER BY TABLE_NAME;  

`В Excel отобразил полученную таблицу:`

![4](https://github.com/Mr-Alex01/sql_ddl_dml/blob/main/img/4.jpg)