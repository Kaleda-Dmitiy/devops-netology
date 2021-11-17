# devops-netology_Dmitriy-Kaleda
# Домашнее задание к занятию "3.1. Работа в терминале, лекция 1"
    

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
