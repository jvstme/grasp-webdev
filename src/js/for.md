# Цикл for

Часто с циклами встречаются конструкции, в которых перед циклом инициализируется переменная, отслеживающая ход цикла, а в конце каждой итерации переменная обновляется.

```js
let i = 0;

while (i < 10) {
    console.log(i);
    i++;
}
```

Для более компактной записи таких случаев существует цикл `for`.

```js
for (let i = 0; i < 10; i++) {
    console.log(i);
}
```

В скобках после ключевого слова `for` указываются три высказывания через точку с запятой: первое выполнится один раз перед первой итерацией; второе выполняется перед каждой итерацией и определяет, нужно ли продолжать итерации; третье выполняется после каждой итерации. В фигурных скобках указывается тело цикла, выполняющееся на каждой итерации.

Эти два примера отличаются только тем, что в случае `for` переменная `i` оказывается привязанной к области видимости цикла, то есть после завершения итераций переменная перестаёт существовать. В примере с `while` переменная объявляется за пределами цикла, поэтому после его завершения остаётся доступной.

## Упражнения

1. В математике факториал целого неотрицательного числа N — это произведение всех целых чисел от 1 до N включительно. Например, факториал 4 — \\( 1 \cdot 2 \cdot 3 \cdot 4 = 24 \\). Напиши скрипт, которые получает на вход целое неотрицательное число и выводит факториал этого числа.

1. Напиши скрипт, который получает на вход ширину и высоту прямоугольника и отображает заданный прямоугольник, "нарисованный" символами `#`. Например, если ширина `6`, а высота — `3`, то скрипт отобразит уведомление с текстом

    ```
    ######
    ######
    ######
    ```
