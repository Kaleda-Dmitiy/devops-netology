# devops-netology_Dmitriy-Kaleda

## Домашнее задание к занятию "3.4. Операционные системы, лекция 2"
### 1)  Установлено, порт  9100 проброшен на хостовую машину

Сервис стартует и перезапускается корректно
1.Проверка после перезапуска работы процесса
2. Остановка
3. Проверка работы процесса
4. Запуск процесса 
5. Проверка работы процесса

vagrant@vagrant:~$ ps -e |grep node_exporter   
   1375 ?        00:00:00 node_exporter
vagrant@vagrant:~$ systemctl stop node_exporter
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
vagrant@vagrant:~$ ps -e |grep node_exporter
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
vagrant@vagrant:/etc/systemd/system$ sudo cat /proc/1809/environ
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
$ sudo lsof -i :19999
COMMAND   PID    USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
netdata 50358 netdata    4u  IPv4 1003958      0t0  TCP localhost:19999 (LISTEN)
 sudo lsof -i :9999
COMMAND     PID USER    FD   TYPE  DEVICE SIZE/OFF NODE NAME
chrome     4089 oragons 80u  IPv4 1112886      0t0  TCP localhost:38598->localhost:9999 (ESTABLISHED)
VBoxHeadl 52075 oragons 21u  IPv4 1053297      0t0  TCP *:9999 (LISTEN)
VBoxHeadl 52075 oragons 30u  IPv4 1113792      0t0  TCP localhost:9999->localhost:38598 (ESTABLISHED)

информация с vm машины:
vagrant@vagrant:~$ sudo lsof -i :19999
COMMAND  PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
netdata 1895 netdata    4u  IPv4  30971      0t0  TCP *:19999 (LISTEN)
netdata 1895 netdata   55u  IPv4  31861      0t0  TCP vagrant:19999->_gateway:38598 (ESTABLISHED)
### 4) 
Судя по выводу dmesg да, причем даже тип ВМ, так как есть соответсвующая строка: 
$ dmesg |grep virtualiz
[    0.002836] CPU MTRRs all blank - virtualized system.
[    0.074550] Booting paravirtualized kernel on KVM
[    4.908209] systemd[1]: Detected virtualization oracle.
Если сравнить с хостовой машиной то это становится очевидным :
$ dmesg |grep virtualiz
[    0.048461] Booting paravirtualized kernel on bare hardware
### 5) 
vagrant@vagrant:~$ /sbin/sysctl -n fs.nr_open
1048576

Это максимальное число открытых дескрипторов для ядра (системы), для пользователя задать больше этого числа нельзя (если не менять). 
Число задается кратное 1024, в данном случае =1024*1024. 

Но макс.предел ОС можно посмотреть так :
vagrant@vagrant:~$ cat /proc/sys/fs/file-max
9223372036854775807
vagrant@vagrant:~$ ulimit -Sn
1024

мягкий лимит (так же ulimit -n)на пользователя (может быть увеличен процессов в процессе работы)

vagrant@vagrant:~$ ulimit -Hn
1048576

### 6)
root@vagrant:~# ps -e |grep sleep
   2020 pts/2    00:00:00 sleep
root@vagrant:~# nsenter --target 2020 --pid --mount
root@vagrant:/# ps
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

##Домашнее задание к занятию "3.2. Работа в терминале, лекция 2"
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
