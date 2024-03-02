---
## Front matter
title: "Индивидуальный проект. Первый этап. "
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

Установить дистрибутив Kali Linux в виртуальную машину. Научиться основным способам тестирования веб приложений. В качестве среды виртуализации предлагается использовать VirtualBox.

# Задание

Установить дистрибутив Kali Linux в виртуальную машину.

# Теоретическое введение

**Kali Linux** — это дистрибутив операционной системы Linux. Это одна из немногих систем, которая предназначена для специалистов информационной безопасности. В неё входит ряд утилит, которые созданы для тестирования уязвимостей. Kali редко используется как основная ОС, чаще всего она устанавливается как гостевая.
Система Kali Linux была разработана в 2013 году. Над ней работала команда из Offensive Security.

# Выполнение лабораторной работы

## Создание машины в VirtualBox

Демонстрирую создание машины Kali linux. Отображаю выделенную оперативную, видео и память жесткого диска для данного дистрибутива. (рис. [-@fig:001]).

![Машина в VirtualBox](image/1.png){#fig:001 width=70%}

## Kali linux

Установил kali linux, обновил и выполнил основную настройку машины (общий буфер обмена, горячие клавиши, языки, github) (рис. [-@fig:002]),(рис. [-@fig:003]),

![kali linux](image/2.png){#fig:002 width=70%}

![kali linux](image/3.png){#fig:003 width=70%}

# Выводы

Научился устанавливать kali linux

