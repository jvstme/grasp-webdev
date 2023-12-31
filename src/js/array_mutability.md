# Изменяемость массивов

Как мы уже обсуждали, массивы являются изменяемыми. Например, в массив можно добавлять новые элементы или присваивать элементам новые значения. Это может приводить к неожиданному поведению, если один и тот же массив присвоен в разные переменные.

```js
const a = [1, 2];
const b = a;
```

Если добавить в `b` новый элемент...

```js
b.push(3);
b;  // Возвращает: [1, 2, 3]
```

...то окажется, что в `a` он тоже добавился, так как `a` и `b` ссылаются на один и тот же массив.

```js
a;  // Возвращает: [1, 2, 3]
```

Если такое поведение не является ожидаемым, то при создании новой переменной можно присваивать в неё не сам массив, а его копию, например сделанную методом `slice`.

```js
const c = [1, 2];
const d = c.slice();
d.push(3);
d;  // Возвращает: [1, 2, 3]
c;  // Возвращает: [1, 2]
```

## Упражнения

1. Работа нейронной сети зависит от массива числовых параметров. В процессе обучения сети каждый её параметр пробуют немного изменить, после чего проверяют, привело ли это к ухудшению или улучшению работы.

    Напиши программу, подбирающие параметры нейронной сети. На вход программе поступает исходный массив параметров. Программа должна сгенерировать как можно больше новых уникальных массивов, при этом каждый новый массив отличается от исходного тем, что ровно один из его параметров на 0.01 больше или на 0.01 меньше того же параметра из исходного массива. Все новые массивы нужно объединить в матрицу, то есть массив массивов, и вывести её в консоль. Длина исходного массива определяется пользователем.

    К примеру, если пользователь введёт три исходных параметра `[0.42, 0.53, 0.48]`, то программа выведет

    ```js
    [
        [0.41, 0.53, 0.48],
        [0.43, 0.53, 0.48],
        [0.42, 0.52, 0.48],
        [0.42, 0.54, 0.48],
        [0.42, 0.53, 0.47],
        [0.42, 0.53, 0.49],
    ]
    ```

    Обрати внимание, что при выполнении вычислений с вещественными числами могут получаться неточные результаты. Например, в результате `0.47 - 0.01` может получиться `0.45999999999999996`. Это нормально и связано с особенностями представления чисел в памяти компьютера.
