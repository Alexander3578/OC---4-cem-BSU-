Задание1 (Source.cpp) 
-
Написать программу для консольного процесса, который состоит из двух потоков: main и worker.

Поток main должен выполнить следующие действия:
1. Создать массив(тип массива согласно варианту) чисел, размерность и элементы которого вводятся с
консоли( или сгенерировать случайно).
2. Для некоторых вариантов ввести дополнительные парамтры : k,a,b, х.
3. Ввести время для остановки и запуска потока worker.
4. Создать поток worker, передать в поток данные: размер маcсива, масив и т.д.
5. Приостановить поток worker(SuspendThread), затем через некоторое время снова запустить поток.
6. Уметь создавать поток командой _beginthreadex
7. Дождаться завершения потока worker.
8. Вывести на консоль результат работы потока worker
9. Завершить работу.
 
Поток worker должен выполнить следующую работу
-
Найти сумму квадратов элементов в массиве и вывести. Тип элементов – long. После каждой итерации цикла -
«спать» 12 миллисекунд. Завершить свою работу.

Задание 2 (Source_Child.cpp и Source_Parent.cpp) 
-
Написать программы двух консольных процессов Parent и Child, которые выполняют следующие действия.
Два проекта (процессы) хранить в одном Solution (Решении)!
В Solution (Решениии) настроить, что бы .exe файлы лежали в одном Debug!

Процесс Parent: 
-
Ввести размер массива, ввести элементы массива;
Ввести необходимые дополнительные значения согласно варианту (A,B,X,K);
Установить высоту буфера для Сhild.
Запускает дочерний процесс Child, которому через командную строку передается информация об
размерности массива, элементах и т.д. 

Процесс Child:
-
Поиск в массиве элементов >A (разместить их в массиве слева, остальные элементы массива -
заполнить нулями). Полученный массив вывести. Тип элементов - вещественные числа

Задание 3 (ОС-3.срр)
-
Написать программу для консольного процесса, который состоит из трёх потоков: main , work, и SumElement
 Объекты синхронизации :
 1. Событие1 (с ручным сбросом) – в потоке work устанавливает сигнал для потока main (для вывода массива) и
для потока SumElement ( сигнализирует о начале суммирования).
 2. Событие2 (с автоматическим сбросом) – в потоке work устанавливает сигнал для потока main (для вывода
массива).

Критическая секция- синхронизация SumElement и потока main (вывод результа SumElement);
Поток main должен выполнить следующие действия:
-
1. Инициализировать необходимые события и критические секции.
2. создать массив, размерность и элементы которого вводятся пользователем с консоли;
3. вывести размерность и элементы исходного массива на консоль;
4. запустить поток work;
5. запустить поток SumElement;
6. получить от потока work сообщение о начале работы потока SumElemen (использовать событие с ручным
бросом).
7. выводить элементы массива (до K2);
8. вывести на экран результат работы потока SumElement;
9. выводить элементы массива (c K2);
10. выводить элементы массива (c K2);

Поток work должен выполнить следующие действия:
-
1. Запросить у пользователя временной интервал, требуемый для отдыха после подготовки одного элемента в
массиве;
2. Поиск в массиве элементов >A (разместить их в массиве слева, остальные элементы массива - заполнить
нулями). Элементы - целые числа без знака. Число A ввести в потоке main.
3. после каждого готового элемента отдыхать в течение заданного интервала времени;
4. известить поток SumElement и поток main о начале суммирования (момент запуска произойдёт после того,
будет сформировано К2 элементов итогового массива (использовать событие с ручным сбросом)
5. известить поток main выводе всего массива (момент запуска произойдёт после того, будет сформирован весь
массив (использовать событие с автоматическим сбросом)

Поток SumElement должен выполнить следующие действия (Для синхронизации с потоком main - использовать
критическую секцию, с потоком work - событие!):
-
1. ждёт от потока work сигнал о начале суммирования (использовать событие с ручным сбросом);
2. выполнить суммирование элементов от позиции К1 до позиции К2 итогового массива;
3. известить(использовать критическую секцию) поток main о выводе результата

Задание 4 (Reader_main.cpp; Writer_main.cpp; main.cpp)
-
Написать программы для консольного процесса Administrator и консольных процессов Reader и Writer. Для
моделирования передачи сообщений ввести специальные события, которые обозначают сообщение «А» , «B», «C» ,
«D» и конец сеанса для процессов Reader и Writer. Для сообщений «C» и «D» использовать события c
ручным сбросом.
Одновременно принимать и отправлять сообщения могут только два АКТИВНЫХ процесса Writer(использовать
мьютекс) и два АКТИВНЫХ процесса Reader(использовать семафор), передача остальных сообщений от других
процессов должна временно блокироваться (находиться в режиме ожидания).

Процесс Administrator (main):
-
1. запрашивает у пользователя количество процессов Writer( Reader);
2. запрашивает у пользователя кол-во отправленных сообщений для процессов Writer и кол-во полученных
сообщений Reader (общее количество отправленных и принятых сообщений должно совпадать);
3. запускает заданное количество процессов Reader и Writer;
4. принимает от каждого процесса Writer сообщения и выводит на консоль, затем отправляет их процессам
Reader.
5. принимает от каждого процесса Reader и Writer сообщение о завершении сеанса и выводит его на
консоль в одной строке.
6. завершает свою работу.
Инициализация объектов синхронизации;

Процесс Writer:
-
1. синхронизировать работу процессов Writer с помощью мьютексов
2. передачу сообщений реализовать с помощью событий
3. запрашивает с консоли сообщения, состоящее из “A” или “B”, и передает их (по одному) процессу
Administrator;
4. передает сообщение о завершении сеанса процессу Administrator;
5. завершает свою работу.

Процесс Reader:
-
1. синхронизировать работу процессов Reader с помощью семафора
2. передачу сообщений реализовать с помощью событий
3. принимает сообщения «C» , «D» от процесса Administrator;
4. выводит на консоль сообщения;
5. передает сообщение о завершении сеанса процессу Administrator;
6. завершает свою работу

Задание 5(Server.cpp; Hignt.cpp)
-
Написать программы для консольных процессов Server и Hignt, которые обмениваются сообщениями по анонимному
каналу.
Одновременно сообщение может передаваться только одним из процессов.

Процесс- Server:
-
1. Размер массива вводится с консоли. Тип массива: __int16
2. Запускает процесс Hignt. 
3. Передаёт размер массива процессу Hignt. 
4. Получает массив от процесса Hignt;
5. Выводит переданную и полученную информацию по каналу на консоль

Процесс-Hignt:
-
1. Получает размер массива чисел по анонимному каналу от процесса- Server
2. Генерирует элементы массива 
3. Запрашивает число N 
4. Определяет какие из чисел массива >N передаёт их по анонимному каналу процессу- Server
5. Выводит полученные числа на консоль

Задание 6( Source_Server.cpp; Source_Hignt.cpp)
-
переделать Задание №5, изменить для именованных каналов.
Объекты синхронизации не использовать.
Процессы должны работать на разных компьютерах!
Имя канала на сервере : . (точка - имя сервера) в имени канала (например: \\\\.\\pipe\\demo_pipe ).
Имя компьютера, на котором ваше приложение подключается к каналу: fpmi506pc14 (например)
( например, имя канала для подключения к серверу: \\\\ fpmi506pc14\\pipe\\demo_pipe),
найти в настройках имя сервера: Параметры -> Система -> О системе -> Характеристики устройства ( Имя устройства  fpmi506pc14) ( Пример)  
