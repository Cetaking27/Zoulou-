---
# Front matter
title: "Отчёт по лабораторной работе №4"
subtitle: "Подгонка полиномиальной кривой и "
author: "Аба Альфонс НПМмд 02-22"

# Generic otions
lang: ru-RU
toc-title: "Содержание"

# Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

# Pdf output format
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
### Fonts
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
## Misc options
indent: true
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Научиться решать общую проблему подгонки полинома к множеству точек и так же использовать несколько способов представления изображения в виде Матрицы и матричные преобразования.

# Теоретические сведения
## Подгонка полиномиальной кривой.
## определение:

Подгонка кривой — это процесс построениякривой, илиматематической функции, которая наилучшим образом подходит для рядаточек данных, возможно, подверженных ограничениям. Подгонка кривой может включать либоинтерполяцию, где требуется точное соответствие данным, либосглаживание, в котором строится «гладкая» функция, которая приблизительно соответствует данным. Смежной темой являетсярегрессионный анализ,который больше фокусируется на вопросахстатистического вывода, таких как сколько неопределенности присутствует в кривой, которая соответствует данным, наблюдаемым со случайными ошибками.

Встроенные кривые могут быть использованы в качестве вспомогательного средства для визуализации данных, чтобы вывести значения функции, где нет доступных данных, и обобщить отношения между двумя или более переменными. Экстраполяцияотносится к использованию подходящей кривой за пределамидиапазонанаблюдаемых данных,и подверженаопределенной степени неопределенности, поскольку она может отражать метод, используемый для построения кривой, в той же мере, в какой она отражает наблюдаемые данные.

Для линейно-алгебраического анализа данных «подгонка» обычно означает попытку найти кривую, которая минимизирует вертикальное (ось y) смещение точки от кривой (например, обычные наименьшие квадраты). Однако для графических и графических приложений геометрическая подгонка стремится обеспечить наилучшее визуальное соответствие; что обычно означает попытку минимизироватьортогональное расстояниедо кривой (например, общее наименьшее количество квадратов) или иным образом включить обе оси смещения точки от кривой. Геометрические припадки не популярны, потому что они обычно требуют нелинейных и / или итеративных вычислений, хотя они имеют преимущество более эстетичного и геометрически точного результата.

## Практические применение подгонкой полиномиальной кривой в OCTAVE 

Пусть нам нужно найти параболу по методу наименьших
квадратов для набора точек, заданных матрицей

![рис 1](image/001.png){ #fig:001 width=70% height=70%}

В матрице заданы значения 𝑥 в столбце 1 и значения 𝑦 в столбце 2.
Введём матрицу данных в Octave и извлечём вектора 𝑥 и 𝑦.
Мы смогли нарисовать точки на графике.


![рис 2](image/1.png){ #fig:01 width=70% height=70%}

Построим уравнение вида 𝑦 = 𝑎𝑥2 + 𝑏𝑥 + 𝑐. Подставляя данные,
получаем следующую систему линейных уравнений.

![рис 3](image/002.png){ #fig:012 width=70% height=70%}

Решение по методу наименьших квадратов получается из решения уравнения 𝐴𝑇𝐴𝑏 = 𝐴𝑇𝑦, где 𝑏 – вектор коэффициентов полинома. Используем
Octave для построения уравнений.

![рис 4](image/2.png){ #fig:002 width=70% height=70%}

Решим задачу методом Гаусса. Запишем расширенную матрицу:

![рис 5](image/3.png){ #fig:003 width=70% height=70%}

Процесс подгонки может быть автоматизирован встроенными функциям OCTAVE

![рис 6](image/4.png){ #fig:004 width=70% height=70%}

## Матричные преобразования

Элементарные преобразования матрицы — это такие преобразования матрицы, в результате которых сохраняется эквивалентность матриц. Таким образом, элементарные преобразования не изменяют множество решений системы линейных алгебраических уравнений, которую представляет эта матрица. Элементарные преобразования используются в методе Гаусса для приведения матрицы к треугольному или ступенчатому виду. Элементарными преобразованиями строк называют: перестановку местами любых двух строк матрицы.

Мы записываем это как матрицу 2 × 𝑛, где каждый столбец представляет точку на рисунке. В качестве простого примера, давайте попробуем закодировать граф-домик. Есть много способов закодировать это как матрицу. Эффективный метод состоит в том, чтобы выбрать путь, который проходит по каждому ребру ровно одинт раз (цикл Эйлера).

![рис 7](image/5.png){ #fig:005 width=70% height=70%}

# 1. Вращение:

Рассмотрим различные способы преобразования изображения.

![рис 8](image/6.png){ #fig:006 width=70% height=70%}

# 2. Отражение:

Отразим граф дома относительно прямой 𝑦 = 𝑥. Зададим матрицу отражения (поясните, почему она такая).

![рис 9](image/7.png){ #fig:007 width=70% height=70%}

# 3. Дилатация:

Дилатация (то есть расширение или сжатие) также может быть выполнено
путём умножения матриц.

![рис 10](image/8.png){ #fig:008 width=70% height=70%}

# Заключения 

я научился как реализовать матричные преобразования и так же решать задач подгонкой полиномиальной кривой на OCTAVE GNU.



1. [OCtave GNU](https://octave.org/bugs.html)
2.[Система линейных алгебраических уравнений](https://ru.wikipedia.org/wiki/%D0%A1%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D0%B0_%D0%BB%D0%B8%D0%BD%D0%B5%D0%B9%D0%BD%D1%8B%D1%85_%D0%B0%D0%BB%D0%B3%D0%B5%D0%B1%D1%80%D0%B0%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D1%85_%D1%83%D1%80%D0%B0%D0%B2%D0%BD%D0%B5%D0%BD%D0%B8%D0%B9)
3.[Элементарные преобразования матрицы](https://ru.wikipedia.org/wiki/%D0%AD%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82%D0%B0%D1%80%D0%BD%D1%8B%D0%B5_%D0%BF%D1%80%D0%B5%D0%BE%D0%B1%D1%80%D0%B0%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F_%D0%BC%D0%B0%D1%82%D1%80%D0%B8%D1%86%D1%8B#:~:text=%D0%AD%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82%D0%B0%D1%80%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%B5%D0%BE%D0%B1%D1%80%D0%B0%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F%20%D0%BC%D0%B0%D1%82%D1%80%D0%B8%D1%86%D1%8B%20%E2%80%94%20%D1%8D%D1%82%D0%BE,%D0%BC%D0%B5%D1%81%D1%82%D0%B0%D0%BC%D0%B8%20%D0%BB%D1%8E%D0%B1%D1%8B%D1%85%20%D0%B4%D0%B2%D1%83%D1%85%20%D1%81%D1%82%D1%80%D0%BE%D0%BA%20%D0%BC%D0%B0%D1%82%D1%80%D0%B8%D1%86%D1%8B)
4. [МЕтод ГАУССА ](https://ru.wikipedia.org/wiki/%D0%9C%D0%B5%D1%82%D0%BE%D0%B4_%D0%93%D0%B0%D1%83%D1%81%D1%81%D0%B0)

