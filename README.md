Стиль LaTeX для расчётно-пояснительной записки к курсовым и дипломным работам (ГОСТ 7.32-2001)
===========

Ориентирован на студентов IT специальностей.

Изначально был написан в расчёте на `pdfLaTeX`, с коммита `23b1612` добавлена поддержка `XeLaTeX`. Помимо стилей содержит "рыбу" РПЗ (в той же папке `tex`). Его можно собрать используя make.

Также имеются необходимые макеты (layout) для [LyX](http://ru.wikipedia.org/wiki/LyX) (редактор, редактирование в котором больше похоже на работу в `Microsoft Word`, чем на написание `LaTeX` кода, но результат получается такой же хороший, как в `LaTeX`). Для использования `LyX` также нужно скопировать стили LaTeX (из папки `tex`).

## Результат
См. вкладку [Релизы](https://github.com/rominf/latex-g7-32/releases).

### Попробовать online
Спасибо [@KMax](https://github.com/rominf/latex-g7-32/issues/11), теперь [можно попробовать](https://www.sharelatex.com/project/54885f204b9308be064f025e) шаблон в ShareLaTeX.

## Участие в проекте

Стиль распространяется "как есть". В случае обнаружения несостыковок с ГОСТом, обнаружении багов, а также если есть вопросы по использованию, не отражённые в документации, заводите issue. Pull requests принимаются. Быстрой реакции не обещаю, особенно во время сессии.

## Установка

### Зависимости

Поскольку я, @rominf, пользуюсь openSUSE, буду также писать список пакетов LaTeX, которые можно поставить через zypper.

#### Основные

##### LaTeX пакеты
```
amssymb amsmath caption flafter footmisc hyperref icomma iftex graphicx longtable underscore
```
###### openSUSE
```
texlive-latex texlive-iftex 
```

##### Программы
```
inkscape dia pgf context 
```

#### pdfLaTeX-версия
##### LaTeX пакеты
```
cmap babel mathtext pscyr ucs
```

Для придания таймовского вида нужно установить соотв. шрифты (пакет `cyrtimes.sty`), в Debian/Ubuntu это пакет `scalable-cyrfonts-tex`. Если этого пакета нет, оно использует стандартную гарнитуру CM.

#### XeLaTeX-версия
##### LaTeX пакеты
```
cm-unicode-fonts minted polyglossia xecyr
```

###### openSUSE
```
cm-unicode-fonts texlive-minted texlive-polyglossia texlive-xecyr
```

##### Программы
```
python pygments
```

#### LyX
```
lyx
```

#### Установочный скрипт
```
python3.4
```

Копирует (или перемещает) файлы со стилями в общую `texmf` папку, макеты `LyX` в папку с настройками `LyX`. Для получения помощи вызовите `install.py --help`.

## Использование LaTeX
После изменения РПЗ запустите `make` в корне. Результатом будет `rpz.pdf`. Если требуется использование `pdfLaTeX` то в `Makefile` надо поменять в третье строке `xelatex` на `pdflatex`.

### Редактор
Можно использовать любой редактор, например, `Kile`. На комманду `cd .. && make` вешается горячая клавиша и создаётся проект с корректным главным докукментом.

## Использование LyX
Откройте `lyx/rpz.lyx` и редактируйте.

В первый раз необходимо настроить параметры вызова XeLaTeX, для того, чтобы `minted` работал.

Настроки -> Обработка файлов -> Конверторы -> LaTeX (XeTeX) -> PDF (XeTeX) -> Изменить -> Преобразователь: `xelatex -shell-escape $$i`.

## Авторы

### 1. Первая версия
Алексей Томин

### 2. Доработка "дебианщика"
[Михаил Конник](http://mydebianblog.blogspot.ru/2008/09/732-2001-latex.html)

### 3a. Доработка кафедры [ИУ7](http://iu7.bmstu.ru)
|[Всеволод Крищенко](http://web.archive.org/web/20100424031801/http://sevik.ru/latex/)|
-------------------

[Иван Коротков](https://github.com/tw33dl3dee)

#### Changelog
1. Заработали cases и tabular;
2. Добавлена опция utf8;
3. Комментарии в UTF-8;
4. Изменены отступы после тире в description;
5. Добавлен \paragraph;
6. Уменьшены отспупы после заголовков и учеличены --- до (хотя это, возможно, и нарушает 7-32);
7. Сделаны отсупы в оглалвнеии (ГОСТ эту тему обходит, как мы поняли);
8. \normalfont;
9. Добавлен раздел "Приложения".
9. Makefile для автоматизации рутины;
10. Рисунки (обрезка, конвертация dia, dot, svg);
11. Стили для листингов;
12. Разные мелочи.


### 3b. Добавление layouts LyX
[Расим (Brotherofken)](http://habrahabr.ru/post/116517/)

### 4. GitHub, поддержка XeLaTeX, LyX
[Роман Инфлянскас](https://github.com/rominf)

### 5. Further fixes, tweaks and development

According to the requirements of
ГОСТ 7.32-2001 ред. 2009 года.pdf and some other random wishes.
-- Ivan Zakharyaschev <imz@altlinux.org>.

(Read the git log... I tried to explain each change clearly.)


#### Благодарности
[Ростислав Листеренко](https://github.com/kaedvann) (сообщения об ошибках)

## См. также
### Статьи
[Записки дебианщика](http://mydebianblog.blogspot.nl/2008/11/latex.html)

### Репозитории
[@qrilka: порт второй версии на `XeLaTeX`](https://github.com/qrilka/G7-32)

[@petethepig: порт урезанной третьей версии ("под себя") на `XeLaTeX`](https://github.com/petethepig/diploma)
