[Block-Engine] (http://webdesign.ru.net)
==============
**Система для удобства создания новых html-файлов (css, js, html блоки)**

###ЧТО ЭТО?

Сумма файлов (блоков) из которых можно быстро собрать необходимый вам сайт.


###ЗАЧЕМ?

Работая над темами для Ruxe-Engine я обратил внимание на то, что каждый раз заново пишу файл стилей. Но обязательно включаю в него определённые, уже ставшие привычными части, как например `Eric Meyer CSS reset`, стили `lightbox` и прочие необходимые части. Порой, открыв старый, написанный мною же файл стилей, я долго не мог его понять, так как уже забыл, почему я назвал так или иначе тот или иной блок. Для того, чтобы более не мучиться, я решил построить какую-то общую систему, логически понятную и достаточно универсальную.

Система будет содержать отдельные блоки, из которых можно будет "собрать" html-файл для дальнейшей работы по созданию сайта.

###ПРЕИМУЩЕСТВА РАБОТЫ С СИСТЕМОЙ

* **Не надо писать код "с нуля"** - Блоки-заготовки позволяют это делать быстро и качественно.
* **Оценка кода "на лету"** - Вы всегда можете запустить страничку для проверки работоспособности.
* **Доступность кода** - Код открытый и доступен для изменений.
* **Минимальный "вес" кода** - Но об этом ниже...

###МИНИМАЛЬНЫЙ ВЕС - ГЛАВНОЕ ПРЕИМУЩЕСТВО ЭТОЙ СИСТЕМЫ!

Я всегда пытался оптимизировать код своих сайтов, чтобы даже старенький смартфон, на любом тарифе, с ограничениями по скорости доступа в интернет и с ограничениями по объёму загруженного контента, "не тормозил". Поэтому в css-файлах я использую селекторы строки и подстроки (и стараюсь использовать их по-максимуму), не стесняюсь использовать мультиклассы, структурные псевдоклассы! Для понимания достаточно внимательно посмотреть код, который я выкладываю в этом проекте!

В дефинициях я не описываю какой-то определённый класс. Я даю определения ОБЩИМ классам. Если вы внимательно проанализируете  css-файлы, которые я здесь выкладываю, то вы обнаружите, что я использую метод **индукции** (Шерлок Холмс нервно курит в стороне), а не дедукции. Я описываю общие значения классов, а частные можно всегда добавить. То есть, если вы хотите с помощью моей системы задать "резиновый" блок шириной 80% с отступом 10% слева, то вам не надо объявлять этот класс. Вы просто пишете:

```html
	<div class="block-80-off-10">
	    <p>Содержание блока</p>
	</div>
```
	
Причём в файле **style.css** вы не найдёте класса `.block-80-off-10`! Его там просто нет, потому что дефиниции даются только ОБЩИМ значениям классов, а не частным вариантам. Так, к примеру, если вы решили создать мульти-блок шириной 90% с полями по краям в 5%, а в нём содержание в две колонки по 50%, то вы просто пишете такой код (все значения выдуманы, можете подставить свои):

```html
<div class="group-90-offset-05">
    <div class="block-50">
		Содержание блока №1
	</div>
	<div class="block-50">
		Содержание блока №2
	</div>
</div>
```

Имя класса `group-90-offset-05` обозначает, что это блок шириной 90% с полями слева и справа по 5%. Это "обёртка", за пределы которой не выходит содержание. Обёртку лучше всего "закрывать" классом "clearfix" для защиты от "выползания" содержимого за пределы обёртки. Классы `block-50` описывают два блока по 50% без отступов по краям. А если бы я захотел создать блок шириной 40% с левым отступом в 2%, то запись класса выглядела бы так - `.block-40-off-02`. **Если вы заметили, то такого описания в системе нет, но его можно добавить в процессе работы, используя синтаксис, который я вам предлагаю**. "Лишние", ненужные вам в этом проекте классы, можно просто удалить. Это ускорит загрузку сайта. 

Этим и отличается система! Вам не надо описывать КАЖДЫЙ класс. Вы просто пишете код, в котором сами определяете, какие описания класса подключить к этому, конкретному классу, который вы только что придумали! Это даёт огромную свободу творчества. Ведь вы же художник ё-моё, а не какой-то там "юзер-с-мышкой" ;) ! Сейчас передо мной стоит задача развития системы. Я не откажусь от посильной помощи тех, кто реально занимается веб-дизайном. Меня интересуют даже не ответы, а ваши вопросы! Я сейчас делаю систему "под себя". То есть, я реализую СВОИ запросы и требования. А мне хотелось бы, чтобы любой веб-художник поставил задачу и мы вместе нашли решение.

Давайте работать вместе!

###ПРИМЕЧАНИЕ

В состав проекта включил несколько директорий, в которых будут находиться вспомогательные файлы, необходимые для построения сайта и демонстрационные страницы:

`dir /css-collection` - готовые css-блоки

`dir /DEMO` - примеры работы с блоками

`dir /fonts-collection` - необходимые шрифты (font-awesome)

`dir /html-collection` - заготовки страниц разных стандартов (html5, loose, strict, transitional)

`dir /images-collection` - коллекция фоновых и вспомогательных изображений

`dir /js-collection` - необходимые скрипты

Они необходимы для того, чтобы пробный html-файл полностью функциональным.

Кроме того в систему включены блоки-заготовки, в которых содержатся части кода:

Название файла  | Содержание файла
----------------|----------------------
block.css       | Основные стили блоков системы
addition.css    | Дополнительные стили
fontawesome.css | Стили иконочного шрифта
layout.css      | Дополнительные стили, применительно к определённому сайту
lightbox.css    | Стили лайтбокса, если таковой используется
normalizercss   | Нормалайзер CSS от Nicolas Gallagher
reset.css       | Reset CSS от Эрика Мейера

Коллекция будет пополняться, поэтому содержание папок может оличаться от описанного здесь.

В корне проекта находятся файлы для "сборки" рабочей страницы (не забудьте указать кодировку файлов **utf-8 без BOM** в начале работы с ними).

Название файла  | Содержание файла
----------------|----------------------
index.html      | Индексный файл для проверки вносимых изменений
style.css       | Пустой файл каскадной таблицы стилей, в который производится сборка необходимых стилей

##ПРИНЦИПЫ РАБОТЫ С БЛОКАМИ

Скачайте архив проекта на свой компьютер и разархивируйте его. Теперь можно приступать к работе.

Система представляет из себя своего рода конструктор, пока ещё разобранный на блоки. Процесс сборки начинается с оформления файлов index.html и style.css, с добавления в них содержимого блоков и вспомогательных файлов и директорий.

Исходя из названия системы, главными в ней являются **блоки**. Блокам присваиваются классы `.group` и `.block`. Особой разницы в этих классах нет, они абсолютно идентичны. Разные названия я им присвоил только для того, чтобы легче было читать созданный код. Блоки класса `group` удобнее делать внешними. Они будут служить "обёрткой" для вкладываемых в них блоков с классом `block`. Такою "конструкцию" легче читать. Глаз сразу будет выхватывать внешний `div` и легко определять внутренние, даже если построение будет достаточно сложным!

В файле `block.css` даются описания основных блоков, которые вы всегда можете дополнить и изменить по своему усмотрению. Самое первое, что вы должны сделать, это понять принцип функционирования данной системы, чтобы получить лёгкий, понятный код. Проверяю я готовый код даже на IE8 (уж если он понял, то остальные уж точно поймут). Итак, я жду ваших "коммитов" и "пулл реквестов"!

**Система "block-engine" на данный момент существует и распространяется по свободной MIT лицензии.**
