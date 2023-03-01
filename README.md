# lab01

### Скачайть библиотеку boost с помощью утилиты wget

```
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```

### Разархивация скаченного файла в директорию

```
$ tar -xvf boost_1_69_0.tar.gz
```

>-x – распаковывает файлы из заархивированного документа

>-v – выводит всю информацию о текущем процессе и показывает сведения об уже завершенном процессе

>-f file – выводит результат в file

Заходим в директорию 

```
$ cd ~/boost_1_69_0
```

### Количество файлов в директории не включая вложенные директории

```
$ ls -la | grep "^-" | wc -l
```

>ls -l - выводить подробный список, в котором будет отображаться владелец, группа, дата создания, размер и другие параметры;

>ls -a – отображать все файлы, включая скрытые, это те, перед именем которых стоит точка

>"^-" – означает, что начинаются со знака "-"

>wc -l – выводит количество строк

### Количество файлов в директории включая вложенные директории
```
$ ls -la | wc -l
```

### Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).

```
$ ls -lAR | grep "\.hpp" | wc -l
$ ls -lAR | grep "\.cpp" | wc -l
$ ls -lAR | grep "\.hpp" -v | grep "\.cpp" -v | wc -l
```

>ls -A – убирает файлы, начинающиеся с . или ..

>ls -R – отображает содержимое поддиректорий (если это не написать, то выводит 0)

>-v – инвертировать поиск, выдавать все строки кроме тех, что содержат шаблон

### Найдите полный пусть до файла any.hpp внутри библиотеки boost.

```
$ find $PWD -type f -name any.hpp
```

>$PWD – выводит путь к папке

>-type f – искать только файлы

>-name – поиск файлов по имени

### Выведите в консоль все файлы, где упоминается последовательность boost::asio.

```
$ grep -Rl "boost::asio"
```

>-l – отобразить только имена файлов, в которых найден шаблон

>-R – читать и обрабатывать все файлы в этом каталоге рекурсивно, следуя всем символическим ссылкам
___

### Скомпилирутйе boost

```
$ sudo apt install libicu-dev
```

Создаем папку "boost_output" в папке ~/boost_1_69_0

```
$ mkdir boost_output
```

Установить пакеты, необходимые для сборки

```
$ sudo apt install gcc
$ sudo apt install build-essential
```
Далее действуем по инструкции из лабы

```
$ ./bootstrap.sh --prefix=boost_output
$ ./b2 install
```

Данная команда будет выполняться долго: 30 мин примерно

### Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs

Переносим все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs

```
$ mv ~/boost_1_69_0/boost_output/lib/ ~/boost-libs/
```

Изменить директорию

```
$ cd ~/boost-libs
```

### Подсчитайте сколько занимает дискового пространства каждый файл в этой директории

```
$ du -h -a | sort -h
```

### Найдите топ10 самых "тяжёлых"

```
$ du -ha | sort -rh | head -n 10
```

## Скрины

![image](https://user-images.githubusercontent.com/125077130/222186623-37ab267b-faa0-47b0-8209-cd6fd8c56fca.png)

![image](https://user-images.githubusercontent.com/125077130/222186683-58367597-2eab-448c-8ebf-6cec95172fbb.png)

![image](https://user-images.githubusercontent.com/125077130/222186734-a47c09e6-e01c-4f90-a61f-57fc1ccf368a.png)

![image](https://user-images.githubusercontent.com/125077130/222186770-67bf1dcf-8500-4a2b-bc8d-37429032731e.png)

![image](https://user-images.githubusercontent.com/125077130/222186805-0d7115bc-f9e6-4005-ac0a-00c0320090db.png)

![image](https://user-images.githubusercontent.com/125077130/222186838-1924d2ec-d933-461c-95c6-0358c4cd4211.png)

![image](https://user-images.githubusercontent.com/125077130/222186890-94285373-82df-4fd8-adef-5f200b3530d1.png)

![image](https://user-images.githubusercontent.com/125077130/222186956-633ce1b9-698f-4c26-80af-b6da48f1f223.png)

![image](https://user-images.githubusercontent.com/125077130/222186988-0786de7c-747b-4c3b-87d8-b8c50663282e.png)

![image](https://user-images.githubusercontent.com/125077130/222187022-cf507cbf-865a-4f43-bdea-7c47972c7572.png)

![image](https://user-images.githubusercontent.com/125077130/222187054-6d5ebaa7-53bc-4f24-8bb7-7985b221167c.png)
