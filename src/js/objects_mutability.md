# Изменяемость объектов

Объекты являются изменяемыми. Свойству объекта можно присвоить новое значение через оператор присваивания.

```js
const point = { x: 0, y: 0 };
point.x = 2;
console.log(point);  // Выводит: { x: 2, y: 0 }
```

Также через оператор присваивания можно задать объекту новое свойство, которого изначально не было.

```js
point.z = 1;
console.log(point);  // Выводит: { x: 2, y: 0, z: 1 }
```

Как и в случае с массивами, стоит помнить, что если несколько переменных ссылаются на один и тот же объект, то при изменении объекта через одну из переменных изменения отразятся и в остальных переменных.

```js
point2 = point;
point2.y = 9;
console.log(point);   // Выводит: { x: 2, y: 9, z: 1 }
console.log(point2);  // Выводит: { x: 2, y: 9, z: 1 }
```

Если это не является ожидаемым, то можно создать копию объекта, чтобы её можно было изменять независимо от оригинального объекта. Один из самых очевидных способов создать копию — явно перечислить все свойства, если они известны заранее.

```js
point3 = {
    x: point.x,
    y: point.y,
    z: point.z,
};
point3.y = 5;
console.log(point);   // Выводит: { x: 2, y: 9, z: 1 }
console.log(point3);  // Выводит: { x: 2, y: 5, z: 1 }
```

## Упражнения

1. В компьютерной игре в объекте персонажа хранятся данные о его имени, уровне и трёх характеристиках: силе, скорости и выносливости. Например:

    ```js
    {
        name: "Black Wizard",
        level: 14,
        strength: 91.3,
        speed: 101.8,
        stamina: 74.5,
    }
    ```

    Напиши функцию `levelUp`, принимающую объект персонажа и повышающую его уровень. В качестве бонуса за повышение функция также повышает все характеристики персонажа на 20%.

1. Напиши программу-симулятор, которая позволит пользователю управлять движением роботов по плоской карте.

    Карта представляет из себя плоскость размером M на N ячеек. Нижняя левая ячейка имеет координаты `(0; 0)`, верхняя правая — `(M - 1; N - 1)`. Значения M и N задаются пользователем при запуске симулятора.

    На карте одновременно могут находиться 0, 1 или несколько роботов. Каждый робот занимает одну ячейку, больше одного робота в ячейке находиться не может. Роботы могут перемещаться в соседние ячейки, в том числе по диагонали. За пределы карты роботы выезжать не могут.

    У каждого робота есть уникальный численный номер от 1 до бесконечности. Каждый робот ориентирован, то есть повёрнут своей передней частью, в одном из восьми направлений: `↑`, `↗`, `→`, `↘`, `↓`, `↙`, `←`, `↖`.

    В каждый момент времени пользователь может управлять только одним роботом, такой робот считается "выбранным".

    Пользователь может управлять роботами, вводя в симулятор текстовые команды:

    - `SPAWN` — добавить на карту нового робота в ячейку `(0; 0)` в ориентации `↗`.

    - `SELECT <N>` — выбрать робота с номером N.

    - `FORWARD` — переместить выбранного робота на одну ячейку в сторону, в которую робот ориентирован.

    - `BACK` — переместить выбранного робота на одну ячейку в сторону, противоположную той, в которую робот ориентирован.

    - `RIGHT` — повернуть выбранного робота вправо на 45°.

    - `LEFT` — повернуть выбранного робота влево на 45°.

    - `REMOVE` — удалить выбранного робота с карты.

    - `QUIT` — завершить работу симулятора.

    После выполнения каждой команды симулятор выводит список всех роботов. Для каждого робота отображается номер, координаты, ориентация и то, является ли он выбранным. Пример вывода:

    ```
    1: (0; 5) ↑
    2: (4; 4) ↗ selected
    3: (3; 1) ↓
    ```

    Если пользователь пытается выполнить недопустимое действие, например вывести робота за пределы карты, то симулятор не выполняет команду и сообщает подробности ошибки.
