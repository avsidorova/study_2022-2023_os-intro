---
## Front matter
lang: ru-RU
title: Лабораторная работа номер 4
subtitle: Продвинутое использование git
author:
  - Сидорова Арина Валерьевна
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 6 марта 2025

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Cидорова Арина Валерьевна
  * студентка НПИбд-02-24
  * студент кафедры прикладной информатики
  * Российский университет дружбы народов

:::
:::
::::::::::::::

# Вводная часть

## Цели и задачи

- Получение навыков правильной работы с репозиториями git.
- Выполнить работу для тестового репозитория.
- Преобразовать рабочий репозиторий в репозиторий с git-flow и conventional commits.

## Материалы и методы

- Процессор `pandoc` для входного формата Markdown
- Результирующие форматы
	- `pdf`
	- `html`
- Автоматизация процесса создания: `Makefile`

# Выполнение лабораторной работы

## Установка программного обеспечения

### Установка git-flow

- Установка из коллекции репозиториев Copr 

![dnf copr enable elegos/gitflow](image/1.png){#fig:001 width=70%}


![dnf install gitflow](image/2.png){#fig:002 width=70%}

### Установка Node.js

- На Node.js базируется программное обеспечение для семантического версионирования и общепринятых коммитов. 

![dnf install nodejs](image/4.png){#fig:004width=70%}


![dnf install nodejs](image/5.png){#fig:005width=70%}

## Настройка Node.js

- Для работы с Node.js добавим каталог с исполняемыми файлами, устанавливаемыми yarn, в переменную PATH.

![Настройка Node.js](image/6.png){#fig:006 width=70%}

## Общепринятые коммиты

### commitizen

- Данная программа используется для помощи в форматировании коммитов.

### standard-changelog

- Данная программа используется для помощи в создании логов. 

![Cоздаем ключи](image/7.png){#fig:007 width=70%}

## Создание репозитория git

Cоздаем репозиторий 
        
![репозиторий гитхаб](image/8.png){#fig:008 width=70%}

- Делаем первый коммит и выкладываем на github
Конфигурация для пакетов Node.js
        
![Делаем коммит и конфигурацию для пакетов](image/9.png){#fig:009 width=70%}

### Сконфигурируем формат коммитов. Для этого добавим в файл package.json команду для формирования коммитов:
        
![Конфигурируем формат коммитов](image/10.png){#fig:010 width=70%}

### Добавим новые файлы, выполним коммит и отправим на гитхаб 
        
![git add . ; git cz; git push](image/11.png){#fig:011 width=70%}

### Инициализируем git-flow
        
![git flow init](image/12.png){#fig:012 width=70%}

### Проверим, что Вы на ветке develop:
        
![git branch](image/13.png){#fig:013 width=70%}

### Загрузим весь репозиторий в хранилище:
        
![git push --all](image/14.png){#fig:014 width=70%}

### Установим внешнюю ветку как вышестоящую для этой ветки:
        
![git branch --set-upstream-to=origin/develop develop](image/15.png){#fig:015 width=70%}

### Создадим релиз с версией 1.0.0
        
![git flow release start 1.0.0](image/16.png){#fig:016 width=70%}

### Создадим журнал изменений
        
![standard-changelog --first-release](image/17.png){#fig:017 width=70%}

### Добавим журнал изменений в индекс
        
![git add CHANGELOG.md;git commit -am 'chore(site): add changelog'](image/18.png){#fig:018 width=70%}


### Зальём релизную ветку в основную ветку
        
![git flow release finish 1.0.0](image/19.png){#fig:019 width=70%}

### Отправим данные на github
        
![git push --all](image/20.png){#fig:020 width=70%}

### Отправим данные на github
        
![git push --tags](image/21.png){#fig:021 width=70%}

### Создадим релиз на github. Для этого будем использовать утилиты работы с github:
        
![gh release create v1.0.0 -F CHANGELOG.md](image/22.png){#fig:022 width=70%}


## Работа с репозиторием git

### Создадим ветку для новой функциональности:
        
![git flow feature start feature_branch](image/23.png){#fig:023 width=70%}

### По окончании разработки новой функциональности следующим шагом следует объединить ветку feature_branch c develop 
        
![git flow feature finish feature_branch](image/24.png){#fig:024 width=70%}

### Создадим релиз с версией 1.2.3:
- Добавим журнал изменений в индекс
- Зальём релизную ветку в основную ветку
        
![git flow release start 1.2.3](image/25.png){#fig:025 width=70%}

### Отправим данные на гитхаб
        
![отправляем](image/26.png){#fig:026 width=70%}

### Создадим релиз на github с комментарием из журнала изменений:
        
![gh release create v1.2.3 -F CHANGELOG.md](image/27.png){#fig:027 width=70%}


# Выводы
Получили навыки правильной работы с репозиториями git.

