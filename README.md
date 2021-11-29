# devops-netology_Dmitriy-Kaleda
## МЕНЮ
##  [Домашнее задание к занятию "3.7. Компьютерные сети, лекция 2"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-37-компьютерные-сети-лекция-2)
##  [Домашнее задание к занятию "3.6. Компьютерные сети, лекция 1"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-36-компьютерные-сети-лекция-1)
##  [Домашнее задание к занятию "3.5. Файловые системы"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-35-файловые-системы)
##  [Домашнее задание к занятию "3.4. Операционные системы, лекция 2"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-34-операционные-системы-лекция-2)
##  [Домашнее задание к занятию "3.2. Работа в терминале, лекция 2"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-32-работа-в-терминале-лекция-2-1)
##  [Домашнее задание к занятию "3.1. Работа в терминале, лекция 1"](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-31-работа-в-терминале-лекция-1)
##  [Домашнее задание к занятию «2.4. Инструменты Git»](https://github.com/Kaleda-Dmitiy/devops-netology#домашнее-задание-к-занятию-24-инструменты-git)

##
##
##
##
##
##
##

## Домашнее задание к занятию "3.7. Компьютерные сети, лекция 2"

### 1) ipconfig
### 2) NDP (Neighbor Discovery Protocol)- протокол из набора протоколов TCP/IP
## пакеты iproute или iproute2 команда ip
## 3) VLAN
vlan с ID-100 для интерфейса eth0 with ID - 100 в Debian/Ubuntu Linux##
auto eth0.100
iface eth0.100 inet static
address 192.168.1.200
netmask 255.255.255.0
vlan-raw-device eth0
## 4)
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

## 5)
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


### 6) 172.32.0.0/26
### 7) 
1. sudo arp-scan --interface=eth0 --localnet
2. ip -s -s neigh flush all
3. arp -d [ip Адрес]
## Домашнее задание к занятию "3.6. Компьютерные сети, лекция 1"
### 1)
vagrant@vagrant:~$ telnet stackoverflow.com 80
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
https://ibb.co/SNPLTn4
### 3) 
77.222.121.62
### 4)
 1. Intersvyaz
 2. AS8369
### 5)
 vagrant@vagrant:~$ traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  _gateway (10.0.2.2)  0.155 ms  0.122 ms  0.114 ms
 2  * * *
 3  * * *
### 6)
vagrant@vagrant:~$ mtr 8.8.8.8

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
  vagrant@vagrant:~$ dig dns.google

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
root@vagrant:/home/vagrant# sfdisk -d /dev/sdb|sfdisk --force /dev/sdc
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
root@vagrant:/home/vagrant# mdadm --create --verbose /dev/md1 -l 1 -n 2 /dev/sd{b1,c1}
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: size set to 522240K
Continue creating array? n
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
root@vagrant:/home/vagrant# mdadm --create --verbose /dev/md1 -l 1 -n 2 /dev/sd{b1,c1}
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
root@vagrant:/home/vagrant# pvcreate /dev/md1 /dev/md0
  Physical volume "/dev/md1" successfully created.
  Physical volume "/dev/md0" successfully created.
## 9)
root@vagrant:/home/vagrant# vgcreate vg1 /dev/md1 /dev/md0
  Volume group "vg1" successfully created
## 10)
root@vagrant:/home/vagrant# lvcreate -L 100M vg1 /dev/md0
  Logical volume "lvol0" created.
root@vagrant:/home/vagrant# vgs
  VG        #PV #LV #SN Attr   VSize   VFree
  vg1         2   1   0 wz--n-   2.49g 2.39g
  vgvagrant   1   2   0 wz--n- <63.50g    0
root@vagrant:/home/vagrant# lvs
  LV     VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lvol0  vg1       -wi-a----- 100.00m
  root   vgvagrant -wi-ao---- <62.54g
  swap_1 vgvagrant -wi-ao---- 980.00m
## 11)
root@vagrant:/home/vagrant# mkfs.ext4 /dev/vg1/lvol0
mke2fs 1.45.5 (07-Jan-2020)
Creating filesystem with 25600 4k blocks and 25600 inodes

Allocating group tables: done
Writing inode tables: done
Creating journal (1024 blocks): done
Writing superblocks and filesystem accounting information: done
## 12)
root@vagrant:/home/vagrant# mkdir /tmp/new
root@vagrant:/home/vagrant# mount /dev/vg1/lvol0 /tmp/new
## 13)
root@vagrant:/home/vagrant# wget https://mirror.yandex.ru/ubuntu/ls-lR.gz -O /tmp/new/test.gz
--2021-11-28 08:03:25--  https://mirror.yandex.ru/ubuntu/ls-lR.gz
Resolving mirror.yandex.ru (mirror.yandex.ru)... 213.180.204.183, 2a02:6b8::183
Connecting to mirror.yandex.ru (mirror.yandex.ru)|213.180.204.183|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 22540872 (21M) [application/octet-stream]
Saving to: ‘/tmp/new/test.gz’

/tmp/new/test.gz              100%[=================================================>]  21.50M  20.3MB/s    in 1.1s

2021-11-28 08:03:27 (20.3 MB/s) - ‘/tmp/new/test.gz’ saved [22540872/22540872]
## 14)
root@vagrant:/home/vagrant# lsblk
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
root@vagrant:/home/vagrant# gzip -t /tmp/new/test.gz
root@vagrant:/home/vagrant# echo $?
0
## 16)
root@vagrant:/home/vagrant# pvmove /dev/md0
  /dev/md0: Moved: 24.00%
  /dev/md0: Moved: 100.00%
root@vagrant:/home/vagrant# lsblk
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
root@vagrant:/home/vagrant# mdadm /dev/md1 --fail /dev/sdb2
mdadm: set /dev/sdb2 faulty in /dev/md1
root@vagrant:/home/vagrant# mdadm -D /dev/md1
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
root@vagrant:/home/vagrant# mdadm -D /dev/md1
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
root@vagrant:/home/vagrant# dmesg |grep md1
[  434.692857] md/raid1:md1: not clean -- starting background reconstruction
[  434.692858] md/raid1:md1: active with 2 out of 2 mirrors
[  434.692872] md1: detected capacity change from 0 to 2144337920
[  434.692986] md: resync of RAID array md1
[  444.922129] md: md1: resync done.
[ 1116.711920] md/raid1:md1: Disk failure on sdb2, disabling device.
               md/raid1:md1: Operation continuing on 1 devices.
## 19)
root@vagrant:/home/vagrant# gzip -t /tmp/new/test.gz
root@vagrant:/home/vagrant# echo $?
0
## 20) vagrant destroy
    default: Are you sure you want to destroy the 'default' VM? [y/N] y
==> default: Forcing shutdown of VM...
==> default: Destroying VM and associated drives...

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
