---
# Front matter
lang: ru-RU
title: "Химические реакции, стохастическое горение"
subtitle: "Этап 2. Алгоритмы моделирования"
author: "Озьяс Стев Икнэль Дани"

## Pdf output format
toc: true # Table of contents
toc-depth: 2
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
lofTitle: "Цель Работы"
lotTitle: "Ход Работы"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Описать алгоритмы решения задачи.

# Задачи

1. Напишите программу, моделирующую ансамбль частиц, в которых возможна мономолекулярная экзотермическая реакция. Рассмотрите случай нулевой теплопроводности. Постройте графики зависимости числа непрореагировавших частиц от времени при разных
температурах. Сравните полученные графики с теоретическими зависимостями.
2. Постройте графики зависимости числа непрореагировавших частиц, температуры и скорости реакции от времени в случае бесконечной теплопроводности внутри области моделирования, считая процесс адиабатическим.

# Описание алгоритмов

## Алгоритм для случая нулевой теплопроводности

1. Инициализация: N₀ частиц, температура T₀, параметры Ea, q, τ.
2. Для каждого временного шага:
   - Для каждой непрореагировавшей частицы:
     - Вычисляется энергия E = -kT * ln(rand()).
     - Если E > Ea, частица реагирует.
   - Обновляется N(t).
3. Построение графика N(t).

## Алгоритм для случая бесконечной теплопроводности (адиабатический процесс)

1. После реакции каждой частицы:
   - Температура увеличивается: 
     $$
     \Delta T = \frac{q}{N_0 c}
     $$
2. Таким образом, с каждой реакцией растёт вероятность новых реакций.
3. Реакция моделируется до тех пор, пока N → 0.

## Численное решение системы дифференциальных уравнений

$$
\frac{dN}{dt} = -\frac{N}{\tau} e^{-E_a / kT}, \quad
\frac{dT}{dt} = \frac{q}{N_0 c} \cdot \frac{N}{\tau} e^{-E_a / kT}
$$

Метод Эйлера или метод Рунге-Кутты используем для численного решения.

# Выводы

Во время выполнения второго этапа проекта сделали теоретическое описание алгоритмов решения задачи в случаях нулевой теплопроводности и бесконечной теплопроводности.

# Список литературы

1. Медведев Д.А. и др. Моделирование физических процессов и явлений на ПК: Учеб. пособие. Новосибирск: Новосиб. гос. ун-т, 2010. 101 с.
2. Gillespie D.T. Exact stochastic simulation of coupled chemical reactions. Journal of Physical Chemistry. — 1977. — Vol. 81, No. 25. — P. 2340–2361.
3. Yu C., Cai L., Chen J.-Y. Stochastic Modeling of Partially Stirred Reactor (PaSR) for the Investigation of the Turbulence-Chemistry Interaction for the Ammonia-Air Combustion. Flow, Turbulence and Combustion. — 2023. — Vol. 111. — P. 575–597.
