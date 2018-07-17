# Руководство по написанию CSS-кода для :barber:«Oldboy&nbsp;Barbershop»:barber:

Данное руководство основано на стайлгайдах от [@mdo](https://github.com/mdo/code-guide), [Sass Guideguide](https://sass-guidelin.es) и [Idiomatic CSS](https://github.com/necolas/idiomatic-css). 

Все разработчики компании обязаны придерживаться данного руководства.

Это «живой документ», и новые идеи всегда приветствуются. Вы можете внести свой вклад сделав pull-request или создав новое [issue](https://github.com/nigel-riss/oldboy-styleguide/issues).

## Содержание

1. [Синтаксис и форматирование](#syntax)
2. [Порядок объявления](#order)
3. [Именование классов](#naming)
4. [Сокращенная запись](#shor)
5. [Вложенность в SCSS](#)
6. [Организация кода](#)
7. [Комментарии](#)

<a name="syntax"></a>
## 1. Синтаксис и форматирование

Формат записи кода должен гарантировать, что код легко читается; единообразен; что его легко комментировать; должен минимизировать шанс случайного внесения ошибки; и в результате обеспечивать удобство чтения сообщений внутри системы управления версиями.

- **Используй мягкие отступы с четырьмя пробелами.** Только в случае использования пробелов можно гарантировать, что твой код будет везде одинаково выглядеть. Четыре пробела для отступа делают код более читаемым, увеличение длины строк для CSS не играет особой роли, а увеличением размера файлов можно пренебречь, т. к. в релизных версиях проектов мы используем минификатор.

- **При группировке селекторов помещай каждый селектор на отдельную строку.**

- **Перед открывающей фигурной скобкой ставь один пробел.**

- **Помещай закрывающую фигурную скобку блока объявлений на новой строке.**

- **Размещай каждое объявление на отдельной строке.** Это нужно для более точного сообщения об ошибках.

- **Добавляй один уровень отступов перед каждым объявлением.**

- **Оставляй один пробел после `:` для каждого объявления.**

- **Завершай все объявления точкой с запятой.** Для последнего объявления в блоке это не является обязательным, но в противном случае твой код будет более подвержен ошибкам.

- **Для свойств, значения которых разделены запятыми, оставляй по одному пробелу после каждой запятой (например, `box-shadow`).**

- **Значения цветов записывай строчными буквами (в нижнем регистре) в полном формате (6 цифр).** Например, `#ffffff` вместо `#FFF`Строчные буквы гораздо легче различить при просмотре файла, поскольку они, как правило, имеют больше уникальных форм.

<!-- - **Не оставляй пробелов после запятых внтури значений `rgb()`, `rgba()`, `hsl()`, `hsla()`, или `rect()`.** Это помогает различать различные цветовые значения (запятая без пробела) от нескольких значений одного свойства (запятая с пробелом). -->

- **Всегда добавляй начальный ноль для значений** (например, `0.5` вместо `.5`).

- **Всегда берите в кавычки значения атрибутов внутри селектора**, например, `input[type="text"]`. В некоторых случаях это делать необязательно, но это является хорошей практикой для поддержки согласованности.

- **Опускай еединицы измерения при нулевом значении**, например, `margin: 0;` вместо `margin: 0px;`.

- **Записывай селекторы по тэгу строчными буквами (в нижнем регистре).**

- **Разделяй правила пустой строкой.**

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

## 2. Порядок объявления
## 3. Именование классов
## 4. Сокращенная запись
## 5. Вложенность в SCSS
## 6. Организация кода
## 7. Комментарии
## 