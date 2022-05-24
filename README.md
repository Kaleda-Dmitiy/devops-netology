# devops-netology_Dmitriy-Kaleda

<details>
<summary>МЕНЮ</summary> 

##  [Домашнее задание к занятию "6.3. mySQL"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-63-mysql-1)
##  [Домашнее задание к занятию "6.2. SQL"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-62-sql-1)
##  Д[омашнее задание к занятию "6.1. Типы и структура СУБД"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-61-типы-и-структура-субд-1)
##  [Домашнее задание к занятию "5.4. Оркестрация группой Docker контейнеров на примере Docker Compose"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-54-оркестрация-группой-docker-контейнеров-на-примере-docker-compose-1)
##  [Домашнее задание к занятию "5.2. Применение принципов IaaC в работе с виртуальными машинами"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-52-применение-принципов-iaac-в-работе-с-виртуальными-машинами)
##  [Домашнее задание к занятию "5.1. Введение в виртуализацию. Типы и функции гипервизоров. Обзор рынка вендоров и областей применения."](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-51-введение-в-виртуализацию-типы-и-функции-гипервизоров-обзор-рынка-вендоров-и-областей-применения)
##  [Курсовая работа по итогам модуля "DevOps и системное администрирование"](https://github.com/Kaleda-Dmitiy/devops-netology#курсовая-работа-по-итогам-модуля-devops-и-системное-администрирование-1)
##  [Домашнее задание к занятию "4.2. Использование Python для решения типовых DevOps задач"](https://github.com/Kaleda-Dmitiy/devops-netology/blob/main/4_2.md)
##  [Домашнее задание к занятию "4.1. Командная оболочка Bash: Практические навыки"](https://github.com/Kaleda-Dmitiy/devops-netology/blob/main/4_1.md)
##
##  [Домашнее задание к занятию "3.8. Компьютерные сети, лекция 3"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-38-компьютерные-сети-лекция-3)
##  [Домашнее задание к занятию "3.7. Компьютерные сети, лекция 2"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-37-компьютерные-сети-лекция-2)
##  [Домашнее задание к занятию "3.6. Компьютерные сети, лекция 1"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-36-компьютерные-сети-лекция-1)
##  [Домашнее задание к занятию "3.5. Файловые системы"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-35-файловые-системы)
##  [Домашнее задание к занятию "3.4. Операционные системы, лекция 2"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-34-операционные-системы-лекция-2)
##  [Домашнее задание к занятию "3.2. Работа в терминале, лекция 2"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-32-работа-в-терминале-лекция-2-1)
##  [Домашнее задание к занятию "3.1. Работа в терминале, лекция 1"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-31-работа-в-терминале-лекция-1)
##  [Домашнее задание к занятию «2.4. Инструменты Git»](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-24-инструменты-git)
</details>

## Домашнее задание к занятию "6.3. mySQL"
<details>
<summary>Решение</summary> 
Используя docker поднимите инстанс MySQL (версию 8). Данные БД сохраните в volume.

Ответ:
Выполнение комманд: 

```
0:52:39 oragons@upc(0):~$ docker pull mysql:8.0
8.0: Pulling from library/mysql
Digest: sha256:b1cc887ed32cc6c2f217b12703bd05f503f2037892c8bb226047fe5dff85a109
Status: Downloaded newer image for mysql:8.0
docker.io/library/mysql:8.0
20:54:36 oraogns@upc(0):~$ docker volume create vol_mysql
vol_mysql
20:55:29 oragons@upc(0):~$ docker run --rm --name mysql-docker -e MYSQL_ROOT_PASSWORD=mysql -ti -p 3306:3306 -v vol_mysql:/etc/mysql/ mysql:8.0
...

```
Статус БД:
```
mysql> \s
--------------
mysql  Ver 8.0.23 for Linux on x86_64 (MySQL Community Server - GPL)

Connection id:		13
Current database:	test_db
Current user:		root@localhost
SSL:			Not in use
Current pager:		stdout
Using outfile:		''
Using delimiter:	;
Server version:		8.0.23 MySQL Community Server - GPL
Protocol version:	10
Connection:		Localhost via UNIX socket
Server characterset:	utf8mb4
Db     characterset:	utf8mb4
Client characterset:	latin1
Conn.  characterset:	latin1
UNIX socket:		/var/run/mysqld/mysqld.sock
Binary data as:		Hexadecimal
Uptime:			24 min 26 sec

Threads: 2  Questions: 57  Slow queries: 0  Opens: 162  Flush tables: 3  Open tables: 80  Queries per second avg: 0.038
--------------

mysql> 
```
Данные БД:
```
mysql> use temp_db;
ERROR 1049 (42000): Unknown database 'temp_db'
mysql> use test_db;
Database changed
mysql> show tables;
+-------------------+
| Tables_in_test_db |
+-------------------+
| orders            |
+-------------------+
1 row in set (0.00 sec)

mysql> select count(*) from orders where price >300;
+----------+
| count(*) |
+----------+
|        1 |
+----------+
1 row in set (0.00 sec)

Число записей 1
```

Создайте пользователя test в БД c паролем test-pass, используя:

Ответ:
```    
mysql> CREATE USER 'test'@'localhost' IDENTIFIED BY 'test-pass';
Query OK, 0 rows affected (0.22 sec)

mysql> 
mysql> ALTER USER 'test'@'localhost' ATTRIBUTE '{"fname":"James", "lname":"Pretty"}';
Query OK, 0 rows affected (0.16 sec)

mysql> 
mysql> ALTER USER 'test'@'localhost' 
    -> IDENTIFIED BY 'test-pass' 
    -> WITH
    -> MAX_QUERIES_PER_HOUR 100
    -> PASSWORD EXPIRE INTERVAL 180 DAY
    -> FAILED_LOGIN_ATTEMPTS 3 PASSWORD_LOCK_TIME 2;
Query OK, 0 rows affected (0.12 sec)

mysql> 
mysql> GRANT Select ON test_db.orders TO 'test'@'localhost';
Query OK, 0 rows affected, 1 warning (0.14 sec)

mysql> 
mysql> SELECT * FROM INFORMATION_SCHEMA.USER_ATTRIBUTES WHERE USER='test';
+------+-----------+---------------------------------------+
| USER | HOST      | ATTRIBUTE                             |
+------+-----------+---------------------------------------+
| test | localhost | {"fname": "James", "lname": "Pretty"} |
+------+-----------+---------------------------------------+
1 row in set (0.03 sec)
```

Установите профилирование SET profiling = 1. Изучите вывод профилирования команд SHOW PROFILES;.
Исследуйте, какой engine используется в таблице БД test_db и приведите в ответе.
Измените engine и приведите время выполнения и запрос на изменения из профайлера в ответе:
- на MyISAM
- на InnoDB

Ответ:
```
mysql> SELECT TABLE_NAME,ENGINE,ROW_FORMAT,TABLE_ROWS,DATA_LENGTH,INDEX_LENGTH FROM information_schema.TABLES WHERE table_name = 'orders' and  TABLE_SCHEMA = 'test_db' ORDER BY ENGINE asc;
+------------+--------+------------+------------+-------------+--------------+
| TABLE_NAME | ENGINE | ROW_FORMAT | TABLE_ROWS | DATA_LENGTH | INDEX_LENGTH |
+------------+--------+------------+------------+-------------+--------------+
| orders     | InnoDB | Dynamic    |          5 |       16384 |            0 |
+------------+--------+------------+------------+-------------+--------------+
1 row in set (0.06 sec)



mysql> ALTER TABLE orders ENGINE = MyISAM;
Query OK, 5 rows affected (1.17 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> ALTER TABLE orders ENGINE = InnoDB;
Query OK, 5 rows affected (1.37 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> show profiles;
+----------+------------+------------------------------------+
| Query_ID | Duration   | Query                              |
+----------+------------+------------------------------------+
|        1 | 0.00013225 | show prifiles                      |
|        2 | 1.17695100 | ALTER TABLE orders ENGINE = MyISAM |
|        3 | 1.36970325 | ALTER TABLE orders ENGINE = InnoDB |
+----------+------------+------------------------------------+
3 rows in set, 1 warning (0.00 sec)

Продолжительность переключения на  MyISAM: 1,17
ПроПродолжительность переключения на InnoDB: 1,36
```

Изучите файл my.cnf в директории /etc/mysql. Измените его согласно ТЗ (движок InnoDB):

Ответ:
```
[mysqld]
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
datadir         = /var/lib/mysql
secure-file-priv= NULL

#Set IO Speed
# 0 - скорость
# 1 - сохранность
# 2 - универсальный параметр
innodb_flush_log_at_trx_commit = 0 

#Set compression
# Barracuda - формат файла с сжатием
innodb_file_format=Barracuda

#Set buffer
innodb_log_buffer_size	= 1M

#Set Cache size
key_buffer_size = 640М

#Set log size
max_binlog_size	= 100M
```
</details>

## Домашнее задание к занятию "6.2. SQL"
<details>
<summary>Решение</summary> 
Используя docker поднимите инстанс PostgreSQL (версию 12) c 2 volume, в который будут складываться данные БД и бэкапы.

Ответ:
```
12:17:28 oragons@upc(0):~$ docker pull postgres:12

13:00:03 oragons@upc(0):~$ docker volume create vol2

vol2

13:00:15 oragons@upc(0):~$ docker volume create vol1

vol1

13:00:03 oragons@upc(0):~$ docker run --rm --name pg-docker -e POSTGRES_PASSWORD=postgres -ti -p 5432:5432 -v vol1:/var/lib/postgresql/data -v vol2:/var/lib/postgresql postgres:12

13:00:35 oragons@upc(0):~$ docker run --rm --name pg-docker -e POSTGRES_PASSWORD=postgres -ti -p 5432:5432 -v vol1:/var/lib/postgresql/data -v vol2:/var/lib/postgresql postgres:12
```
![](pic/ss_6_1.png)

В БД из задачи 1:

создайте пользователя test-admin-user и БД test_db
в БД test_db создайте таблицу orders и clients (спeцификация таблиц ниже)
предоставьте привилегии на все операции пользователю test-admin-user на таблицы БД test_db
создайте пользователя test-simple-user
предоставьте пользователю test-simple-user права на SELECT/INSERT/UPDATE/DELETE данных таблиц БД test_db
Ответ:
Команды:
```
CREATE DATABASE test_db
CREATE ROLE "test-admin-user" SUPERUSER NOCREATEDB NOCREATEROLE NOINHERIT LOGIN;

CREATE TABLE orders 
(
id integer, 
name text, 
price integer, 
PRIMARY KEY (id) 
);

CREATE TABLE clients 
(
	id integer PRIMARY KEY,
	lastname text,
	country text,
	booking integer,
	FOREIGN KEY (booking) REFERENCES orders (Id)
);

CREATE ROLE "test-simple-user" NOSUPERUSER NOCREATEDB NOCREATEROLE NOINHERIT LOGIN;
GRANT SELECT ON TABLE public.clients TO "test-simple-user";
GRANT INSERT ON TABLE public.clients TO "test-simple-user";
GRANT UPDATE ON TABLE public.clients TO "test-simple-user";
GRANT DELETE ON TABLE public.clients TO "test-simple-user";
GRANT SELECT ON TABLE public.orders TO "test-simple-user";
GRANT INSERT ON TABLE public.orders TO "test-simple-user";
GRANT UPDATE ON TABLE public.orders TO "test-simple-user";
GRANT DELETE ON TABLE public.orders TO "test-simple-user";
```

Скриншоты 
Список БД:

![](pic/ss_6_2_0.png)

Список Таблиц и привелегий:

![](pic/ss_6_2_1.png)

Скрины из Beaver:

![](pic/ss_6_2_2.png)


Используя SQL синтаксис - наполните таблицы следующими тестовыми данными:

Ответ:
```
insert into orders VALUES (1, 'Шоколад', 10), (2, 'Принтер', 3000), (3, 'Книга', 500), (4, 'Монитор', 7000), (5, 'Гитара', 4000);
insert into clients VALUES (1, 'Иванов Иван Иванович', 'USA'), (2, 'Петров Петр Петрович', 'Canada'), (3, 'Иоганн Себастьян Бах', 'Japan'), (4, 'Ронни Джеймс Дио', 'Russia'), (5, 'Ritchie Blackmore', 'Russia');
select count (*) from orders;
select count (*) from clients;
```
![](pic/ss_6_3_1.png)


Часть пользователей из таблицы clients решили оформить заказы из таблицы orders. Используя foreign keys свяжите записи из таблиц, согласно таблице:

Ответ:
update  clients set booking = 3 where id = 1;
update  clients set booking = 4 where id = 2;
update  clients set booking = 5 where id = 3;

Запрос получения Вариант1 -  учитывает наличие в таблице заказов данных:

select * from clients as c where  exists (select id from orders as o where c.booking = o.id) ;
Запрос получения Вариант2 - проверяет на непустые значения у клиентов по заказам:
select * from clients where booking is not null

![](pic/ss_6_4_1.png)


Получите полную информацию по выполнению запроса выдачи всех пользователей из задачи 4 (используя директиву EXPLAIN). Приведите получившийся результат и объясните что значат полученные значения.

![](pic/ss_6_5_1.png)

Вариант 1
Показывает стоимость(нагрузку на исполнение) запроса (не оптимальный в сравнении с Вар2)
Показывает шаги связи, и сбор сканирование таблиц после связи

Вариант 2
Так же показывает стоимость(нагрузку на исполнение) запроса , и фильтрацию по полю Booking для выборки.
По обоим планам видно что Вар2 оптимальней. 
Создайте бэкап БД test_db и поместите его в volume, предназначенный для бэкапов (см. Задачу 1).
Остановите контейнер с PostgreSQL (но не удаляйте volumes).
Поднимите новый пустой контейнер с PostgreSQL.
Восстановите БД test_db в новом контейнере.
Приведите список операций, который вы применяли для бэкапа данных и восстановления.

Ответ:
```
  17:23:15 oraogns@upc(0):~$ docker exec -t pgre-docker pg_dump -U postgres test_db -f /var/lib/postgresql/data/dump_test.sql

  17:29:18 oragons@upc(0):~$ docker exec -i pgre-docker2 psql -U postgres -d test_db -f /var/lib/postgresql/data/dump_test.sql
  SET
  SET
  SET
  SET
  SET
  set_config 
  ------------
 
  (1 row)

  SET
SET
SET
SET
SET
SET
CREATE TABLE
ALTER TABLE
CREATE TABLE
ALTER TABLE
COPY 5
COPY 5
ALTER TABLE
ALTER TABLE
ALTER TABLE
GRANT
GRANT
17:33:29 oragons@upc(0):~$ 
```

![](pic/ss_6_6_1.png)

</details>

## Домашнее задание к занятию "6.1. Типы и структура СУБД"

<details>
<summary>Решение</summary>
Выберите подходящие типы СУБД для каждой сущности и объясните свой выбор.

Ответ:
```
Описание задачи отсутсвует, по одной предметной области сложно судить, но примерно так
        

Электронные чеки в json виде: Документо-ориентированная - классичиское применение документов json(судя по лекции)

Склады и автомобильные дороги для логистической компании: Сетевая - иерархическая с множеством узлов, 
но в зависимости от целей, можно и графовую использовать т.к. графы обычно используют для решения структурных задачь в теории СМО (если правильно помню)

Генеалогические деревья: Иерархическая- класические деревья с одним родителем

Кэш идентификаторов клиентов с ограниченным временем жизни для движка аутенфикации: Ключ-значение тоже класическая постановка задачи для данного типа

Отношения клиент-покупка для интернет-магазина - Реляционная - так как тут отношение М:М, то логичнее использовать такое, и в каждом есть описание,
но по терии лекции из NoSQL больше похоже на Графовую
```

Вы создали распределенное высоконагруженное приложение и хотите классифицировать его согласно CAP-теореме. Какой классификации по CAP-теореме соответствует ваша система, если (каждый пункт - это отдельная реализация вашей системы и для каждого пункта надо привести классификацию)

Ответ:
```
Данные записываются на все узлы с задержкой до часа (асинхронная запись): CA, EL-PC
При сетевых сбоях, система может разделиться на 2 раздельных кластера: AP, PA-EL
Система может не прислать корректный ответ или сбросить соединение: CP, PA-EC
```

Могут ли в одной системе сочетаться принципы BASE и ACID? Почему?

Ответ:
```
Принцыпы BASE и ACID сочетаться не могут. По ACID - данные согласованные, а по BASE - могут быть неверные, следовательно они противоречат друг другу.
Вам дали задачу написать системное решение, основой которого бы послужили:

фиксация некоторых значений с временем жизни
реакция на истечение таймаута
```

Вы слышали о key-value хранилище, которое имеет механизм Pub/Sub. Что это за система? Какие минусы выбора данной системы?
Ответ:
```
Основываясь на лекции - это Redis
    Минусы Redis:
Требуютсядостаточные ресурсы RAM(оперативной памяти) + нужно следить за достатончостью памяти 
отсутсвие поддержки  языка SQL, т.е. проблема оперативного поиска данных  
при отказе сервера все данные с последней синхронизации с диском будут утеряны
```
</details>

## Домашнее задание к занятию "5.4. Оркестрация группой Docker контейнеров на примере Docker Compose"
<details>
<summary>Решение</summary> 

### Задача 1

Создать собственный образ операционной системы с помощью Packer.

Для получения зачета, вам необходимо предоставить:
- Скриншот страницы, как на слайде из презентации (слайд 37).
![](pic/05.04-1.jpg)

### Задача 2

Создать вашу первую виртуальную машину в Яндекс.Облаке.

Для получения зачета, вам необходимо предоставить:
- Скриншот страницы свойств созданной ВМ:
![](pic/05.04-2.jpg)

### Задача 3

Создать ваш первый готовый к боевой эксплуатации компонент мониторинга, состоящий из стека микросервисов.

Для получения зачета, вам необходимо предоставить:
- Скриншот работающего веб-интерфейса Grafana с текущими метриками:
![](pic/05.04-3.jpg)

### Задача 4 (*)

Создать вторую ВМ и подключить её к мониторингу развёрнутому на первом сервере.

Для получения зачета, вам необходимо предоставить:
- Скриншот из Grafana, на котором будут отображаться метрики добавленного вами сервера.
![](pic/05.04-4.jpg)

Создаем node02.tf по аналогии с node01.tf, добавив ip
```
  network_interface {
    ....
    ....
    ip_address = "192.168.101.12"
  }
```
Добавляем в inventory
```
....
[monitoring:children]
machines

[machines]
node02.netology.cloud ansible_host=-----ip_node2-----
```
Создаем exporters/docker-compose.exporters.yml по аналогии с node01   
Создаем docker-compose.yml с секциями nodeexporter и cadvisor  
Создаем add_nodes.yml по аналогии с provision.yml  
Добавляем node02 - ansible-playbook add_nodes.yml  
В Grafana на дашбордах в Metrics-Legend добавляем {{instance}}
</details>

## Домашнее задание к занятию "5.2. Применение принципов IaaC в работе с виртуальными машинами"
<details>
<summary>Решение</summary> 

### Задача 1

> Опишите своими словами основные преимущества применения на практике IaaC паттернов.

- Копии конфигураций серверов всегда доступны в стороннем хранилище, если что-то случиться с сервером - бекап есть 
- Доступна история изменений, можно откатиться если что-то пошло не так
- Если нужно что-то уточнить о причинах или принятых решениях в конфигурации - известно к кому обращаться
- Удобно масштабировать
- Удобно вносить изменения - централизованно, через гит

> Какой из принципов IaaC является основополагающим?

Идемпотентность: возможность описать желаемое состояние того, что конфигурируется, с определённой гарантией что оно будет достигнуто.

### Задача 2

> Чем Ansible выгодно отличается от других систем управление конфигурациями?

- Если не удалось доставить конфигурацию на сервер, он оповестит об этом.
- Более простой синтаксис, чем, например, у Saltstack
- Работает без агента на клиентах, использует ssh для доступа на клиент

> Какой, на ваш взгляд, метод работы систем конфигурации более надёжный push или pull?

Push надёжней, т.к. централизованно управляет конфигурацией и исключает ситуации, когда кто-то что-то исправил напрямую на сервере и не отразил в репозитории - это может потеряться или создавать непредсказуемые ситуации.

### Задача 3

> Установить на личный компьютер:
> 
> - VirtualBox
> - Vagrant
> - Ansible
> 
> *Приложить вывод команд установленных версий каждой из программ, оформленный в markdown.*

Я постоянню использую WSL2, но его невозможно использовать вместе с VirtualBox, поэтому воспользовался Hyper-V из состава Windows 11 Pro, а Ansible буду использовать внутри виртуальной машины с ровиженером `ansible_local`

* Vagrant

      PS C:\Users\sergey> vagrant --version
      Vagrant 2.2.18

* Varantfile

      # -*- mode: ruby -*-
      # vi: set ft=ruby :
      
      Vagrant.configure("2") do |config|
          config.vm.box = "bento/ubuntu-20.04"
          config.vm.provider "hyperv"
          
          config.vm.network "public_network", bridge: "Default Switch"
          config.vm.synced_folder ".", "/vagrant", disabled: true
      
          config.vm.provider "hyperv" do |h|
              h.vm_integration_services = { 
                guest_service_interface: true
              }
          end
      
          config.vm.provision "shell", inline: <<-SHELL
            apt-get update
            apt-get install -y ansible
          SHELL
        end
               
* Ubuntu

      vagrant@ubuntu-20:~$ dmesg | grep 'Hypervisor detected'
      [    0.000000] Hypervisor detected: Microsoft Hyper-V

* Ansible

      vagrant@ubuntu-20:~$ ansible --version
      ansible 2.9.6
        config file = /etc/ansible/ansible.cfg
        configured module search path = ['/home/vagrant/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
        ansible python module location = /usr/lib/python3/dist-packages/ansible
        executable location = /usr/bin/ansible
        python version = 3.8.2 (default, Apr 27 2020, 15:53:34) [GCC 9.3.0]

</details>


## Домашнее задание к занятию "5.1. Введение в виртуализацию. Типы и функции гипервизоров. Обзор рынка вендоров и областей применения."

<details>

### Задача 1: Опишите кратко, как вы поняли: в чем основное отличие полной (аппаратной) виртуализации, паравиртуализации и виртуализации на основе ОС.

Основная разница в необходимости модифицировать гостевые ОС:
* При аппаратной виртуализации она не требуется;
* Для паравиртуализации нужна модификация ядра и драйверов;
* При виртуализации средствами ОС, гостевая ОС не имеет собственного ядра, использует ядро хоста.

Ещё разница в производительности. Чем больше модифицирована ОС, тем производительность выше. Наиболее высокая у виртуализации средствами ОС, так как приложения напрямую используют ядро хостовой ОС.

### Задача 2: Выберите один из вариантов использования организации физических серверов, в зависимости от условий использования.

| Условия | Организация | Почему |
| --- | --- | --- |
| Высоконагруженная база данных, чувствительная к отказу | физические сервера | Виртуализация даёт оверхед и увеличивает латентность. В высоконагруженной системе это нежелательно, а достичь отказоустойчивости можно резервированием. Постоянно нагруженной системе потребуется максимум ресурсов хоста, присутствие соседей которые могут их отобрать тоже нежелательно.  |
| Различные web-приложения | виртуализация уровня ОС | Современная практика - разворачивать часто и много веб-приложений на одном хосте, при этом нужно обеспечить их изоляцию друг от друга. Виртуализация ОС подходит лучше всего, так свернуть приложение в контейнер и развернуть из него быстрей, чем делать это с виртуальными машинами с полноценной ОС и отдельным ядром. |
| Windows системы для использования бухгалтерским отделом | паравиртуализация | Виртуализация поможет системе быть более отказоустойчивой, из предложенных вариантов для Windows возможна только паравиртуализация. |
| Системы, выполняющие высокопроизводительные расчеты на GPU | виртуализация уровня ОС | виртуализация GPU может потребоваться в проектах с машинным обучением, из предложенных видов виртуализации для GPU возможна только виртуализация средствами ОС |

### Задача 3: Выберите подходящую систему управления виртуализацией для предложенного сценария. Детально опишите ваш выбор.

> 1. 100 виртуальных машин на базе Linux и Windows, общие задачи, нет особых требований. Преимущественно Windows based инфраструктура, требуется реализация программных балансировщиков нагрузки, репликации данных и автоматизированного механизма создания резервных копий.

Подойдут Hyper-V, vSphere: они оба хорошо поддерживают виртуальные машины с Windows и Linux, имеют встроенные перечисленные возможности (балансировка, репликация, бекапы) и могут работать в кластере гипервизоров, что необходимо для работы 100 виртуальных машин. 

> 2. Требуется наиболее производительное бесплатное open source решение для виртуализации небольшой (20-30 серверов) инфраструктуры на базе Linux и Windows виртуальных машин.

Лучше всего подойдёт Proxmox в режиме KVM: open source решение, хорошо поддерживает Windows гостей, имеет возможности по управлению сравнимые с платными гипервизорами.

> 3. Необходимо бесплатное, максимально совместимое и производительное решение для виртуализации Windows инфраструктуры.

Hyper-V Server, максимально совместим т.к. от Microsoft, полностью бесплатен.

> 4. Необходимо рабочее окружение для тестирования программного продукта на нескольких дистрибутивах Linux.

Оптимальней всего будет LXD, т.к. содержит огромную библиотеку с разными дистрибутивами в большом количестве конфигураций в виде контейнеров. Версия 4 позволяет запускать ещё и виртуальные машины, что позволит тестить даже ПО, требующее собственное полноценное ядро. 

### Задача 4: Опишите возможные проблемы и недостатки гетерогенной среды виртуализации (использования нескольких систем управления виртуализацией одновременно) и что необходимо сделать для минимизации этих рисков и проблем. Если бы у вас был выбор, то создавали бы вы гетерогенную среду или нет? Мотивируйте ваш ответ примерами.

Если я правильно понимаю, имеется в виду ситуация, когда используется несколько гипервизоров одного типа (например, VMWare ESXi и KVM), или примерно одного (например, Xen паравиртуализация и hardware assisted виртуализация с KVM или VMWare).
Основная проблема, из которой вытекает всё остальное - нужно в Н раз больше усилий на изучение и поддержку одного и того же.  
- Б**о**льшие расходы на штат инженеров, чтобы закрыть потребность в экспертизе по используемым технологиям
- Больше заморочек с мониторингом 
- Если требуется интегрировать гипервизор с какими-то внешними системами - нужно делать отдельно для каждой платформы
- В нужный момент может не оказаться специалистов по технологии, с которой возникли проблемы
- Скорей всего будет сложно выбирать железо: одни вендоры поддерживают одно, другие другое, нужно больше тратиться на резерв, сложно взаимно заменять аппаратные компоненты
- 

Решения мне видятся предельно простые: нанять больше людей, купить больше поддержки у вендоров, и/или использовать какую-то абстрагирующую прослойку вроде OpenStack, чтобы решить хотя бы задачи по интеграции и унификации управления. Использовать тот гипервизор, где у нас меньше экспертизы или специалистов, для менее критичных ресурсов. 

Лучшее решение, конечно, мигрировать на одну платформу, но полагаю это может быть не всегда возможно: всегда есть какое-то легаси, которое лучше не трогать без надобности, или раньше было дорогое и платное решение, теперь бюджет только на опенсорс, или какие-то административные ограничения и т.д. Либо мы работаем в датацентре и тогда, скорей всего, поддержку множества гипервизоров от нас будут ожидать клиенты.

Если бы я выбирал, то делал бы максимально единообразную систему с минимумом разнообразия используемых технологий в основе.

Конечно, если речь идёт о среде, где используются как виртуальные машины, так и контейнеры, то это "стандарт отрасли". Он несёт все минусы, которые я перечислил выше, но это параллельно развивающиеся технологии, имеющие свою нишу, и часто требуется знать и применять как минимум один гипервизор 1/2 уровня и какую-то технологию виртуализации.

</details>



### Курсовая работа по итогам модуля "DevOps и системное администрирование"

<details>

#### 1. Создайте виртуальную машину Linux.
```
% vagrant ssh
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-80-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Mon 06 Dec 2021 05:16:31 PM UTC

  System load:  1.93              Processes:             119
  Usage of /:   2.3% of 61.31GB   Users logged in:       0
  Memory usage: 15%               IPv4 address for eth0: 10.0.2.15
  Swap usage:   0%


This system is built by the Bento project by Chef Software
More information can be found at https://github.com/chef/bento
vagrant@vagrant:~$
```
#### 2. Установите ufw и разрешите к этой машине сессии на порты 22 и 443, при этом трафик на интерфейсе localhost (lo) должен ходить свободно на все порты.
```
vagrant@vagrant:~$ sudo ufw status
Status: inactive
vagrant@vagrant:~$ sudo ufw allow 22
Rules updated
Rules updated (v6)
vagrant@vagrant:~$ sudo ufw allow 443
Rules updated
Rules updated (v6)
vagrant@vagrant:~$ sudo ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
Firewall is active and enabled on system startup
vagrant@vagrant:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
443                        ALLOW       Anywhere
22 (v6)                    ALLOW       Anywhere (v6)
443 (v6)                   ALLOW       Anywhere (v6)
```
#### 3. Установите hashicorp vault (инструкция по ссылке).
```
vagrant@vagrant:~$ curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
OK
vagrant@vagrant:~$ sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
vagrant@vagrant:~$ sudo apt-get update && sudo apt-get install vault
vagrant@vagrant:~$ sudo vault
Usage: vault <command> [args]

Common commands:
    read        Read data and retrieves secrets
    write       Write data, configuration, and secrets
    delete      Delete secrets and configuration
    list        List data or secrets
    login       Authenticate locally
    agent       Start a Vault agent
    server      Start a Vault server
    status      Print seal and HA status
    unwrap      Unwrap a wrapped secret

Other commands:
    audit          Interact with audit devices
    auth           Interact with auth methods
    debug          Runs the debug command
    kv             Interact with Vault's Key-Value storage
    lease          Interact with leases
    monitor        Stream log messages from a Vault server
    namespace      Interact with namespaces
    operator       Perform operator-specific tasks
    path-help      Retrieve API help for paths
    plugin         Interact with Vault plugins and catalog
    policy         Interact with policies
    print          Prints runtime configurations
    secrets        Interact with secrets engines
    ssh            Initiate an SSH session
    token          Interact with tokens
```
#### 4. Создайте центр сертификации по инструкции (ссылка), и выпустите сертификат для использования его в настройке веб-сервера nginx (срок жизни сертификата - месяц).

Запуск Vault server в dev-режиме
```
vagrant@vagrant:~$ sudo vault server -dev -dev-root-token-id 2mFgnI7QiRtCfQT4ynGQUdKe4N
==> Vault server configuration:

             Api Address: http://127.0.0.1:8200
                     Cgo: disabled
         Cluster Address: https://127.0.0.1:8201
              Go Version: go1.17.2
              Listener 1: tcp (addr: "127.0.0.1:8200", cluster address: "127.0.0.1:8201", max_request_duration: "1m30s", max_request_size: "33554432", tls: "disabled")
               Log Level: info
                   Mlock: supported: true, enabled: false
           Recovery Mode: false
                 Storage: inmem
                 Version: Vault v1.9.0

==> Vault server started! Log data will stream in below:
....
```
```
root@vagrant:~# export VAULT_ADDR='http://127.0.0.1:8200'
root@vagrant:~# export VAULT_TOKEN=2mFgnI7QiRtCfQT4ynGQUdKe4N
```
```
root@vagrant:~# vault status
Key             Value
---             -----
Seal Type       shamir
Initialized     true
Sealed          false
Total Shares    1
Threshold       1
Version         1.9.0
Storage Type    inmem
Cluster Name    vault-cluster-d18425f4
Cluster ID      a492c217-c0f4-2411-7d10-0066ac1be454
HA Enabled      false
```
Создание Root CA и Intermediate CA
```
root@vagrant:~# vault secrets enable pki
Success! Enabled the pki secrets engine at: pki/

root@vagrant:~# vault secrets tune -max-lease-ttl=8760h pki
Success! Tuned the secrets engine at: pki/

root@vagrant:~# vault write -field=certificate pki/root/generate/internal common_name="example.com" ttl=87600h > CA_cert.crt

root@vagrant:~# vault write pki/config/urls issuing_certificates="http://127.0.0.1:8200/v1/pki/ca" crl_distribution_points="http://127.0.0.1:8200/v1/pki/crl"
Success! Data written to: pki/config/urls

root@vagrant:~# vault secrets enable -path=pki_int pki
Success! Enabled the pki secrets engine at: pki_int/

root@vagrant:~# vault secrets tune -max-lease-ttl=8760h pki_int
Success! Tuned the secrets engine at: pki_int/

root@vagrant:~# apt install jq

root@vagrant:~# vault write -format=json pki_int/intermediate/generate/internal common_name="example.com Intermediate Authority" | jq -r '.data.csr' > pki_intermediate.csr

root@vagrant:~# vault write -format=json pki/root/sign-intermediate csr=@pki_intermediate.csr format=pem_bundle ttl="8760h" | jq -r '.data.certificate' > intermediate.cert.pem

root@vagrant:~# vault write pki_int/intermediate/set-signed certificate=@intermediate.cert.pem
Success! Data written to: pki_int/intermediate/set-signed

root@vagrant:~# vault write pki_int/roles/example-dot-com allowed_domains="example.com" allow_subdomains=true max_ttl="4380h"
Success! Data written to: pki_int/roles/example-dot-com

root@vagrant:~# vault list pki_int/roles/
Keys
----
example-dot-com
```
Создание сертификатов для devops.example.com
```
root@vagrant:~# vault write -format=json pki_int/issue/example-dot-com common_name="devops.example.com" ttl=720h > devops.example.com.crt

root@vagrant:~# cat devops.example.com.crt
....
serial_number       40:fa:18:00:fb:7c:9b:97:95:50:10:da:2f:48:7f:f7:48:08:c1:4a

root@vagrant:~# cat devops.example.com.crt | jq -r .data.certificate > devops.example.com.crt.pem

root@vagrant:~# cat devops.example.com.crt | jq -r .data.issuing_ca >> devops.example.com.crt.pem

root@vagrant:~# cat devops.example.com.crt | jq -r .data.private_key > devops.example.com.crt.key
```
#### 5. Установите корневой сертификат созданного центра сертификации в доверенные в хостовой системе.
```
root@vagrant:~# ln -s /root/CA_cert.crt /usr/local/share/ca-certificates/CA_cert.crt
root@vagrant:~# update-ca-certificates
Updating certificates in /etc/ssl/certs...
1 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
```
#### 6. Установите nginx.
```
root@vagrant:~# apt install nginx

root@vagrant:~# systemctl status nginx
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2021-12-07 10:15:15 UTC; 11s ago
       Docs: man:nginx(8)
   Main PID: 14592 (nginx)
      Tasks: 3 (limit: 1071)
     Memory: 4.4M
     CGroup: /system.slice/nginx.service
             ├─14592 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
             ├─14593 nginx: worker process
             └─14594 nginx: worker process

Dec 07 10:15:15 vagrant systemd[1]: Starting A high performance web server and a reverse proxy server...
Dec 07 10:15:15 vagrant systemd[1]: Started A high performance web server and a reverse proxy server.

root@vagrant:~# nano /etc/hosts
127.0.0.1       localhost
127.0.1.1       vagrant.vm      vagrant
127.0.0.1       devops.example.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

root@vagrant:~# ping devops.example.com
PING devops.example.com (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.021 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.035 ms
^C
--- devops.example.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1031ms
rtt min/avg/max/mdev = 0.021/0.028/0.035/0.007 ms
```
#### 7. По инструкции (ссылка) настройте nginx на https, используя ранее подготовленный сертификат:
- можно использовать стандартную стартовую страницу nginx для демонстрации работы сервера;
- можно использовать и другой html файл, сделанный вами;
```
root@vagrant:~# nano /etc/nginx/sites-enabled/default
....
server {
....

        # SSL configuration
        #
        listen 443 ssl default_server;
        listen [::]:443 ssl default_server;
        ssl_certificate /root/devops.example.com.crt.pem;
        ssl_certificate_key /root/devops.example.com.crt.key;
....
root@vagrant:~# nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

root@vagrant:~# systemctl reload nginx
root@vagrant:~# root@vagrant:~# curl -I https://devops.example.com
HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Tue, 07 Dec 2021 19:22:40 GMT
Content-Type: text/html
Content-Length: 612
Last-Modified: Tue, 07 Dec 2021 19:19:05 GMT
Connection: keep-alive
ETag: "61afb3a9-264"
Accept-Ranges: bytes
```
#### 8. Откройте в браузере на хосте https адрес страницы, которую обслуживает сервер nginx.

![](pic/sert.png)
#### 9. Создайте скрипт, который будет генерировать новый сертификат в vault:
- генерируем новый сертификат так, чтобы не переписывать конфиг nginx;
- перезапускаем nginx для применения нового сертификата.
```
root@vagrant:~# nano sert.sh
#!/bin/bash
vault write -format=json pki_int/issue/example-dot-com common_name="devops.example.com" ttl=720h > /root/devops.example.com.crt
cat /root/devops.example.com.crt | jq -r .data.certificate > /root/devops.example.com.crt.pem
cat /root/devops.example.com.crt | jq -r .data.issuing_ca >> /root/devops.example.com.crt.pem
cat /root/devops.example.com.crt | jq -r .data.private_key > /root/devops.example.com.crt.key
systemctl reload nginx

root@vagrant:~# chmod ugo+x sert.sh
```

![](pic/sert_renew.png)
#### 10. Поместите скрипт в crontab, чтобы сертификат обновлялся какого-то числа каждого месяца в удобное для вас время.
```
root@vagrant:~# crontab -l
....
# m h  dom mon dow   command
0 0 7 * * /root/sert.sh
```

</details>

## Домашнее задание к занятию "3.8. Компьютерные сети, лекция 3"

### 1)
### route-views>show ip route 77.222.111.97
        Routing entry for 77.222.111.0/24
        Known via "bgp 6447", distance 20, metric 0
        Tag 6939, type external
        Last update from 64.71.137.241 3w2d ago
        Routing Descriptor Blocks:
        64.71.137.241, from 64.71.137.241, 3w2d ago
         * Route metric is 0, traffic share count is 1
           AS Hops 2
           Route tag 6939
           MPLS label: none
### route-views>show bgp 77.222.111.97
        BGP routing table entry for 77.222.111.0/24, version 1297188382
        Paths: (23 available, best #23, table default)
          Not advertised to any peer
          Refresh Epoch 1
          4901 6079 31133 8369
            162.250.137.254 from 162.250.137.254 (162.250.137.254)
              Origin incomplete, localpref 100, valid, external
              Community: 65000:10100 65000:10300 65000:10400
              path 7FE1279E3C68 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 3
          3303 50384 8369
            217.192.89.50 from 217.192.89.50 (138.187.128.158)
              Origin IGP, localpref 100, valid, external
              Community: 3303:1004 3303:1006 3303:1030 3303:1031 3303:3081 31210:50384 65005:10643
              path 7FE0F8E4EB30 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          7660 2516 12389 8369
            203.181.248.168 from 203.181.248.168 (203.181.248.168)
              Origin incomplete, localpref 100, valid, external
              Community: 2516:1050 7660:9003
              path 7FE108D72260 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          3267 31133 8369
            194.85.40.15 from 194.85.40.15 (185.141.126.1)
              Origin incomplete, metric 0, localpref 100, valid, external
              path 7FE04F2AB7E0 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          57866 9002 8369 8369 8369 8369 8369 8369
            37.139.139.17 from 37.139.139.17 (37.139.139.17)
              Origin IGP, metric 0, localpref 100, valid, external
              Community: 9002:0 9002:64667
              path 7FE045314970 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          7018 3356 3216 8369
            12.0.1.63 from 12.0.1.63 (12.0.1.63)
              Origin IGP, localpref 100, valid, external
              Community: 7018:5000 7018:37232
              path 7FE02DEC7B98 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          3333 31133 8369
            193.0.0.56 from 193.0.0.56 (193.0.0.56)
              Origin incomplete, localpref 100, valid, external
              path 7FE085A8A298 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          49788 12552 31133 8369
            91.218.184.60 from 91.218.184.60 (91.218.184.60)
              Origin incomplete, localpref 100, valid, external
              Community: 12552:12000 12552:12100 12552:12101 12552:22000
              Extended Community: 0x43:100:1
              path 7FE18D5CE4A8 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          20912 3257 12389 12389 12389 12389 8369
            212.66.96.126 from 212.66.96.126 (212.66.96.126)
              Origin IGP, localpref 100, valid, external
              Community: 3257:4000 3257:8921 3257:50001 3257:50110 3257:54600 3257:54601 20912:65004
              path 7FE099432CB0 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          8283 31133 8369
            94.142.247.3 from 94.142.247.3 (94.142.247.3)
              Origin incomplete, metric 0, localpref 100, valid, external
              Community: 8283:1 8283:101
              unknown transitive attribute: flag 0xE0 type 0x20 length 0x18
                value 0000 205B 0000 0000 0000 0001 0000 205B
                      0000 0005 0000 0001
              path 7FE0D4D350D0 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          3356 3216 8369
            4.68.4.46 from 4.68.4.46 (4.69.184.201)
              Origin IGP, metric 0, localpref 100, valid, external
              Community: 0:16509 3216:2001 3216:4474 3216:5130 3216:5650 3216:5680 3356:2 3356:22 3356:100 3356:123 3356:503 3356:903 3356:2067
              path 7FE176C5B888 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          1221 4637 12389 8369
            203.62.252.83 from 203.62.252.83 (203.62.252.83)
              Origin incomplete, localpref 100, valid, external
              path 7FE17A3099C8 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          2497 12389 8369
            202.232.0.2 from 202.232.0.2 (58.138.96.254)
              Origin incomplete, localpref 100, valid, external
              path 7FE0FAEC6450 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          852 31133 8369
            154.11.12.212 from 154.11.12.212 (96.1.209.43)
              Origin IGP, metric 0, localpref 100, valid, external
              path 7FE100A16F68 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          20130 6939 8369
            140.192.8.16 from 140.192.8.16 (140.192.8.16)
              Origin IGP, localpref 100, valid, external
              path 7FE1726E7D88 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          701 1273 3216 8369
            137.39.3.55 from 137.39.3.55 (137.39.3.55)
              Origin incomplete, localpref 100, valid, external
              path 7FE093950038 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          3257 12389 12389 12389 12389 8369
            89.149.178.10 from 89.149.178.10 (213.200.83.26)
              Origin IGP, metric 10, localpref 100, valid, external
              Community: 3257:4000 3257:8921 3257:50001 3257:50110 3257:54600 3257:54601
              path 7FE18A689C88 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          3549 3356 3216 8369
            208.51.134.254 from 208.51.134.254 (67.16.168.191)
              Origin IGP, metric 0, localpref 100, valid, external
              Community: 0:16509 3216:2001 3216:4474 3216:5130 3216:5650 3216:5680 3356:2 3356:22 3356:100 3356:123 3356:503 3356:903 3356:2067 3549:2581 3549:30840
              path 7FE11C0F9D20 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          53767 174 31133 8369
            162.251.163.2 from 162.251.163.2 (162.251.162.3)
              Origin incomplete, localpref 100, valid, external
              Community: 174:21101 174:22005 53767:5000
              path 7FE02C4F5178 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          101 3491 12389 8369
            209.124.176.223 from 209.124.176.223 (209.124.176.223)
              Origin incomplete, localpref 100, valid, external
              Community: 101:20300 101:22100 3491:400 3491:415 3491:9001 3491:9080 3491:9081 3491:9087 3491:62210 3491:62220
              path 7FE142FAC0C8 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          1351 6939 8369
            132.198.255.253 from 132.198.255.253 (132.198.255.253)
              Origin IGP, localpref 100, valid, external
              path 7FE042718CD0 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          3561 3910 3356 3216 8369
            206.24.210.80 from 206.24.210.80 (206.24.210.80)
              Origin IGP, localpref 100, valid, external
              path 7FE0D7CA4600 RPKI State not found
              rx pathid: 0, tx pathid: 0
          Refresh Epoch 1
          6939 8369
            64.71.137.241 from 64.71.137.241 (216.218.252.164)
              Origin IGP, localpref 100, valid, external, best
              path 7FE13C492C30 RPKI State not found
              rx pathid: 0, tx pathid: 0x0
### 2)
### root@vagrant:/etc/systemd/network# touch dummy0.netdev dummy0.network
### root@vagrant:/etc/systemd/network# cat dummy0.network
        [Match]
        Name=Dummy0
        [Network]
        Address=171.16.1.23 
        Mask=255.255.255.255
        Broadcast=172.16.1.255
### root@vagrant:/etc/systemd/network# cat dummy0.netdev
        [NetDev]
        Name=Dummy0
        Kind=dummy
### root@vagrant:/etc/systemd/network# sudo ip addr add 192.168.1.0/24 dev Dummy0
### root@vagrant:/etc/systemd/network# sudo ip addr add 192.168.2.0/24 dev Dummy0
### root@vagrant:/etc/systemd/network# ip ro sh
        default via 10.0.2.2 dev eth0 proto dhcp src 10.0.2.15 metric 100
        10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15
        10.0.2.2 dev eth0 proto dhcp scope link src 10.0.2.15 metric 100
        192.168.1.0/24 dev Dummy0 proto kernel scope link src 192.168.1.0
        192.168.2.0/24 dev Dummy0 proto kernel scope link src 192.168.2.0
root@vagrant:/etc/systemd/network#

### 3)
### root@vagrant:/etc/systemd/network# netstat -ntlp | grep LISTEN
        tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      1/init
        tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      614/systemd-resolve
        tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3638/sshd: /usr/sbi
        Init 1- загружает одно пользовательский вариант операционной системы
        Systemd-resolved — это сервис systemd для локального резолвинга DNS запросов
        sshd - это служба, принимающая запросы на соединения от клиентов
### 4) 
### root@vagrant:/etc/systemd/network# ss -ltupn
        Netid        State         Recv-Q        Send-Q                Local Address:Port               Peer Address:Port       Process
        udp          UNCONN        0             0                     127.0.0.53%lo:53                      0.0.0.0:*
         users:(("systemd-resolve",pid=614,fd=12))
        udp          UNCONN        0             0                    10.0.2.15%eth0:68                      0.0.0.0:*
         users:(("systemd-network",pid=12956,fd=22))
        udp          UNCONN        0             0                           0.0.0.0:111                     0.0.0.0:*
         users:(("rpcbind",pid=613,fd=5),("systemd",pid=1,fd=36))
            
        systemd-network - Набор утилит для запуска и управления всеми типами процессов и служб (а также устройствами, сокетами, точками монтирования, областью подкачки, модулями и пр.)
        rpcbind — демон, сопоставляющий универсальные адреса и номера программ RPC. Это сервер, преобразующий номера программ RPC в универсальные адреса
### 5) [Диаграмма](https://drive.google.com/file/d/1LDfictMoVuO8NDoPQf4LS57FrCSPpAfj/view?usp=sharing)
## Домашнее задание к занятию "3.7. Компьютерные сети, лекция 2"

### 1) ipconfig(windows) ip link(linux)
### 2) NDP (Neighbor Discovery Protocol)- протокол из набора протоколов TCP/IP
### пакеты iproute или iproute2 команда ip
## #3) VLAN
vlan с ID-100 для интерфейса eth0 with ID - 100 в Debian/Ubuntu Linux##
auto eth0.100
iface eth0.100 inet static
address 192.168.1.200
netmask 255.255.255.0
vlan-raw-device eth0
### 4)
Linux поддерживает несколько режимов агрегации интерфейсов:

0 (balance-rr) — round-robin распределение пакетов между интерфейсами. Обеспечивает отказоустойчивость и повышение пропускной способности.
1 (active-backup) — в каждый момент времени работает только один интерфейс, в случае его выхода из строя, mac-адрес назначается второму интерфейсу и трафик переключается на него.
2 (balance-xor) — обеспечивает балансировку между интерфейсами на основании MAC-адресов отправителя и получателя.
3 (broadcast) — отправляет пакеты через все интерфейсы одновременно, обеспечивает отказоустойчивость.
4 (802.3ad) — обеспечивает агрегацию на основании протокола 802.3ad.
5 (balance-tlb) — в этом режиме входящий трафик приходит только на один «активный» интерфейс, исходящий же распределяется по всем интерфейсам.
6 (balance-alb) — балансирует исходящий трафик как tlb, а так же входящий IPv4 трафик используя ARP.

Установим ifenslave:

root@localhost:~$ apt-get install ifenslave-2.6
конфиг /etc/network/interfaces примерно к такому виду:
auto bond0
iface bond0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        up /sbin/ifenslave bond0 eth0 eth1
        down /sbin/ifenslave -d bond0 eth0 eth1
Создаем файл /etc/modprobe.d/bonding.conf:

alias bond0 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200
Добавляем модуль bonding в /etc/modules:

root@localhost:~$ echo "bonding" >> /etc/modules

### 5)
1. 8
2. 32
=>
Network:   10.10.10.0/24
HostMin:   10.10.10.1
HostMax:   10.10.10.254
Broadcast: 10.10.10.255
Hosts/Net: 254                   Class A, Private Internet

1 Requested size: 6 hosts
Netmask:   255.255.255.248 = 29
Network:   10.10.10.0/29
HostMin:   10.10.10.1
HostMax:   10.10.10.6
Broadcast: 10.10.10.7
Hosts/Net: 6                     Class A, Private Internet

2 Requested size: 6 hosts
Netmask:   255.255.255.248 = 29
Network:   10.10.10.8/29
HostMin:   10.10.10.9
HostMax:   10.10.10.14
Broadcast: 10.10.10.15
Hosts/Net: 6                     Class A, Private Internet

3 Requested size: 6 hosts
Netmask:   255.255.255.248 = 29
Network:   10.10.10.16/29
HostMin:   10.10.10.17
HostMax:   10.10.10.22
Broadcast: 10.10.10.23
Hosts/Net: 6                     Class A, Private Internet

4 Requested size: 6 hosts
Netmask:   255.255.255.248 = 29
Network:   10.10.10.24/29
HostMin:   10.10.10.25
HostMax:   10.10.10.30
Broadcast: 10.10.10.31
Hosts/Net: 6                     Class A, Private Internet
...
32 Requested size: 6 hosts
Netmask:   255.255.255.248 = 29
Network:   10.10.10.248/29
HostMin:   10.10.10.249
HostMax:   10.10.10.254
Broadcast: 10.10.10.255
Hosts/Net: 6                     Class A, Private Internet


### 6) 100.64.0.0/10
### 7) 
1. sudo arp-scan --interface=eth0 --localnet
2. ip -s -s neigh flush all
3. arp -d [ip Адрес]

#
## Домашнее задание к занятию "3.6. Компьютерные сети, лекция 1"
### 1)
### vagrant@vagrant:~$ telnet stackoverflow.com 80
    Trying 151.101.65.69...
    Connected to stackoverflow.com.
    Escape character is '^]'.
    GET /questions HTTP/1.0
    HOST: stackoverflow.com

    HTTP/1.1 301 
    стандартный код ответа HTTP, получаемый в ответ от сервера в ситуации, когда запрошенный ресурс был на постоянной основе перемещён в новое месторасположение, и указывающий на то, что текущие ссылки, использующие данный URL, должны быть обновлены. Адрес нового месторасположения ресурса указывается в поле Location получаемого в ответ заголовка пакета протокола HTTP.

### 2) 

    Status Code: 200 
    успешный запрос. Если клиентом были запрошены какие-либо данные, то они находятся в заголовке и/или теле сообщения. Появился в HTTP/1.0.
    [https://ibb.co/SNPLTn4](https://ibb.co/SNPLTn4)
### 3) 
    77.222.121.62
### 4)
 1. Intersvyaz
 2. AS8369
### 5)
 ### vagrant@vagrant:~$ traceroute 8.8.8.8
    traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
    1  _gateway (10.0.2.2)  0.155 ms  0.122 ms  0.114 ms
    2  * * *
    3  * * *
### 6)
### vagrant@vagrant:~$ mtr 8.8.8.8

                                        My traceroute  [v0.93]
    vagrant (10.0.2.15)                                                                            2021-11-28T09:22:34+0000
    Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                                                               Packets               Pings
Host                                                                        Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. _gateway                                                                  0.0%     7    0.2   0.2   0.1   0.2   0.0
 2. ip-192-168-27-1.is74.loc                                                  0.0%     7    0.7   0.7   0.5   0.9   0.1
 3. 172.24.128.1                                                              0.0%     7    1.8   7.3   1.2  40.6  14.7
 4. 10.100.120.5                                                              0.0%     7    4.9   5.3   4.1   9.4   1.8
 5. 10.100.120.6                                                              0.0%     7    5.3   5.2   4.9   5.5   0.3
 6. 10.100.124.146                                                            0.0%     7    4.9   4.8   4.2   5.1   0.3
 7. 10.100.124.161                                                            0.0%     7    4.3   4.6   4.0   5.5   0.5
 8. msk-ix-gw1.google.com                                                     0.0%     7   31.4  30.9  30.4  31.5   0.5
 9. 108.170.250.51                                                           28.6%     7   33.2  32.9  32.0  33.3   0.6
 10. 142.251.49.158                                                           50.0%     7   68.5  52.0  43.7  68.5  14.3
 11. 108.170.235.204                                                           0.0%     7   48.4  49.3  48.0  51.7   1.2
 12. 216.239.42.23                                                             0.0%     7   47.5  48.6  46.2  59.2   4.7
 13. (waiting for reply)
 14. (waiting for reply)
 15. (waiting for reply)
 16. (waiting for reply)
 17. (waiting for reply)
 18. (waiting for reply)
 19. (waiting for reply)
 20. (waiting for reply)
 21. (waiting for reply)
 22. dns.google                                                               16.7%     6   45.0  46.9  44.9  48.5   1.8
### 7)
 ### vagrant@vagrant:~$ dig dns.google

    ;; QUESTION SECTION:
    ;dns.google.                    IN      A

    ;; ANSWER SECTION:
    dns.google.             874     IN      A       8.8.4.4
    dns.google.             874     IN      A       8.8.8.8
### 8) 
    4.4.8.8.in-addr.arpa    IN PTR    dns.google
    8.8.8.8.in-addr.arpa    IN PTR    dns.google
## Домашнее задание к занятию "3.5. Файловые системы"

## 1)   Изучил. Хорошее решение для использования в Торрентах.
## 2)   Так как hardlink это ссылка на тот же самый файл и имеет тот же inode то права будут одни и теже.
## 3)   
Выполнено:
    
    Device     Boot   Start     End Sectors  Size Id Type
    /dev/sdb1          2048 4196351 4194304    2G 83 Linux
    /dev/sdb2       4196352 5242879 1046528  511M 83 Linux  
## 4)

    Disk /dev/sdb: 2.51 GiB, 2684354560 bytes, 5242880 sectors
    Disk model: VBOX HARDDISK   
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0xb289fd48

    Device     Boot   Start     End Sectors  Size Id Type
    /dev/sdb1          2048 4196351 4194304    2G 83 Linux
    /dev/sdb2       4196352 5242879 1046528  511M 83 Linux


    Disk /dev/sdc: 2.51 GiB, 2684354560 bytes, 5242880 sectors
    Disk model: VBOX HARDDISK   
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0xb289fd48

    Device     Boot   Start     End Sectors  Size Id Type
    /dev/sdc1          2048 4196351 4194304    2G 83 Linux
    /dev/sdc2       4196352 5242879 1046528  511M 83 Linux
## 5)
### root@vagrant:/home/vagrant# sfdisk -d /dev/sdb|sfdisk --force /dev/sdc
    Checking that no-one is using this disk right now ... OK

    Disk /dev/sdc: 2.51 GiB, 2684354560 bytes, 5242880 sectors
    Disk model: VBOX HARDDISK
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes

    >>> Script header accepted.
    >>> Script header accepted.
    >>> Script header accepted.
    >>> Script header accepted.
    >>> Created a new DOS disklabel with disk identifier 0x9e1c2417.
    /dev/sdc1: Created a new partition 1 of type 'Linux' and of size 511 MiB.
    /dev/sdc2: Created a new partition 2 of type 'Linux' and of size 2 GiB.
    /dev/sdc3: Done.

    New situation:
    Disklabel type: dos
    Disk identifier: 0x9e1c2417

    Device     Boot   Start     End Sectors  Size Id Type
    /dev/sdc1       4196352 5242879 1046528  511M 83 Linux
    /dev/sdc2          2048 4196351 4194304    2G 83 Linux

    Partition table entries are not in disk order.

    The partition table has been altered.
    Calling ioctl() to re-read partition table.
    Syncing disks.
## 6)
### root@vagrant:/home/vagrant# mdadm --create --verbose /dev/md1 -l 1 -n 2 /dev/sd{b1,c1}
    mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
    mdadm: size set to 522240K
    Continue creating array?    n
    mdadm: create aborted.
    root@vagrant:/home/vagrant# mdadm --create --verbose /dev/md1 -l 1 -n 2 /dev/sd{b2,c2}
    mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
    mdadm: size set to 2094080K
    Continue creating array? y
    mdadm: Defaulting to version 1.2 metadata
    mdadm: array /dev/md1 started.
## 7)
### root@vagrant:/home/vagrant# mdadm --create --verbose /dev/md1 -l 1 -n 2 /dev/sd{b1,c1}
    mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
    mdadm: size set to 522240K
    Continue creating array? y
    mdadm: Fail create md1 when using /sys/module/md_mod/parameters/new_array
    mdadm: /dev/md1 is already in use.
## 8)
### root@vagrant:/home/vagrant# pvcreate /dev/md1 /dev/md0
    Physical volume "/dev/md1" successfully created.
    Physical volume "/dev/md0" successfully created.
## 9)
### root@vagrant:/home/vagrant# vgcreate vg1 /dev/md1 /dev/md0
    Volume group "vg1" successfully created
## 10)
### root@vagrant:/home/vagrant# lvcreate -L 100M vg1 /dev/md0
    Logical volume "lvol0" created.
### root@vagrant:/home/vagrant# vgs
    VG        #PV #LV #SN Attr   VSize   VFree
    vg1         2   1   0 wz--n-   2.49g 2.39g
    vgvagrant   1   2   0 wz--n- <63.50g    0
### root@vagrant:/home/vagrant# lvs
    LV     VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
    lvol0  vg1       -wi-a----- 100.00m
    root   vgvagrant -wi-ao---- <62.54g
    swap_1 vgvagrant -wi-ao---- 980.00m
## 11)
### root@vagrant:/home/vagrant# mkfs.ext4 /dev/vg1/lvol0
    mke2fs 1.45.5 (07-Jan-2020)
    Creating filesystem with 25600 4k blocks and 25600 inodes

    Allocating group tables: done
    Writing inode tables: done
    Creating journal (1024 blocks): done
    Writing superblocks and filesystem accounting information: done
## 12)
### root@vagrant:/home/vagrant# mkdir /tmp/new
### root@vagrant:/home/vagrant# mount /dev/vg1/lvol0 /tmp/new
## 13)
### root@vagrant:/home/vagrant# wget https://mirror.yandex.ru/ubuntu/ls-lR.gz -O /tmp/new/test.gz
    --2021-11-28 08:03:25--  https://mirror.yandex.ru/ubuntu/ls-lR.gz
    Resolving mirror.yandex.ru (mirror.yandex.ru)... 213.180.204.183, 2a02:6b8::183
    Connecting to mirror.yandex.ru (mirror.yandex.ru)|213.180.204.183|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 22540872 (21M) [application/octet-stream]
    Saving to: ‘/tmp/new/test.gz’
    /tmp/new/test.gz              100%[=================================================>]  21.50M  20.3MB/s    in 1.1s

    2021-11-28 08:03:27 (20.3 MB/s) - ‘/tmp/new/test.gz’ saved [22540872/22540872]
## 14)
### root@vagrant:/home/vagrant# lsblk
    NAME                 MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
    sda                    8:0    0   64G  0 disk
    ├─sda1                 8:1    0  512M  0 part  /boot/efi
    ├─sda2                 8:2    0    1K  0 part
    └─sda5                 8:5    0 63.5G  0 part
    ├─vgvagrant-root   253:0    0 62.6G  0 lvm   /
    └─vgvagrant-swap_1 253:1    0  980M  0 lvm   [SWAP]
    sdb                    8:16   0  2.5G  0 disk
    ├─sdb1                 8:17   0  511M  0 part
    │ └─md0                9:0    0  510M  0 raid1
    │   └─vg1-lvol0      253:2    0  100M  0 lvm   /tmp/new
    └─sdb2                 8:18   0    2G  0 part
    └─md1                9:1    0    2G  0 raid1
    sdc                    8:32   0  2.5G  0 disk
    ├─sdc1                 8:33   0  511M  0 part
    │ └─md0                9:0    0  510M  0 raid1
    │   └─vg1-lvol0      253:2    0  100M  0 lvm   /tmp/new
    └─sdc2                 8:34   0    2G  0 part
      └─md1                9:1    0    2G  0 raid1
## 15)
### root@vagrant:/home/vagrant# gzip -t /tmp/new/test.gz
### root@vagrant:/home/vagrant# echo $?
    0
## 16)
### root@vagrant:/home/vagrant# pvmove /dev/md0
    /dev/md0: Moved: 24.00%
    /dev/md0: Moved: 100.00%
### root@vagrant:/home/vagrant# lsblk
    NAME                 MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
    sda                    8:0    0   64G  0 disk
    ├─sda1                 8:1    0  512M  0 part  /boot/efi
    ├─sda2                 8:2    0    1K  0 part
    └─sda5                 8:5    0 63.5G  0 part
    ├─vgvagrant-root   253:0    0 62.6G  0 lvm   /
    └─vgvagrant-swap_1 253:1    0  980M  0 lvm   [SWAP]
    sdb                    8:16   0  2.5G  0 disk
    ├─sdb1                 8:17   0  511M  0 part
    │ └─md0                9:0    0  510M  0 raid1
    └─sdb2                 8:18   0    2G  0 part
    └─md1                9:1    0    2G  0 raid1
    └─vg1-lvol0      253:2    0  100M  0 lvm   /tmp/new
    sdc                    8:32   0  2.5G  0 disk
    ├─sdc1                 8:33   0  511M  0 part
    │ └─md0                9:0    0  510M  0 raid1
    └─sdc2                 8:34   0    2G  0 part
    └─md1                9:1    0    2G  0 raid1
    └─vg1-lvol0      253:2    0  100M  0 lvm   /tmp/new
## 17)
### root@vagrant:/home/vagrant# mdadm /dev/md1 --fail /dev/sdb2
    mdadm: set /dev/sdb2 faulty in /dev/md1
### root@vagrant:/home/vagrant# mdadm -D /dev/md1
    /dev/md1:
           Version : 1.2
     Creation Time : Sun Nov 28 07:55:36 2021
        Raid Level : raid1
        Array Size : 2094080 (2045.00 MiB 2144.34 MB)
     Used Dev Size : 2094080 (2045.00 MiB 2144.34 MB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

       Update Time : Sun Nov 28 08:06:59 2021
             State : clean, degraded
    Active Devices : 1
    Working Devices : 1
    Failed Devices : 1
    Spare Devices : 0

    Consistency Policy : resync

              Name : vagrant:1  (local to host vagrant)
              UUID : 3aa1bf02:e479477c:b97c6d7d:264ffc40
            Events : 19

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       1       8       34        1      active sync   /dev/sdc2

       0       8       18        -      faulty   /dev/sdb2
### root@vagrant:/home/vagrant# mdadm -D /dev/md1
    /dev/md1:
           Version : 1.2
     Creation Time : Sun Nov 28 07:55:36 2021
        Raid Level : raid1
        Array Size : 2094080 (2045.00 MiB 2144.34 MB)
     Used Dev Size : 2094080 (2045.00 MiB 2144.34 MB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

       Update Time : Sun Nov 28 08:06:59 2021
             State : clean, degraded
    Active Devices : 1
    Working Devices : 1
    Failed Devices : 1
    Spare Devices : 0

    Consistency Policy : resync

              Name : vagrant:1  (local to host vagrant)
              UUID : 3aa1bf02:e479477c:b97c6d7d:264ffc40
            Events : 19

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       1       8       34        1      active sync   /dev/sdc2

       0       8       18        -      faulty   /dev/sdb2
## 18)
### root@vagrant:/home/vagrant# dmesg |grep md1
    [  434.692857] md/raid1:md1: not clean -- starting background reconstruction
    [  434.692858] md/raid1:md1: active with 2 out of 2 mirrors
    [  434.692872] md1: detected capacity change from 0 to 2144337920
    [  434.692986] md: resync of RAID array md1
    [  444.922129] md: md1: resync done.
    [ 1116.711920] md/raid1:md1: Disk failure on sdb2, disabling device.
               md/raid1:md1: Operation continuing on 1 devices.
## 19)
### root@vagrant:/home/vagrant# gzip -t /tmp/new/test.gz
### root@vagrant:/home/vagrant# echo $?
    0
## 20) vagrant destroy
    default: Are you sure you want to destroy the 'default' VM? [y/N] y
    ==> default: Forcing shutdown of VM...
    ==> default: Destroying VM and associated drives...

## Домашнее задание к занятию "3.4. Операционные системы, лекция 2"
### 1)  Установлено, порт  9100 проброшен на хостовую машину
    Пример передачи параметров через файл cron:
    1 EnvironmentFile=-/etc/default/cron
    2 ExecStart=/usr/sbin/cron -f -P $EXTRA_OPTS




    Сервис стартует и перезапускается корректно
1. Проверка после перезапуска работы процесса
2. Остановка
3. Проверка работы процесса
4. Запуск процесса 
5. Проверка работы процесса

### vagrant@vagrant:~$ ps -e |grep node_exporter   
    1375 ?        00:00:00 node_exporter
### vagrant@vagrant:~$ systemctl stop node_exporter
    ==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
    Authentication is required to stop 'node_exporter.service'.
    Authenticating as: vagrant,,, (vagrant)
    Password: 
    ==== AUTHENTICATION COMPLETE ===
    vagrant@vagrant:~$ ps -e |grep node_exporter
    vagrant@vagrant:~$ systemctl start node_exporter
    ==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
    Authentication is required to start 'node_exporter.service'.
    Authenticating as: vagrant,,, (vagrant)
    Password: 
    ==== AUTHENTICATION COMPLETE ===
### vagrant@vagrant:~$ ps -e |grep node_exporter
    1420 ?        00:00:00 node_exporter
    vagrant@vagrant:~$ 


    Прописан конфигруационный файл:
    vagrant@vagrant:/etc/systemd/system$ cat /etc/systemd/system/node_exporter.service
    [Unit]
    Description=Node Exporter
 
    [Service]
    ExecStart=/opt/node_exporter/node_exporter
    EnvironmentFile=/etc/default/node_exporter
 
    [Install]
    WantedBy=default.target


    при перезапуске переменная окружения выставляется :
### vagrant@vagrant:/etc/systemd/system$ sudo cat /proc/1809/environ
    LANG=en_US.UTF-8LANGUAGE=en_US:PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
    INVOCATION_ID=0fcb24d52895405c875cbb9cbc28d3ffJOURNAL_STREAM=9:35758MYVAR=some_value
### 2) 
    CPU:
    node_cpu_seconds_total{cpu="0",mode="idle"} 2238.49
    node_cpu_seconds_total{cpu="0",mode="system"} 16.72
    node_cpu_seconds_total{cpu="0",mode="user"} 6.86
    process_cpu_seconds_total
    
    Memory:
    node_memory_MemAvailable_bytes 
    node_memory_MemFree_bytes
    
    Disk(если несколько дисков то для каждого):
    node_disk_io_time_seconds_total{device="sda"} 
    node_disk_read_bytes_total{device="sda"} 
    node_disk_read_time_seconds_total{device="sda"} 
    node_disk_write_time_seconds_total{device="sda"}
    
    Network(так же для каждого активного адаптера):
    node_network_receive_errs_total{device="eth0"} 
    node_network_receive_bytes_total{device="eth0"} 
    node_network_transmit_bytes_total{device="eth0"}
    node_network_transmit_errs_total{device="eth0"}
### 3)  
    информация с хостовой машины:
### $ sudo lsof -i :19999
    COMMAND   PID    USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
    netdata 50358 netdata    4u  IPv4 1003958      0t0  TCP localhost:19999 (LISTEN)
    sudo lsof -i :9999
    COMMAND     PID USER    FD   TYPE  DEVICE SIZE/OFF NODE NAME
    chrome     4089 oragons 80u  IPv4 1112886      0t0  TCP localhost:38598->localhost:9999 (ESTABLISHED)
    VBoxHeadl 52075 oragons 21u  IPv4 1053297      0t0  TCP *:9999 (LISTEN)
    VBoxHeadl 52075 oragons 30u  IPv4 1113792      0t0  TCP localhost:9999->localhost:38598 (ESTABLISHED)

    информация с vm машины:
### vagrant@vagrant:~$ sudo lsof -i :19999
    COMMAND  PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
    netdata 1895 netdata    4u  IPv4  30971      0t0  TCP *:19999 (LISTEN)
    netdata 1895 netdata   55u  IPv4  31861      0t0  TCP vagrant:19999->_gateway:38598 (ESTABLISHED)
### 4) 
    Судя по выводу dmesg да, причем даже тип ВМ, так как есть соответсвующая строка: 
### $ dmesg |grep virtualiz
    [    0.002836] CPU MTRRs all blank - virtualized system.
    [    0.074550] Booting paravirtualized kernel on KVM
    [    4.908209] systemd[1]: Detected virtualization oracle.
    Если сравнить с хостовой машиной то это становится очевидным :
### $ dmesg |grep virtualiz
    [    0.048461] Booting paravirtualized kernel on bare hardware
### 5) 
### vagrant@vagrant:~$ /sbin/sysctl -n fs.nr_open
    1048576

    Это максимальное число открытых дескрипторов для ядра (системы), для пользователя задать больше этого числа нельзя (если не менять). 
    Число задается кратное 1024, в данном случае =1024*1024. 

    Но макс.предел ОС можно посмотреть так :
### vagrant@vagrant:~$ cat /proc/sys/fs/file-max
    9223372036854775807
### vagrant@vagrant:~$ ulimit -Sn
    1024

    мягкий лимит (так же ulimit -n)на пользователя (может быть увеличен процессов в процессе работы)

### vagrant@vagrant:~$ ulimit -Hn
    1048576

### 6)
### root@vagrant:~# ps -e |grep sleep
    2020 pts/2    00:00:00 sleep
### root@vagrant:~# nsenter --target 2020 --pid --mount
### root@vagrant:/# ps
    PID TTY          TIME CMD
    2986 pts/0    00:00:00 bash
    3110 pts/0    00:00:00 ps
### 7) 
    Из предыдущих лекций ясно что это функция внутри "{}", судя по всему с именем ":" , которая после опредения в строке запускает саму себя.

    А функционал этот:
    [ 3099.973235] cgroup: fork rejected by pids controller in /user.slice/user-1000.slice/session-4.scope
    [ 3103.171819] cgroup: fork rejected by pids controller in /user.slice/user-1000.slice/session-11.scope

    Судя по всему, система на основании этих файлов в пользовательской зоне ресурсов имеет определенное ограничение на создаваемые ресурси 
    и соответсвенно при превышении начинает блокировать создание числа 

    Если установить ulimit -u 50 - число процессов будет ограниченно 50 для пользоователя. 
## Домашнее задание к занятию "3.3. Операционные системы, лекция 1"
    

### 1) системный вызов команды CD -> chdir("/tmp") в нашем случае. 
### 2)  Файл базы типов - /usr/share/misc/magic.mgc
### в тексте это: openat(AT_FDCWD, "/usr/share/misc/magic.mgc", O_RDONLY) = 3
### 3)  vagrant@vagrant:~$ lsof -p 1126
...
vi      1126 vagrant    4u   REG  253,0    12288  526898 /home/vagrant/.tst_bash.swp (deleted)
### vagrant@vagrant:~$ echo '' >/proc/1126/fd/4
где 1126 - PID процесса vi
4 - дескриптор файла , который предварительно удалил. 
### 4) "Зомби" процессы, в отличии от "сирот" освобождают свои ресурсы, но не освобождают запись в таблице процессов. 
### запись освободиться при вызове wait() родительским процессом.
### 5) vagrant@vagrant:~sudo -i
### root@vagrant:~# dpkg -L bpfcc-tools | grep sbin/opensnoop
### /usr/sbin/opensnoop-bpfcc
### root@vagrant:~# /usr/sbin/opensnoop-bpfcc
PID    COMM               FD ERR PATH
766    vminfo              6   0 /var/run/utmp
562    dbus-daemon        -1   2 /usr/local/share/dbus-1/system-services
562    dbus-daemon        18   0 /usr/share/dbus-1/system-services
562    dbus-daemon        -1   2 /lib/dbus-1/system-services
562    dbus-daemon        18   0 /var/lib/snapd/dbus-1/system-services/
### 7) системный вызов uname()
Цитата :
     Part of the utsname information is also accessible  via  /proc/sys/ker‐
       nel/{ostype, hostname, osrelease, version, domainname}.
### 8)
&& -  условный оператор, 
а ;  - разделитель последовательных команд

set -e - прерывает сессию при любом ненулевом значении исполняемых команд в конвеере кроме последней.
в случае &&  вместе с set -e- вероятно не имеет смысла, так как при ошибке , выполнение команд прекратиться. 
### 9)
Самые частые:
S*(S,S+,Ss,Ssl,Ss+) - Процессы ожидающие завершения (спящие с прерыванием "сна")
I*(I,I<) - фоновые(бездействующие) процессы ядра

## Домашнее задание к занятию "3.2. Работа в терминале, лекция 2"
### 1) Это команда встройенная.
### Встроенная, потому что, работать внутри сессии терминала логичнее менять указатель на текущую дерикторию внутренней функцией, 
### Если использовать внешний вызов, то он будет работать со своим окружением, и менять  текущий каталог внутри своего окружения, а на вызвовший shell влиять не будет. 
### 2) vagrant@vagrant:~$ cat tst_bash
###if [[ -d /tmp ]];
sdgsdfgfd
sdgsdfgfghdgfd
123
### vagrant@vagrant:~$ grep 123 tst_bash -c
### 1
### vagrant@vagrant:~$ grep 123 tst_bash |wc -l
### 1
### 3) pstree -p 
### systemd(1)─┬─VBoxService(833)─┬─{VBoxService}(835)  
### 4) ls -l \root 2>/dev/pts/1
### 5) vagrant@vagrant:~$ cat tst_bash if [[ -d /tmp ]];
sdgsdfgfd
sdgsdfgfghdgfd
123
new line
11111111
### vagrant@vagrant:~$ cat tst_bash_out
cat: tst_bash_out: No such file or directory 
### vagrant@vagrant:~$ cat <tst_bash >tst_bash_out
### vagrant@vagrant:~$ cat tst_bash_out if [[ -d /tmp ]];
sdgsdfgfd
sdgsdfgfghdgfd
123
new line
11111111

### 6) Вывести полуится при использовании перенаправлении вывода: tty/dev/pts/3
### vagrant@vagrant:~$ echo Hello from pts3 to tty3 >/dev/tty3
### 7) bash 5>&1 - Создаст дескриптор с 5 и перенатправит его в stdout
### echo netology > /proc/$$/fd/5 - выведет в дескриптор "5", который был пернеаправлен в stdout
### 8) vagrant@vagrant:~$ ls -l /root 9>&2 2>&1 1>&9 |grep denied -c
9>&2 - новый дескриптор перенаправили в stderr
2>&1 - stderr перенаправили в stdout 
1>&9 - stdout - перенаправили в в новый дескриптор
### 9) 
Будут выведены переменные окружения:
можно получить тоже самое (только с разделением по переменным по строкам):
printenv
env
### 10
/proc/<PID>/cmdline - полный путь до исполняемого файла процесса [PID]  (строка 231)
/proc/<PID>/exe - содержит ссылку до файла запущенного для процесса [PID], 
                        cat выведет содержимое запущенного файла, 
                        запуск этого файла,  запустит еще одну копию самого файла  (строка 285)
### 11) SSE 4.2
### 12)  
при подключении ожидается пользователь, а не другой процесс, и нет локального tty в данный момент. 
для запуска можно добавить -t - , и команда исполняется c принудительным созданием псевдотерминала
### 13)
При первых запусках ругался на права, 10-patrace.conf
после установки заначения  kernel.yama.ptrace_scope = 0
после чего процесс был перехвачен в screen, и продолжил работу после закрытия терминала. 
единственное в pstree процесс не отображался, точнее оботражался в виде процесса reptyr. не сразу сообразил что это то, что нужно 
### 14)
команда tee делает вывод одновременно и в файл, указаный в качестве параметра, и в stdout, 
в данном примере команда получает вывод из stdin, перенаправленный через pipe от stdout команды echo
и так как команда запущена от sudo , соотвественно имеет права на запись в файл

## Домашнее задание к занятию "3.1. Работа в терминале, лекция 1"
    

### 1) 
####    Оперативная память: 1024МБ
####    Количество выделеных ядер процессора : 2
####    Колличество выделеной видеопамяти: 4мб
### 2)  Для изменения выделеных рессурсов необходимо выключить VM и через меню НАСТОРИТЬ -> СИСТЕМА  в соответсвующем пункте выбрать тот рессурс который необходимо добавить
### 3)  
#### 1.HISTSIZE  862 line
#### 2.  не сохранять команды начинающиеся с пробела и не сохранять команду, если такая уже имеется в истории
### 4) {} - зарезервированные слова, список, в т.ч. список команд команд в отличии от "(...)" исполнятся в текущем инстансе,используется в различных условных циклах, условных операторах, или ограничивает тело функции,В командах выполняет подстановку элементов из списка , если упрощенно то  цикличное выполнение команд с подстановкой например mkdir ./DIR_{A..Z} - создаст каталоги сименами DIR_A, DIR_B и т.д. до DIR_Z строка 343
### 5) touch {000001..100000}.txt - создаст в текущей директории соответсвющее число фалов
###  300000 - создать не удасться, это слишком дилинный список аргументов, максимальное число получил экспериментально - 110188
### 6) проверяет условие у -d /tmp и возвращает ее статус (0 или 1), наличие катаолга /tmp
### 7) 
    vagrant@vagrant:~$ mkdir /tmp/new_path_dir/
    vagrant@vagrant:~$ cp /bin/bash /tmp/new_path_dir/
    vagrant@vagrant:~$ type -a bash
    bash is /usr/bin/bash
    bash is /bin/bash
    vagrant@vagrant:~$ PATH=/tmp/new_path_dir/:$PATH
    vagrant@vagrant:~$ type -a bash
    bash is /tmp/new_path_dir/bash
    bash is /usr/bin/bash
    bash is /bin/bash
### 8) at - команда запускается в указанное время (в параметре)
### batch - запускается когда уровень загрузки системы снизится ниже 1.5.

# Домашнее задание к занятию «2.4. Инструменты Git»

### 1)   git show aefea
### commit aefead2207ef7e2aa5dc81a34aedf0cad4c32545
### 2)   $ git show 85024
### commit 85024d3100126de36331c6982bfaac02cdab9e76 (tag: v0.12.23)
### 3)   $ git show --pretty=format:' %P' b8d720 : 56cd7859e05c36c06b56d013b55a252d0bb7e158 9ea88f22fc6269854151c571162c5bcf958bee2b

### 4)   $ git log  v0.12.23..v0.12.24  --oneline
   #### 1.b14b74c49 [Website] vmc provider links
   #### 2.3f235065b Update CHANGELOG.md
   #### 3.6ae64e247 registry: Fix panic when server is unreachable
   #### 4.5c619ca1b website: Remove links to the getting started guide's old location
   #### 5.06275647e Update CHANGELOG.md
   #### 6.d5f9411f5 command: Fix bug when using terraform login on Windows
   #### 7.4b6d06cc5 Update CHANGELOG.md
   #### 8.dd01a3507 Update CHANGELOG.md
   #### 9.225466bc3 Cleanup after v0.12.23 release
### 5)   git log -S'func providerSource' --oneline
### 5af1e6234 main: Honor explicit provider_installation CLI config when present
### 8c928e835 main: Consult local directories as potential mirrors of providers


### 6)   git grep 'func globalPluginDirs'
### plugins.go:func globalPluginDirs() []string {
### git log -L :'func globalPluginDirs':plugins.go --oneline
### 7)  git log -S'func synchronizedWriters' --pretty=format:'%h - %an %ae'
### 5ac311e2a - Martin Atkins mart@degeneration.co.uk



## Будут проигнорированны файлы :
### 1)типа: tfvars которые могут содержат конфиденциальные данные, такие как пароль, секретные ключи и другие секреты
### 2))типа: override.tf, override.tf.json и файлы содержашие в названии _override.tf, _override.tf.json
### 3)типа: .terraformrc и с именем terraform.rc
