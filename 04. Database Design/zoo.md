# Что понадобится

- MySQL Workbench [Скачать](https://dev.mysql.com/downloads/workbench/). После нажатия на Download откроется страница, где надо будет авторизоваться, но ниже есть кнопка "No thanks, just start my download" - нажите её. Удобное средства для построения EER диаграммы и генерации SQL кода. Инструкция по применению - внизу этого документа.
- С MySQL поработаем чуть позже, а первая часть семестра опять посвящена Oracle.
- Синтаксис создания таблиц в MySQL и Oracle отличается, поэтому воспользуемся этим ресурсом [sqlines](http://www.sqlines.com/online) для конвертирования кода в Oracle-вид.
- Примечание: Дома вы можете поставить такой продукт, как Visual Paradigm, который предоставляет больше возможностей (но генерация кода есть в платной версии).

## Конвертация кода

Если вы подготовили EER-диаграмму, то можно получить сгенерированный готовый код, создающий таблицы, ключи и т.д.

1. Нажмите сверху Database - Forward Engineering.
2. В окне вы можете подключиться к MySQL серверу. Можно установить MySQL server на компьютере. Это делается для того, чтобы сразу создать таблички. Но нам необходимо увидеть только Review. Необходимо подлючиться к MySQL Server. Лучший вариант - установить его самостоятельно [MySQL Server](https://dev.mysql.com/downloads/mysql/) Лучше поставить версию 5.7.23 (нажать на кнопку Looking for the latest GA version?). Во время установки не забудьте указанный пароль для root пользователя, после установки можно будет подключиться к серверу через MySQL Workbench, указав host - localhost, user - root, password - то, что вы указали. Другой вариант (не точно, что рабочий) Поэтому подключитесь Hostname: 159.93.169.249 (если из дома) или 10.210.2.249 (если из универа). Port: 3306. Username: user. Password: password.
3. Нажать далее, далее и на шаге - Review SQL Script - скопировать код, начиная с первого `CREATE TABLE` и до конца.
4. Вставить код в [sqlines](http://www.sqlines.com/online) (сверху выбрать MySQL слева, Oracle справа). Нажать кнопку convert.
5. В полученных данных есть немного лишнего. Например `CREATE TABLE mydb.class` (в качестве примера, у вас вместо mydb может быть что-то другое (если переименовывали)). Во всех местах в документе `mydb.` необходимо убрать. Поэтому откройте код в текстовом редакторе и сделайте замену - `mydb.` на пустое значение во всем документе.
6. После этого можно открыть apex.oracle.com SQL workshop - SQL scripts и создать новый скрипт, куда скопировать весь код, полученный выше. Запустить скрипт. Если ошибок не было, то все таблицы создадутся.

## Задание

## Зоопарк

Необходимо спроектировать БД зоопарка.

Нужно хранить список животных с о том, какой у них тип, класс, порядок, семейство, род, вид.

Кроме этого для животного указывается его дата рождения, вес, высота, длина.

Для типа, класса, порядка, семейства, рода и вида необходимо хранить справочную информацию.
Для вида ещё храним охранный статус конкретного вида.

Ещё по БД должна быть возможность понять, кто родитель ребёнка (может и не быть).

Уходом за животными занимаются люди. Нужно хранить информацию о них - (Имя, Фамилия, Отчество, ДР, опыт работы (в годах))
Работник может быть привязан к одному или несколько животных и мы храним дату начала и дата окончания ухода (окончание может быть пустое, т.е. бессрочное).

У каждого животного есть опекуны. Ма храним пока только их имя. Один опекун может быть привязан к 1 или нескольким животным.

**Инструкция:**
Как создать новую диаграмму - показано на скриншотах ниже

![Главная](http://pics.sl/42a/efd/db42a528.png)

![Создание новой модели](http://pics.sl/07f/514/45148768.png)

![Добавление новой диаграммы](http://pics.sl/44b/bf9/83bf9abe.png)

На диаграмму можно добавить таблицы и прочие объекты. Но нам нужны только таблицы

![Добавление таблицы на диаграмму](http://pics.sl/27f/e9d/5b92f37e.png)

После нажатия двойным кликом на таблицу - её можно изменять. Поменять название, атрибуты, поставить первичный ключ и прочие параметры.

![Изменение таблицы](http://pics.sl/5c1/58d/dba21ee7.png)

![Изменение таблицы](http://pics.sl/d74/3aa/ea538b2a.png)

К таблице можно добавить внешний ключ.
Для этого необходимо выбрать нужный из списка слева. Нажать на ту таблицу, в которую будет добавлен новый атрибут - внешний ключ.
И после этого кликнуть на ту таблицу, из которой берём первичный ключ.
После этого ключ создан.

Отменить действией можно как и везде - ctrl+z

![Добавление внешних ключей](http://pics.sl/e6e/e84/5e6e84fc.png)
