---
## Front matter
title: "Отчёт по лабораторной работе № 2"
author: "Королёв Иван Андреевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux

# Задание

Постарайтесь последовательно выполнить все пункты, занося ваши ответы на поставленные вопросы и замечания в отчёт:
1. В установленной при выполнении предыдущей лабораторной работы
операционной системе создайте учётную запись пользователя guest (использую учётную запись администратора):
useradd guest
2. Задайте пароль для пользователя guest (использую учётную запись администратора):
passwd guest
3. Войдите в систему от имени пользователя guest.
4. Определите директорию, в которой вы находитесь, командой pwd. Сравните её с приглашением командной строки. Определите, является ли она
вашей домашней директорией? Если нет, зайдите в домашнюю директорию.
5. Уточните имя вашего пользователя командой whoami.
6. Уточните имя вашего пользователя, его группу, а также группы, куда входит пользователь, командой id. Выведенные значения uid, gid и др. запомните. Сравните вывод id с выводом команды groups.
7. Сравните полученную информацию об имени пользователя с данными,
выводимыми в приглашении командной строки.
8. Просмотрите файл /etc/passwd командой cat /etc/passwd
Найдите в нём свою учётную запись. Определите uid пользователя.
Определите gid пользователя. Сравните найденные значения с полученными в предыдущих пунктах.
Замечание: в случае, когда вывод команды не умещается на одном
экране монитора, используйте прокрутку вверх–вниз (удерживая клавишу shift, нажимайте page up и page down) либо программу grep в качестве фильтра для вывода только строк, содержащих определённые
буквенные сочетания:
cat /etc/passwd | grep guest
9. Определите существующие в системе директории командой
ls -l /home/
Удалось ли вам получить список поддиректорий директории /home? Какие права установлены на директориях?
10. Проверьте, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой:
lsattr /home
Удалось ли вам увидеть расширенные атрибуты директории?
Удалось ли вам увидеть расширенные атрибуты директорий других
пользователей?
11. Создайте в домашней директории поддиректорию dir1 командой
mkdir dir1
Определите командами ls -l и lsattr, какие права доступа и расширенные атрибуты были выставлены на директорию dir1.
12. Снимите с директории dir1 все атрибуты командой
chmod 000 dir1
и проверьте с её помощью правильность выполнения команды
ls -l
13. Попытайтесь создать в директории dir1 файл file1 командой
echo "test" > /home/guest/dir1/file1
Объясните, почему вы получили отказ в выполнении операции по созданию файла?
Оцените, как сообщение об ошибке отразилось на создании файла? Проверьте командой
ls -l /home/guest/dir1
действительно ли файл file1 не находится внутри директории dir1.
14. Заполните таблицу «Установленные права и разрешённые действия»
(см. табл. 2.1), выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.
Если операция разрешена, занесите в таблицу знак «+», если не разрешена, знак «-».
**Замечание 1:** при заполнении табл. 2.1 рассматриваются не все атрибуты файлов и директорий, а лишь «первые три»: г, w, х, для «владельца».
Остальные атрибуты также важны (особенно при использовании доступа от имени разных пользователей, входящих в те или иные группы).
Проверка всех атрибутов при всех условиях значительно увеличила бы
таблицу: так 9 атрибутов на директорию и 9 атрибутов на файл дают
218 строк без учёта дополнительных атрибутов, плюс таблица была бы
расширена по количеству столбцов, так как все приведённые операции
необходимо было бы повторить ещё как минимум для двух пользователей: входящего в группу владельца файла и не входящего в неё.
После полного заполнения табл. 2.1 и анализа полученных данных нам
удалось бы выяснить, что заполнение её в таком виде излишне. Можно разделить большую таблицу на несколько малых независимых таблиц.
В данном примере предлагается рассмотреть 3 + 3 атрибута, т.е. 2
6 = 64
варианта.
**Замечание 2:** в ряде действий при выполнении команды удаления файла
вы можете столкнуться с вопросом: «удалить защищённый от записи пустой обычный файл dir1/file1?» Обратите внимание, что наличие этого
вопроса не позволяет сделать правильный вывод о том, что файл можно удалить. В ряде случаев, при ответе «y» (да) на указанный вопрос,
возможно получить другое сообщение: «невозможно удалить dirl /file1:
Отказано в доступе».
15. На основании заполненной таблицы определите те или иные минимально необходимые права для выполнения операций внутри директории
dir1, заполните табл. 2.2.

# Теоретическое введение

В Linux существует три основных типа прав доступа:

1. Чтение (Read) — обозначается буквой «r». Предоставляет возможность просматривать содержимое файла или каталога.

2. Запись (Write) — обозначается буквой «w». Позволяет создавать, изменять и удалять файлы внутри каталога, а также изменять содержимое файла.

3. Выполнение (Execute) — обозначается буквой «x». Даёт разрешение на выполнение файла или на вход в каталог.

Каждый из указанных типов прав доступа может быть назначен трём группам пользователей:

1. Владелец (Owner) — пользователь, который является владельцем файла или каталога.

2. Группа (Group) — группа пользователей, к которой принадлежит файл или каталог.

3. Остальные пользователи (Others) — все остальные пользователи системы.

Комбинация базовых прав доступа для каждой из групп пользователей определяет полный набор прав доступа для файла или каталога.

# Выполнение лабораторной работы

## Задание № 1

Создаю новую учётную запись и называю её guest. 

## Задание № 2

Создаю пароль для новой учётной записи и вхожу от имени guest 

## Задание № 3

Определяю в какой директории я нахожусь. Она совпадает (рис. [-@fig:001]).

![guest](image/10.jpg){#fig:001 width=70%}

## Задание № 4

Проверяю имя своего пользователя. Она совпадает (рис. [-@fig:002]).

![guest](image/3.jpg){#fig:002 width=70%}

## Задание № 5

Уточняю имя пользователя, его группу, а также группы, куда входит пользователь, командой id. Сравиваю вывод id и groups(id - выводит реальные и действующие идентификаторы пользователей и групп. groups - вывод списка групп, в которых состоит пользователь с указанным именем.) (рис. [-@fig:003]).

![id and groups](image/7.jpg){#fig:003 width=70%}

## Задание № 6

Просматриваю файл /etc/passwd с помощью команды cat /etc/passwd | grep guest и сравниваю группы с выводом id. Всё совпадает, 1001! (рис. [-@fig:004]).

![/etc/passwd](image/12.jpg){#fig:004 width=70%}

## Задание № 7

Определите существующие в системе директории командой ls -l /home/. Список поддиректорий получить удалось. Права установлены чтение, запись и выполнение (рис. [-@fig:005]).

![ls -l /home/](image/4.jpg){#fig:005 width=70%}

## Задание № 8

Проверьте, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой: lsattr /home. Для моего основного пользователя узнать нельзя, тк нет на это прав, для guest вывод есть. (рис. [-@fig:006]).

![lsattr /home](image/5.jpg){#fig:006 width=70%}

## Задание № 9

Создайте в домашней директории поддиректорию dir1. Права доступа выведены на скриншот (рис. [-@fig:007]).

![dir1](image/9.jpg){#fig:007 width=70%}

## Задание № 10

Снимите с директории dir1 все атрибуты (рис. [-@fig:008]).

![dir1](image/6.jpg){#fig:008 width=70%}

## Задание № 10

Попытайтесь создать в директории dir1 файл file1. Отказ, потому что нет прав доступа на создание в директории файлов. (рис. [-@fig:009]).

![dir1](image/1.jpg){#fig:009 width=70%}

## Таблица  «Установленные права и разрешённые действия»

![Установленные права и разрешённые действия](image/lab2_table.pdf)

# Выводы

Получил практические навыки работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux

