
Отдельный класс задач, который не может обойтись без циклов, называется агрегированием данных. К таким задачам относятся поиск максимального, минимального, суммы, среднего арифметического и т.п. Их главная особенность в том, что результат зависит от всего набора данных. Для расчета суммы нужно сложить **все** числа, для вычисления максимального нужно сравнить **все** числа.

С такими задачами хорошо знакомы все, кто занимаются с числами, например бухгалтеры или маркетологи. Обычно их выполняют в таблицах наподобие Microsoft Excel или Google Tables.

Разберем самый простой пример – поиск суммы набора чисел. Реализуем функцию, которая складывает числа в указанном диапазоне, включая границы. Диапазоном в данном случае называется ряд чисел от какого-то начала до определенного конца. Например, диапазон [1, 10] включает в себя все целые числа от 1 до 10.

```javascript
sumNumbersFromRange(5, 7); // 5 + 6 + 7 = 18
sumNumbersFromRange(1, 2); // 1 + 2 = 3

// [1, 1] диапазон с одинаковым началом и концом – тоже диапазон
// он в себя включает ровно одно число – саму границу диапазона
sumNumbersFromRange(1, 1); // 1
sumNumbersFromRange(100, 100); // 100
```

Для реализации этого кода нам понадобится цикл, так как сложение чисел – это итеративный процесс (он повторяется для каждого числа), а количество итераций зависит от размера диапазона. Перед тем, как смотреть код, попробуйте ответить на вопросы ниже:

* Каким значением инициализировать счетчик?
* Как он будет изменяться?
* Когда цикл должен остановиться?

Попробуйте сначала подумать над этими вопросами, а затем посмотрите код ниже:

```javascript
const sumNumbersFromRange = (start, finish) => {
  // Технически можно менять start
  // Но входные аргументы нужно оставлять в исходном значении
  // Это сделает код проще для анализа
  let i = start;
  let sum = 0; // Инициализация суммы

  while (i <= finish) { // Двигаемся до конца диапазона
    sum = sum + i; // Считаем сумму для каждого числа
    i = i + 1; // Переходим к следующему числу в диапазоне
  }

  // Возвращаем получившийся результат
  return sum;
};
```

https://replit.com/@hexlet/js-basics-aggregation-numbers

Общая структура цикла здесь стандартна. Есть счетчик, который инициализируется начальным значением диапазона, есть сам цикл с условием остановки при достижении конца диапазона, и, наконец, изменение счетчика в конце тела цикла. Количество итераций в таком цикле равно `finish - start + 1`. То есть для диапазона от 5 до 7 – это 7 - 5 + 1, то есть 3 итерации.

Главные отличия от обычной обработки связаны с логикой вычислений результата. В задачах на агрегацию всегда есть какая-то переменная, которая хранит внутри себя результат работы цикла. В коде выше это `sum`. На каждой итерации цикла происходит её изменение, прибавление следующего числа в диапазоне: `sum = sum + i`. Весь процесс выглядит так:

```javascript
// Для вызова sumNumbersFromRange(2, 5);
let sum = 0;
sum = sum + 2; // 2
sum = sum + 3; // 5
sum = sum + 4; // 9
sum = sum + 5; // 14
// 14 – результат сложения чисел в диапазоне [2, 5]
```

У переменной `sum` есть начальное значение, равное 0. Зачем вообще задавать значение? Любая повторяющаяся операция начинается с какого-то значения. Нельзя просто так объявить переменную и начать с ней работать внутри цикла. Это приведет к неверному результату:

```javascript
// начальное значение не задано
// js автоматически делает его равным undefined
let sum;

// первая итерация цикла
sum = sum + 2; // ?
```

В результате такого вызова внутри `sum` окажется `NaN`, то есть не число. Оно возникает из-за попытки сложить `2` и `undefined`. Значит какое-то значение всё же нужно. Почему в коде выше выбран 0? Очень легко проверить, что все остальные варианты приведут к неверному результату. Если начальное значение будет равно 1, то результат получится на 1 больше, чем нужно.

В математике существует понятие **нейтральный элемент операции** (у каждой операции свой элемент). Это понятие имеет очень простой смысл. Операция с этим элементом не изменяет то значение, над которым проводится операция. В сложении любое число плюс ноль дает само число. При вычитании – то же самое. Даже у конкатенации есть нейтральный элемент – это пустая строка: `'' + 'one'` будет 'one'.

Вопрос на самопроверку. Какой нейтральный элемент у операции умножения? Для ответа на этот вопрос, найдите число, которое не меняет любые другие числа при умножении на него.

<details>
<summary>Ответ</summary>

Нейтральный элемент умножения — 1.

</details>