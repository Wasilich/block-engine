[Block Engine] (http://webdesign.ru.net)
==============
###Система для удобства создания html-файлов (css, js, html блоки)

ЧТО ЭТО?
--------

Сумма файлов (блоков) из которых можно быстро собирать необходимый вам сайт.


ЗАЧЕМ?
------

Работая над темами для Ruxe-Engine я обратил внимание на то, что каждый раз заново пишу файл стилей. Но обязательно включаю в него определённые, уже ставшие привычными части, как например "Eric Meyer CSS reset", стили "lightbox" и прочие необходимые части. Порой, открыв старый, написанный мною же файл стилей, я долго не мог его понять, так как уже забыл, почему я назвал так или иначе тот или иной блок. Для того, чтобы более не мучиться, решил построить какую-то общую систему, логически понятную и достаточно универсальную.

Система будет содержать, как я предполагаю, отдельные блоки, из которых можно будет "собрать" html-файл для дальнейшей работы по созданию сайта.

В состав планирую включить несколько директорий, в которых будут находиться вспомогательные файлы, необходимые для построения сайта:

    dir /fonts
    dir /images
    dir /js

Они небходимы для того, чтобы пробный html-файл был достаточно наглядным при тестировании.

Кроме того в систему включены блоки-заготовки, в которых содержатся части кода:

Название файла  | Содержание файла
----------------|----------------------
style.css       | Пустой файл каскадной таблицы стилей, в который производится сбока необходимых стилей
reset.css       | Reset CSS от Эрика Мейера
normalize.css   | Нормалайзер CSS от Nicolas Gallagher
block.css       | Основные стили блоков системы
addition.css    | Дополнительные стили
fontawesome.css | Стили иконочного шрифта
layout.css      | Основные стили, применительно к определённому сайту
lightbox.css    | Стили лайтбокса, если таковой используется
index.html      | Индексный файл для проверки вносимых изменений

ПРИНЦИПЫ РАБОТЫ С БЛОКАМИ
-------------------------

Система представляет из себя своего рода конструктор, пока ещё разобранный на блоки. Процесс сборки начинается с оформления файлов /index/.html и /style/.css, с добавления в них содержимого блоков.

