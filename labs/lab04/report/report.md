---
## Front matter
title: "Лабораторная работа №4"
subtitle: "Продвинутое использование git"
author: "Арина Валерьевна Сидорова"

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
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
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
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение навыков правильной работы с репозиториями git.

# Задание

- Выполнить работу для тестового репозитория.
- Преобразовать рабочий репозиторий в репозиторий с git-flow и conventional commits.
.
# Выполнение лабораторной работы

## Установка программного обеспечения

### Установка git-flow

Установка из коллекции репозиториев Copr (рис. @fig:001).

![dnf copr enable elegos/gitflow](image/1.png){#fig:001 width=70%}

(рис. @fig:002).

![dnf install gitflow](image/2.png){#fig:002 width=70%}

### Установка Node.js

На Node.js базируется программное обеспечение для семантического версионирования и общепринятых коммитов. (рис. @fig:004).

![dnf install nodejs](image/4.png){#fig:004width=70%}

(рис. @fig:005).

![dnf install nodejs](image/5.png){#fig:005width=70%}

## Настройка Node.js

Для работы с Node.js добавим каталог с исполняемыми файлами, устанавливаемыми yarn, в переменную PATH.(рис. @fig:006).

![Настройка Node.js](image/6.png){#fig:006 width=70%}

## Общепринятые коммиты

### commitizen

- Данная программа используется для помощи в форматировании коммитов.

### standard-changelog

- Данная программа используется для помощи в создании логов. (рис. @fig:007).

![Cоздаем ключи](image/7.png){#fig:007 width=70%}

## Создание репозитория git

Cоздаем репозиторий (рис. @fig:008).
        
![репозиторий гитхаб](image/8.png){#fig:008 width=70%}

Делаем первый коммит и выкладываем на github
Конфигурация для пакетов Node.js(рис. @fig:009).
        
![Делаем коммит и конфигурацию для пакетов](image/9.png){#fig:009 width=70%}

Сконфигурируем формат коммитов. Для этого добавим в файл package.json команду для формирования коммитов:(рис. @fig:010).
        
![Конфигурируем формат коммитов](image/10.png){#fig:010 width=70%}

Добавим новые файлы, выполним коммит и отправим на гитхаб (рис. @fig:011).
        
![git add . ; git cz; git push](image/11.png){#fig:011 width=70%}

Инициализируем git-flow(рис. @fig:012).
        
![git flow init](image/12.png){#fig:012 width=70%}

Проверим, что Вы на ветке develop:(рис. @fig:013).
        
![git branch](image/13.png){#fig:013 width=70%}

Загрузим весь репозиторий в хранилище:(рис. @fig:014).
        
![git push --all](image/14.png){#fig:014 width=70%}

Установим внешнюю ветку как вышестоящую для этой ветки:(рис. @fig:015).
        
![git branch --set-upstream-to=origin/develop develop](image/15.png){#fig:015 width=70%}

Создадим релиз с версией 1.0.0(рис. @fig:016).
        
![git flow release start 1.0.0](image/16.png){#fig:016 width=70%}

Создадим журнал изменений(рис. @fig:017).
        
![standard-changelog --first-release](image/17.png){#fig:017 width=70%}

Добавим журнал изменений в индекс(рис. @fig:018).
        
![git add CHANGELOG.md;git commit -am 'chore(site): add changelog'](image/18.png){#fig:018 width=70%}


Зальём релизную ветку в основную ветку(рис. @fig:019).
        
![git flow release finish 1.0.0](image/19.png){#fig:019 width=70%}

Отправим данные на github(рис. @fig:020).
        
![git push --all](image/20.png){#fig:020 width=70%}

Отправим данные на github(рис. @fig:021).
        
![git push --tags](image/21.png){#fig:021 width=70%}

Создадим релиз на github. Для этого будем использовать утилиты работы с github:(рис. @fig:022).
        
![gh release create v1.0.0 -F CHANGELOG.md](image/22.png){#fig:022 width=70%}


## Работа с репозиторием git

Создадим ветку для новой функциональности:(рис. @fig:023).
        
![git flow feature start feature_branch](image/23.png){#fig:023 width=70%}

По окончании разработки новой функциональности следующим шагом следует объединить ветку feature_branch c develop (рис. @fig:024).
        
![git flow feature finish feature_branch](image/24.png){#fig:024 width=70%}

Создадим релиз с версией 1.2.3:
Добавим журнал изменений в индекс
Зальём релизную ветку в основную ветку(рис. @fig:025).
        
![git flow release start 1.2.3](image/25.png){#fig:025 width=70%}

Отправим данные на гитхаб(рис. @fig:026).
        
![отправляем](image/26.png){#fig:026 width=70%}

Создадим релиз на github с комментарием из журнала изменений:(рис. @fig:027).
        
![gh release create v1.2.3 -F CHANGELOG.md](image/27.png){#fig:027 width=70%}


# Выводы
Получили навыки правильной работы с репозиториями git.

