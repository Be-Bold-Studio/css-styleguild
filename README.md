# Руководство по написанию CSS-кода

Данное руководство основано на стайлгайдах от [@mdo](https://github.com/mdo/code-guide), [Sass Guideguide](https://sass-guidelin.es) и [Idiomatic CSS](https://github.com/necolas/idiomatic-css). 

Все разработчики организации обязаны придерживаться данного руководства.

Это «живой документ», и новые идеи всегда приветствуются. Вы можете внести свой вклад сделав pull-request или создав новое [issue](https://github.com/Be-Bold-Studio/css-styleguide/issues).

## Содержание

1. [Синтаксис и форматирование](#syntax)
2. [Порядок объявления](#declaration-order)
3. [Именование классов](#naming)
4. [Сокращенная запись](#shornings)
5. [Вложенность в SCSS](#scss-nesting)
6. [Организация кода](#code-organization)
7. [Комментарии](#comments)

<a name="syntax"></a>

## 1. Синтаксис и форматирование

Формат записи кода должен гарантировать, что код легко читается; единообразен; что его легко комментировать; должен минимизировать шанс случайного внесения ошибки; и обеспечивать удобство чтения сообщений внутри системы управления версиями.

- **Используй мягкие отступы с двумя пробелами.** Только в случае использования пробелов можно гарантировать, что твой код будет везде одинаково выглядеть.

- **Используй двойные кавычки**

- **При группировке селекторов помещай каждый селектор на отдельную строку.**

- **Перед открывающей фигурной скобкой `{` ставь один пробел.**

- **Помещай закрывающую фигурную скобку `}` на новой строке.**

- **Размещай каждое объявление на отдельной строке.** Это нужно для более точного сообщения об ошибках.

- **Добавляй один уровень отступов перед каждым объявлением.**

- **Оставляй один пробел после `:` для каждого объявления.**

- **Завершай все объявления точкой с запятой.** Для последнего объявления в блоке это не является обязательным, но в противном случае твой код будет более подвержен ошибкам.

- **Для свойств, значения которых разделены запятыми, оставляй по одному пробелу после каждой запятой (например, `box-shadow`).**

- **Значения цветов записывай строчными буквами (в нижнем регистре) в полном формате (6 цифр для значений без альфа-канала, 8 цифр для значений с альфой).** Например, `#ffffff` вместо `#FFF`Строчные буквы гораздо легче различить при просмотре файла, поскольку они, как правило, имеют больше уникальных форм.

<!-- - **Не оставляй пробелов после запятых внтури значений `rgb()`, `rgba()`, `hsl()`, `hsla()`, или `rect()`.** Это помогает различать различные цветовые значения (запятая без пробела) от нескольких значений одного свойства (запятая с пробелом). -->

- **Всегда добавляй начальный ноль для значений** (например, `0.5` вместо `.5`).

- **Всегда бери в кавычки значения атрибутов внутри селектора**, например, `input[type="text"]`. В некоторых случаях это делать необязательно, но это является хорошей практикой для поддержки согласованности кода.

- **Опускай единицы измерения при нулевом значении**, например, `margin: 0;` вместо `margin: 0px;`.

- **Записывай селекторы по тэгу строчными буквами (в нижнем регистре)**, например `section` вместо `SECTION`

- **Разделяй правила пустой строкой.**

### Пример

#### Плохо :no_entry:
```css
.selector, .selector-secondary, .selector[type=text]{
padding:15px;
margin:0px 0px 15px;
background-color:rgba(0, 0, 0, .5);
box-shadow:0px 1px 2px #CCC,inset 0px 1px 0px #FFFFFF}
```

#### Хорошо :white_check_mark:
```css
.selector,
.selector-secondary,
.selector[type="text"] {
    padding: 15px;
    margin: 0 0 15px;
    background-color: rgba(0, 0, 0, 0.5);
    box-shadow: 0 1px 2px #cccccc, inset 0 1px 0 #ffffff;
}
```
### Исключения и небольшие отклонения
К большим группам правил, состоящих из одного свойства, может применяться запись в одну строку. В таком случае следует ставить пробел после открывающей и перед закрывающей скобками. Ключевым фактором здесь является удобство обнаружения ошибок.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Длинные значения свойств, разделяемые запятыми — как, например, набор градиентов или теней — могут быть помещены на отдельной строке каждое, чтобы повысить читабельность кода и сообщений в системе управления версиями. Формат записи может слегка различаться, один из вариантов приведён ниже.

```css
.selector {
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
}
```


<a name="declaration-order"></a>

## 2. Порядок объявления

Объявления логически связанных свойств должны быть группируй в следующем порядке:

1. Позиционирование
2. Блочная модель
3. Типографика
4. Отображение
5. Прочее

Позиционирование следует первым потому, что оно может удалить элемент из нормального потока документа и переопределить блочную модель связанных стилей. Блочная модель идет следующей, так как она диктует размеры и расположение компонента.

Все остальные объявления, выполняющиеся внутри компонента или не оказывающие влияния на предыдущие два раздела, следуют в последнюю очередь.

Группы свойств разделяй пустой строкой.

Перед каждой группой свойств добавляй комментарий с названием этой группы: `Positioning`, `Box model`, `Typography`, `Visual` и `Misc`.

В рамках групп `Positioning` и `Box model` объявления сортируются логически (сначала более влиятельные, затем менее). В рамках остальных групп в алфавитном порядке.

### Пример
``` css

.declaration-order {
    /* Positioning */
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;

    /* Box model */
    display: block;
    float: right;
    width: 100px;
    height: 100px;

    /* Typography */
    color: #333333;
    font: normal 13px "Helvetica Neue", sans-serif;
    line-height: 1.5;
    text-align: center;

    /* Visual */
    background-color: #f5f5f5;
    border: 1px solid #e5e5e5;
    border-radius: 3px;

    /* Misc */
    opacity: 1;
}
```

<a name="naming"></a>

## 3. Именование классов

Для именования классов используй **BEM-naming**, стиль **Two Dashes**. Подробнее на [сайте методологии](https://ru.bem.info/methodology/naming-convention/).

### Правила формирования имён
- Имена записывай латиницей в нижнем регистре.
- Используй английский язык. Транслит это **очень плохо**. Если не знаешь как то или иное понятие называется по-английски используй [переводчик](https://translate.google.com)
- Для разделения слов в именах используй дефис (`-`). Но, по возможности, избегай длинных имён в два слова и более.
- Избегай слишком длинных и слишком коротких имён
- Применяй сокращения только для длинных имён. Например, не стоит сокращать `button` до `btn`. Но в случае с `recommendation` следует задуматься о поиске альтернативы.
- Имя элемента отделяй от имени блока двумя подчеркиваниями (`__`)
- Имя модификатора отделяй от имени блока или элемента двумя дефисами (`--`).

#### Пример
Примерно вот какой логике должен следовать программист при именовании блока.

0. Исходная задача: придумать имя `блоку с рекламой`.
1. (опционально). При незнании английского приходит в голову `.reklamniy-blok`. Но это **очень плохо**.
2. Находим английские названия `advertising`, `advertisement`, `ad`. Получаем названия классов `.advertising-block`, `.advertisement-block`, `.ad-block`. Но это не очень подходящие названия, т.к. некоторые слишком длинные, а некоторые могут блокироваться различными плагинами, фильтрующими рекламу. А нам явно не нужна блокировка собственного контента.
3. Находим альтернативное название `.promotion-block`. Уже лучше.
4. Мы используем БЭМ, поэтому можно часть названия с блоком упустить. Получаем `.promotion`.
5. Сокращаем по возможности. В данном случае есть общепринятое сокращение. И получаем идеальный вариант — `.promo`.


<a name="shortnings"></a>

## 4. Сокращенная запись

Старайся ограничить использование сокращенных объявлений в тех случаях, когда необходимо явно задать все доступные значения. Наиболее часто злоупотребляют сокращением следующих свойств:

- padding
- margin
- font
- background
- border
- border-radius

Часто нам не нужно устанавливать все значения сокращенной записи свойства. Например, HTML заголовки устанавливают только отступы сверху и снизу, таким образом, в случае необходимости нужно переопределить только эти два значения. Чрезмерное использование сокращенной записи свойств часто приводит к грязному коду с ненужными переопределения и непреднамеренными побочными эффектами.

На сайте Mozilla Developer Network есть отличная статья о [сокращенной записи свойств](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties) для тех кто не знаком с такой формой записи.

### Пример 

#### Плохо :no_entry:
```css
.block {
    margin: 0 0 10px;
    background: red;
    background: url("image.jpg");
    border-radius: 3px 3px 0 0;
}
```

#### Хорошо :white_check_mark:
```css
.block {
    margin-bottom: 10px;
    background-color: red;
    background-image: url("image.jpg");
    border-top-left-radius: 3px;
    border-top-right-radius: 3px;
}
```

<a name="scss-nesting"></a>

## 5. Вложенность в SCSS

Избегай лишней вложенности. То, что ты можешь использовать вложенность, не означает, что это всегда надо делать. Зачастую вложенность элементов в блок усложняет чтение кода.

Когда применять вложенность:
- для псевдоэлементов `::before` и `::after`
- для всевдоклассов `:hover`, `:active`, `:checked` и т. п.
- для медиазапросов и миксинов их реализующих.
- для модификаторов (`&--modifier`)

Когда **НЕ** применять вложенность:
- для элементов (`.block__element`, а не `.block` &rarr; `&__element`)
- для дочерних элементов, если нужно сократить область видимости (`.block__text p`, а не `.block` &rarr; `&__text` &rarr; `& p`)
- если уровень вложенности больше трёх.

Если кратко: **один элемент DOM — одно правило**.

### Пример 

#### Плохо :no_entry:
```scss
.block {
    color: green;

    &__element-1 {
        color: red;

        &:hover {
            color: tomato;
        }
    }

    &__element-2 {
        color: orange;

        & p {
            color: blue;
        }
    }
}
```

#### Хорошо :white_check_mark:
```scss
.block {
    color: green;
}

.block__element-1 {
    color: red;

    &:hover {
        color: tomato;
    }
}

.block__element-2 {
    color: orange;
}

.block__element-2 p {
    color: blue;
}
```

<a name="code-organization"></a>

## 6. Организация кода

Придерживайся следующей структуры проекта для стилей.

```
sass/
|- base/
|   |- _global.scss
|   |- _mixins.scss
|   |- _vars.scss
|   |- _wordpress.scss
|
|- fonts/
|   |- _fonts.scss
|   |- _icons.scss
|
|- modules/
|   |- _about.scss
|   |- _button.scss
|   |- _contact.scss
|   ... Etc.
|
`- styles.scss
```
- В директории `base` следует размещать файлы базовых стилей, стили, миксины и переменные.
- В директории `fonts` — стили шрифтов и иконок
- В директории `modules` — стили отдельных блоков проекта
- Файл styles.scss — основной файл стилей. В нём должны содержаться только директивы `@import` и комментарии




<a name="comments"></a>

## 7. Комментарии

CSS синтаксически достаточно простой язык, но «благодаря» огромному многообразию браузеров и техник написания, может быть очень каверзным. Поэтому пиши комментарии по поводу:
- структуры и/или роли файла;
- цели правила;
- идеи, которая стоит за «магическими» числами;
- причин объявления неочевидных правил;
- [порядка объявления](#declaration-order);
- идеи, которая является основой того или иного решения;
- и особенно «грязные хаки».

Комментирование прямо в процессе написания кода, занимает намного меньше времени, по сравнению с тем временем, которое ты потратишь потом, вспоминая почему принял именно это решение.

![The End](the-end.jpg)
