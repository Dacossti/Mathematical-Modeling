---
# Front matter
lang: ru-RU
title: "Химические реакции, стохастическое горение"
subtitle: "Этап 1. Теоретическая модель"
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

# Введение

## Научная проблема

Моделирование химических реакций в условиях микроскопического ансамбля частиц — это ключ к пониманию динамики горения, катализаторов и других физических явлений. В частности, интерес представляет мономолекулярная экзотермическая реакция, где реакция A → B сопровождается выделением тепла. [@medved:2010].

## Цель работы

Моделировать химические реакции в условиях микроскопического ансамбля частиц.

## Задачи

1. Напишите программу, моделирующую ансамбль частиц, в которых возможна мономолекулярная экзотермическая реакция. Рассмотрите случай нулевой теплопроводности. Постройте графики зависимости числа непрореагировавших частиц от времени при разных температурах. Сравните полученные графики с теоретическими зависимостями.
2. Постройте графики зависимости числа непрореагировавших частиц, температуры и скорости реакции от времени в случае бесконечной теплопроводности внутри области моделирования, считая процесс адиабатическим.

# Теоретическое описание задачи

Для одной молекулы A вероятность реакции за время τ определяется:
$$
\alpha = \int_{E_a}^{\infty} \frac{1}{kT} e^{-E/kT} dE = e^{-E_a / kT}
$$

Изменение количества непрореагировавших молекул:
$$
\frac{dN}{dt} = -N u, \quad u = \frac{1}{\tau} e^{-E_a / kT}
$$

Решение: 
$$
N(t) = N_0 e^{-u t}
$$

В случае **бесконечной теплопроводности**, температура меняется:
$$
\frac{dN}{dt} = -\frac{N}{\tau} e^{-E_a/kT}, \quad
\frac{dT}{dt} = -\frac{q}{N_0 c} \frac{dN}{dt}
$$

## Описание модели

1. **Частицы** находятся в начальном состоянии A.
2. Для каждой частицы генерируется энергия: `E = -kT * ln(random())`.
3. Реакция происходит, если `E > Ea`.
4. При реакции:
   - В случае нулевой теплопроводности: температура не меняется.
   - В случае бесконечной теплопроводности: температура системы возрастает.
5. Статистика собирается для N(t), T(t), скорости реакции.

# Выводы

Во время выполнения первого этапа проекта сделали теоретическое описание моделей химических реакций в условиях микроскопического ансамбля частиц в случаях нулевой теплопроводности и бесконечной теплопроводности. Далее определили задачи дальнейшего исследования.

# Список литературы

1. Медведев Д.А. и др. Моделирование физических процессов и явлений на ПК: Учеб. пособие. Новосибирск: Новосиб. гос. ун-т, 2010. 101 с.
2. Gillespie D.T. Exact stochastic simulation of coupled chemical reactions. Journal of Physical Chemistry. — 1977. — Vol. 81, No. 25. — P. 2340–2361.
3. Yu C., Cai L., Chen J.-Y. Stochastic Modeling of Partially Stirred Reactor (PaSR) for the Investigation of the Turbulence-Chemistry Interaction for the Ammonia-Air Combustion. Flow, Turbulence and Combustion. — 2023. — Vol. 111. — P. 575–597.
