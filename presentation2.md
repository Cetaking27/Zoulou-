---
## Front matter
lang: ru-RU
title: Язык разметки Маrkdwon
author: Аба Альфонс  НПМмд-02-22
institute: Российский Университет Дружбы Народов
date:  01 Октябрь, 2022, Москва, Россия

## Formatting
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
toc: false
slide_level: 2
theme: metropolis
header-includes: 
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true

---

# Цели и задачи

## Цель лабораторной работы

Изучение как оформлять отчёты с помощью легковесного языка разметки Markdown.
пример отчета с git 


# Выполнение лабораторной работы

## Markdown 

Markdown (МФА: [ ˈ m ɑ ː k d a ʊ n ], произносится маркда́ун) — облегчённый язык разметки, созданный с целью обозначения форматирования в простом тексте, с максимальным сохранением его читаемости человеком, и пригодный для машинного преобразования в языки для продвинутых публикаций (HTML, Rich Text и других).

## Системы контроля версий. Общие понятия
# системы контроля версий (Distributed Version Control System, DVCS) :  git
Система контроля версий Git представляет собой набор программ командной строки. Доступ к ним можно получить из терминала посредством ввода команды git с различными опциям.
Благодаря тому, что Git является распределённой системой контроля версий, резервную копию локального хранилища можно сделать простым копированием или архивацией.

## Контрольный пример
1. Создание базовых конфигурации для работы с git:

![учётная запись](image/1.1.png){ #fig:001 width=70% height=70%}

2. Создание ключи ssh и  ключи pgp

![генерация ключи ssh ](image/3.png){ #fig:005 width=70% height=70%}

![генерация ключи PGP](image/5.png){ #fig:007 width=70% height=70%}

3. Добавление PGP ключа в GitHub

![Дабавление PGP](image/7.png){ #fig:009 width=70% height=70%}

4. Шаблон для рабочего пространства

# Выводы
базовые сведения просходит через создание заголовков, которой производится путём помещения знака решетки перед текстом заголовка. Количество знаков «#» соответствует уровню заголовка. 
1 # This is heading 1
2 ## This is heading 2
3 ### This is heading 3
4 #### This is heading 4
Чтобы задать для текста какие-нибудь модификацию, используем двойные, либо троеные звездочки следовательно ставим язык на котором делаем модификацию.
пример : This text is  **bold**, *italic*,  ***bold and italic***.

## Результаты выполнения лабораторной работы
 
изучал как офомрить очеты на язык разметки Маrkdwon.