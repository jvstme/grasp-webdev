# Навигация по DOM

Часто удобнее не искать нужный элемент от корня документа, то есть через `document.querySelector` или `document.querySelectorAll`, а "перейти" к нему от уже найденного элемента, находящегося поблизости. Рассмотрим, как это сделать.

Для всех примеров в этой главе будем использовать такой HTML-документ:

```html
<!DOCTYPE html>
<html>
    <body>
        <ul>
            <li class="li-1"><span class="span-1">First</span></li>
            <li class="li-2"><span class="span-2">Second</span></li>
            <li class="li-3"><span class="span-3">Third</span></li>
        </ul>
    </body>
</html>
```

### Переход к родительскому элементу

Имея объект элемента, получить объект его родительского элемента можно через свойство `parentElement`. Если у элемента нет родителя, то свойство принимает значение `null`.

```js
const list = document.querySelector("ul");
list.parentElement;                              // Возвращает: элемент <body>
list.parentElement.parentElement;                // Возвращает: элемент <html>
list.parentElement.parentElement.parentElement;  // Возвращает: null
```

### Переход к дочерним элементам

Имея объект элемента, можно воспользоваться методами этого элемента `querySelector` и `querySelectorAll`, чтобы найти объекты его дочерних элементов, как мы уже [обсуждали ранее](querying_elements_inside_other_elements.md). Однако эти методы ищут по всему дереву потомков элемента, то есть могут найти не только дочерние элементы, но и дочерние дочерних, дочерние дочерних дочерних и так далее.

```js
const list = document.querySelector("ul");
list.querySelectorAll("li");    // Возвращает: NodeList из трёх элементов <li>
list.querySelectorAll("span");  // Возвращает: NodeList из трёх элементов <span>
```

Если же нужны *только* дочерние элементы, то их полный список можно получить через свойство `children`. Свойство содержит в себе объект типа `HTMLCollection`, который подобен массиву.

```js
list.children;           // Возвращает: HTMLCollection из трёх элементов <li>
list.children[0];        // Возвращает: элемент <li class="li-1">
list.children.length;    // Возвращает: 3
```

### Переход к сестринским элементам

Имея объект некого элемента, при помощи свойства `previousElementSibling` можно получить объект сестринского элемента, находящегося в DOM строго перед данным. Если такого элемента нет, например если данный элемент является первым внутри своего родителя, то свойство принимает значение `null`.

```js
const middleItem = document.querySelector(".li-2");
middleItem.previousElementSibling;                         // Возвращает: элемент <li class="li-1">
middleItem.previousElementSibling.previousElementSibling;  // Возвращает: null
```

Аналогично, свойство `nextElementSibling` содержит объект сестринского элемента, следующего строго после данного, либо `null`, если за данным элементом не следует других сестринских элементов.

```js
middleItem.nextElementSibling;                     // Возвращает: элемент <li class="li-3">
middleItem.nextElementSibling.nextElementSibling;  // Возвращает: null
```

## Упражнения

1. Реализуй список с удаляемыми элементами. Рядом с каждым элементом списка должна быть кнопка удаления, при нажатии на которую этот элемент удаляется. В программе должен быть только один обработчик событий.

1. Реализуй список с перемещаемыми элементами. Рядом с каждым элементом списка должны быть две кнопки: перемещения вниз на одну позицию и перемещения вверх на одну позицию. В программе должно быть не более двух обработчиков событий.

1. Сделай страницу с двумя списками дел: по дому и по учёбе. Перед каждым списком должно быть собственное поле ввода и кнопка "Добавить". При помощи поля и кнопки можно добавлять новые элементы в соответствующий список. Для реализации используй только один обработчик событий, общий для двух списков.

1. Реализуй страницу настроек видеоигры. На странице можно установить 3 настройки: громкость музыки, громкость звуков и сложность игры.

    Каждая настройка задаётся при помощи инструмента, состоящего из 10 ячеек, иллюстрирующих уровень, на который настройка установлена. Изначально в первой ячейке указана отметка `+`, а в остальных указан прочерк `-`. Это означает, что настройка установлена на 1/10 от максимума.

    <table><tr><td>+</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td></tr></table>

    Чтобы поменять значение настройки, пользователь жмёт на одну из ячеек. Например, если пользователь хочет установить настройку на 7/10 от максимума, то он нажмёт на седьмую ячейку, после чего инструмент должен выглядеть так:

    <table><tr><td>+</td><td>+</td><td>+</td><td>+</td><td>+</td><td>+</td><td>+</td><td>-</td><td>-</td><td>-</td></tr></table>