# linux_dz
Задание 1
Назовите по два DEB и RPM дистрибутива Linux

ответ:
DEB: Ubuntu, Kali Linux
RPM: Fedora, Cent OS

Задание 2
Объясните, что делает команда:
ps -aux | grep root | wc -l >> root

ответ:
команда ps выведет все процессы по условию aux, grep выберет процессы запущенные под root, wc -l подсчитает количество строк, >> root добавит значение в конец файла root (если файл не существует, он будет создан)

Задание 3
Напишите команду, которая выводит все запущенные процессы пользователя root в файл "user_root_ps"

ответ:
ps aux | grep root >> user_root_ps

Задание 4
В лекции была упомянута одна команда для получения информации о нагрузке на компьютер и в частности на ОЗУ.
Ее вывод выглядит вот так:
![image](https://user-images.githubusercontent.com/101703961/168033761-aa5f5e85-cea7-4a57-b652-666d893cb724.png)
Как называется эта команда? Что такое si и so в примере на картинке?

ответ:
это утилита vmstat - показывает работу компьютера (информацию о процессах, активности процессора, памяти и т.д.). Была вызвана командой vmstat -a. 
si - это swap in. Объем памяти, выгруженный с диска.
so - это swap out. Объем памяти, перенесенный на диск.

Задание 5
Приведите 3 команды, которые выведут на экран следующее:

Архитектуру ПК
Модель процессора
Количество памяти, которая уже не используется процессами, но еще остается в памяти(ключевое слово - inactive).
Примечание: при выполнении задания предполагается использование конструкции "{команда} | grep {параметр для фильтрации вывода}" в каталоге /proc

ответ:
1. lscpu | grep Architecture
2. cat /proc/cpuinfo | grep model name
3. cat /proc/meminfo | grep Inactive

Задание 6
ответ:

Задание 7
ответ:

Задание 8
Влияет ли количество операций ввода-вывода HDD диска на параметр load average?

ответ:
load average - это критически важная для индустрии метрика, отражает среднее значение нагрузки системы по 3м параметрам: жесткий диск, память, процессор по состоянию на 1, 5, 15 минут назад до текущего времени.
Операции ввода-вывода HDD несомненно повлияют на параметр load average

Задание 9
Чем hardlink отличается от softlink?

ответ:
Hardlink - по сути тот же файл, на который идет ссылка, только с другим именем. Если сравним их inode-номер, он будет общим. Счетчик ссылок при этом будет = 2.
Symlink (она же soft) - создает новый объект файловой системы, который указывает на уже существующий. Перед правами доступа у такой ссылки в атрибуте будет стоять буква l. Если сравним их inode-номер,они будут разными, т.к. файловая система воспринимает их как 2 независимых файла.

Ключевые различия:
1. Hardlink не может указывать на файл в другой файловой системе (так как inode может принадлежать только одной ФС), а Symlink – может
2. При редактировании файла-ссылки в случае с hardlink – изменятся оба файла, так как это один и тот же объект, а в случае с symlink – можно изменять его имя, атрибуты, направить его на другой файл и при этом оригинальный файл не будет затронут.(нюанс: если открыть файл симлинка для редактирования – то будет изменен оригинальный файл, т.к. по сути мы откроем для редактирования именно его)
3. Hardlink  не может указывать на на каталог

Задание 10
Как посмотреть количество inodes?

ответ: 
командой df -i

Задание 11
При каких событиях выполнение процесса переходит в режим ядра в Linux?

ответ: 
Существуют всего три события, при которых выполнение процесса переходит в режим ядра: аппаратные прерывания, особые ситуации, системные вызовы. Во всех случаях ядро Linux получает управление и вызывает соответствующую системную процедуру для обработки события

Задание 12
ответ:

Задание 13
ответ:

Задание 14
Существует такой вид виртуализации как контейнеризация: контейнеры создаются на уровне ОС и работают в изолированных пространствах.
Вопрос: что произойдет, если в хостовой ОС установлен upstart или systemV, а в запущенном контейнере - systemd?

ответ:
Это для меня сложный вопрос, нет практического навыка. Но я так понимаю, конфликтов быть не должно, если ОС на хосте и в контейнере совпадают, а при инициализации будет ориентироваться на systemd в контейнере.
