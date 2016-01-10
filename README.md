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
style.css       | Пустой файл каскадной таблицы стилей, в который производится сборка необходимых стилей
reset.css       | Reset CSS от Эрика Мейера
normalize.css   | Нормалайзер CSS от Nicolas Gallagher
block.css       | Основные стили блоков системы
addition.css    | Дополнительные стили
fontawesome.css | Стили иконочного шрифта
layout.css      | Основные стили, применительно к определённому сайту
lightbox.css    | Стили лайтбокса, если таковой используется
index.html      | Индексный "пустой" файл для проверки вносимых изменений. Плюс индексные файлы разных стандартов html (strict, transitional, loose, html5), с готовыми шапками, в соответствии со стандартами.

ПРИНЦИПЫ РАБОТЫ С БЛОКАМИ
-------------------------

Система представляет из себя своего рода конструктор, пока ещё разобранный на блоки. Процесс сборки начинается с оформления файлов **index.html** и **style.css**, с добавления в них содержимого блоков.

Открываете пустые файлы index.html и style.css в любимом текстовом редакторе. В  index.html добавляете нужную вам шапку и общий код html, в соответствии с требованиями данного проекта. В style.css добавляете сначала необходимые для проекта общие части "по умолчанию". Например - содержание файла reset.css, затем уточняете стили, в соответствии с разметкой файла index.html.

Надеюсь, что с **составными классами** будет легко и приятно работать. Ведь в стилях не даются описания конкретных классов, а даются **общие** принципы стилей.

Например:
```css
    /* У нас есть несколько описаний классов */
    [class*=group-25], [class*=block-25] {width: 25%;}
    [class*=group-][class*=-off-05], [class*=block-][class*=-off-05] {margin-left: 5%;}
    [class*=group-][class*=-offset-05], [class*=block-][class*=-offset-05] {margin-left: 5%; margin-right: 5%;}
```
Такие стили позволяют нам не описывать класс полностью, а строить его по своему желанию. Например, присвоив блоку класс `.block-25` мы получим "резиновый" блок шириной 25%. Присвоив ему класс `.block-25-off-05` мы получим блок шириной 25% с отступом (margin) слева 5%. Присвоив ему класс `.block-25-offset-05` мы получим блок шириной 25% с отступами 5% с обеих сторон. Сочетая в классе разные свойства мы получаем необходимую свободу! Теперь можно легко добавлять и собственные классы, которые вам могут понадобиться, но которых не окажется в таблице стилей **block.css**.

Если вы заметили, то в стилях присутствуют классы `.group` и `.block`, которые описываются одинаково. Я сделал это специально, для удобства. Ведь блоки `div` будут вложены друг в друга. И такой текст будет сложнее читаться. Поэтому, для удобства работы с системой, выделяйте блоки-контейнеры, в которые вложены другие блоки, классом `.group`. Посмотрите пример:

```html
<div class="group-80-offset-10">
<div class="block-10 edge">
</div>
<div class="block-30-off-010">
<div class="content">
<p>Содержание блока</p>
</div>
</div>
<div class="block-30-off-010">
<div class="content">
<p>Содержание блока</p>
</div>
</div>
<div class="block-10 edge">
</div>
</div>
```

Этим вы облегчите себе работу с html-файлами. Глазами легче будет отличить внешний контейнер от внутреннего.
