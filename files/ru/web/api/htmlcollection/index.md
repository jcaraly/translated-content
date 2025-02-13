---
title: HTMLCollection
slug: Web/API/HTMLCollection
translation_of: Web/API/HTMLCollection
---
{{APIRef("HTML DOM")}}

Интерфейс **`HTMLCollection`** является обобщённой коллекцией (объектом, ведущим себя подобно массиву) элементов (в порядке упоминания в документе) и предоставляет методы и свойства для получения хранящихся в нём элементов.

> **Примечание:** **Замечание:** Интерфейс назван `HTMLCollection` по историческим причинам. До стандарта DOM4 коллекции, реализующие данный интерфейс, использовались только для хранения HTML-элементов.

`HTMLCollection`, хранящая элементы DOM, является динамической. При изменении документа она моментально отражает все произведённые изменения.

## Свойства

- {{domxref("HTMLCollection.length")}} {{readonlyInline}}
  - : Возвращает количество элементов в коллекции.

## Методы

- {{domxref("HTMLCollection.item()")}}
  - : Возвращает узел с порядковым номером `index`; отсчёт ведётся от нуля. Возвращает `null`, если `index `выходит за границы допустимого диапазона.
- {{domxref("HTMLCollection.namedItem()")}}
  - : Возвращает узел, идентификатор или имя (в целях совместимости) которого совпадает со строкой, переданной в аргументе `name`. Соответствие имени проверяется в самую последнюю очередь, только для HTML-элементов и только для тех из них, которые поддерживают свойство `name`. Возвращает `null` , если искомый элемент отсутствует.

## Использование в JavaScript

`HTMLCollection` предоставляет своё содержимое как собственные свойства, доступные как по имени, так и по индексу (как в массиве). Это связано с тем, что идентификаторы HTML-элементов, содержащие точки и двоеточие (допустимо в HTML5), адресуемы исключительно через синтаксис доступа к массиву. Однако, при числовых идентификаторах невозможно определить, производится ли запрос по индексу или по идентификатору, неявно приведённому к числу.

Пусть в документе присутствует элемент `<form> `с `id,` равным «`myForm`»`:`

```js
var elem1, elem2;

// document.forms имеет тип HTMLCollection

elem1 = document.forms[0];
elem2 = document.forms.item(0);

alert(elem1 === elem2); // выводит "true"

elem1 = document.forms.myForm;
elem2 = document.forms.namedItem("myForm");

alert(elem1 === elem2); // выводит "true"

elem1 = document.forms["named.item.with.periods"];
```

## Поддержка браузерами

Браузеры по разному ведут себя при наличии нескольких элементов с одинаковыми индексами, либо значениями свойств `namedItem`. Firefox 8 действует в соответствии с DOM2 и DOM4, возвращая первое совпадение. Internet Explorer и браузеры на основе WebKit возвращают новый экземпляр `HTMLCollection`. Opera возвращает {{domxref("NodeList")}} со всеми найденными элементами.

## Спецификации

- [DOM Level 2 HTML, Section 1.4, Miscellaneous Object Definitions](http://www.w3.org/TR/DOM-Level-2-HTML/html.html#ID-75708506)
- [DOM4: HTMLCollection](http://www.w3.org/TR/domcore/#interface-htmlcollection)

## Смотрите также

- {{domxref("NodeList")}}
- {{domxref("HTMLFormControlsCollection")}}, {{domxref("HTMLOptionsCollection")}}
