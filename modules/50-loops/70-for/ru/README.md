
Цикл `while` идеален для ситуаций, когда количество итераций неизвестно заранее, например, при поиске простого числа. Когда количество итераций известно, предпочтительнее использовать цикл `for`.

Посмотрим реализацию переворота строки через цикл `for`:

```javascript
const reverseString = (str) => {
  let result = '';
  for (let i = 0; i < str.length; i += 1) {
    result = `${str[i]}${result}`;
  }

  return result;
};
```

https://replit.com/@hexlet/js-basics-for

Можно читать так: *цикл с индексом `i` повторяется пока `i < str.length` и после каждого шага увеличивает `i` на 1*.

В определении цикла `for` в круглых скобках есть три выражения, разделённые точкой с запятой:

1. Начальное значение счётчика. Этот код выполняется ровно один раз перед первой итерацией.
2. Предикат — условие повторения циклов. Выполняется на каждой итерации. Точно так же как и в `while`
3. Описание изменения счётчика. Этот код выполняется в конце каждой итерации.

В остальном принцип работы точно такой же, как у цикла `while`.

В определении `for` не обязательно указывать все три выражения. Если не указать условие повторения цикла, то цикл будет выполняться бесконечно:

```javascript
let i = 1;
// Можно даже не указывать все три выражения
for (;;) {
  console.log(i);
  i += 1;
}
```