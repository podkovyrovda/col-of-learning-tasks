
# #15 Сбалансированы ли скобки?

> Реализуйте и экспортируйте функцию по умолчанию, которая принимает на вход строку, состоящую только из открывающих и закрывающих круглых скобок, и проверяет является ли эта строка корректной. Пустая строка (отсутствие скобок) считается корректной.

Строка считается корректной (сбалансированной), если содержащаяся в ней скобочная структура соответствует требованиям:

Скобки — это парные структуры. У каждой открывающей скобки должна быть соответствующая ей закрывающая скобка.
Закрывающая скобка не должна идти впереди открывающей.


```js
//js code
const lenth = (str) => str.length

const areBracketsBalanced = (str) => {
  if (length(str) % 2 !== 0) {
    return false;
  }
  
  let countOfOpenBrackets = 0;
  let countOfCloseBrackets = 0;

  for (let i = 0; i < length(str); i += 1) {
    if (str[i] === '(') {
      countOfOpenBrackets += 1;
    } else
    countOfCloseBrackets += 1;
      if ((countOfOpenBrackets - countOfCloseBrackets) < 0 ) {
        return false;
      };
  };
  return countOfOpenBrackets === countOfCloseBrackets;
}
```
# #14 Без двух нулей

> Реализуйте и экспортируйте по умолчанию функцию, которая принимает на вход два аргумента - количество нулей и количество единиц, и определяет сколько есть способов размещения этих нулей и единиц так, что бы не было двух нулей идущих подряд.

Например, определим все способы размещения двух нулей и двух единиц. Существует шесть возможных способов размещения: 0011, 0101, 0110, 1001, 1010, 1100. В трех случаях содержится два нуля, идущих подряд: 0011, 1001 и 1100. Вычитаем их из общего числа и получаем три возможных способа: 0101, 0110 и 1010. Ответ - 3.

```js
//js code
const factorial = num => {
    let result = 1;
    for (let i = 1; i <= num; i += 1) {
      result = result * i;
    }
    return result;
  }

const allVariantes = (a, b) => factorial(a + b) / (factorial(a) * factorial(b));

const withoutTwoZeros = (zeros, ones) => {
  if (zeros > 2) {
    return allVariantes(zeros, ones) - (allVariantes(zeros - 2, ones + 1) * allVariantes(zeros - 2, ones) - allVariantes(zeros - 2, ones));
  } else
  if (zeros === 2) {
    return allVariantes(zeros, ones) - allVariantes(zeros - 1, ones);
  } else
  return allVariantes(zeros, ones);
}
```

> 

```js
//js code

```
# #13 Степень тройки

> Реализуйте и экспортируйте по умолчанию функцию isPowerOfThree, которая определяет, является ли переданное число натуральной степенью тройки. Например, число 27 — это третья степень: 3^3, а 81 — это четвёртая: 3^4.

```js
//js code
const isPowerOfThree = num => {
  if (num === 1) {
    return true;
  }
  if (num % 3 !== 0) {
    return false;
  }
  for (let i = 0; num !== 1; i += 1) {
    if (num % 3 === 0) {
    num = num / 3;
    } else
    return false;
  }
return true;
}
```
# #12 Счастливый билет

> Счастливым билетом называют такой билет с шестизначным номером, где сумма первых трех цифр равна сумме последних трех.

Например, билет с номером 385916 - счастливый, так как 3 + 8 + 5 = 9 + 1 + 6

Напишите и экспортируйте по умолчанию функцию, проверяющую является ли номер счастливым (номер может быть как числового, так и строкового типа: см. примеры ниже). Функция должна возвращать true, если билет счастливый, или false, если нет.

```js
//js code
const length = (str) => str.length
const substr = (str) => str.substr


const isHappyTicket = str => {
  if (String(str) !== str) {
    str = String(str);
  }
  let sumOfFirstThreeDigits = 0;
  let sumOfLastThreeDigits = 0;
  for (let i = 0; i <= 2; i += 1) {
    sumOfFirstThreeDigits += Number(str[i]);
  }
  for (let i = 3; i <= 5; i += 1) {
    sumOfLastThreeDigits += Number(str[i]);
  }
  return sumOfFirstThreeDigits === sumOfLastThreeDigits;
} 
```
# #11 - Счастливые числа


```js
//js code

```
# #10 Преобразование DNA в RNA

> Реализуйте и экспортируйте функцию по умолчанию, которая принимает на вход цепь ДНК и возвращает соответствующую цепь РНК (совершает транскрипцию РНК).

Цепь РНК составляется на основе цепи ДНК последовательной заменой каждого нуклеотида:

G -> C
C -> G
T -> A
A -> U

Если во входном параметре нет ни одного нуклеотида (т.е. передана пустая строка), то функция должна вернуть пустую строку. Если в переданной цепи ДНК встретится "незнакомый" нуклеотид (не являющийся одним из четырех перечисленных выше), то функция должна вернуть null.

```js
//js code
const length = (str) => str.length

const dnaToRna = (str) => {
  let result = '';
  let i = 0;
  while (i < length(str)) {
    switch (str[i]) {
      case 'A':
        result += 'U';
        break;
      case 'T':
        result += 'A';
        break;
      case 'C':
        result += 'G';
        break;
      case 'G':
        result += 'C';
        break;
      default:
        return null;
    }
    i += 1;
  }
  return result;
};
```
# #9 Функция Аккермана

> Функция Аккермана — простой пример вычислимой функции, которая не является примитивно рекурсивной.

Она обозначается A(m,n), принимает два неотрицательных целых числа в качестве параметров и возвращает натуральное число. Эта функция растёт очень быстро, например, число A(4,4) настолько велико, что количество цифр в порядке этого числа многократно превосходит количество атомов в наблюдаемой части Вселенной.

```js
//js code
const ackermann = (m, n) => {
  if (m < 0 || n < 0) {
    return undefined;
  }
  if (m === 0) {
    return n + 1;
  }
  if (m > 0, n === 0) {
    return ackermann(m - 1, 1);
  }
  return ackermann(m - 1, ackermann(m, n - 1));
} 
```
# #8 Форматированное время

> Реализуйте и экспортируйте по умолчанию функцию, которая принимает на вход количество минут (прошедших с начала суток) и возвращает строку, являющуюся временем в формате чч:мм.

```js
//js code
const formattedTime = (num) => {
  const hours = Math.floor(num / 60);
  const minutes = num - hours * 60;
  const formattedHours = hours < 10 ? '0' + hours : hours; 
  const formattedMinutes = minutes < 10 ? '0' + minutes : minutes; 
  return formattedHours + ':' + formattedMinutes;
}
```
# #7 - Переворот строки

> Реализуйте и экспортируйте функцию по умолчанию, которая переворачивает строку задом наперед, используя рекурсию.

```js
//js code

```
# #6 Инвертированный регистр

> Реализуйте и экспортируйте по умолчанию функцию invertCase, которая меняет в строке регистр каждой буквы на противоположный.

```js
//js code
const length = (str) => str.length

const invertCase = str => {
  let result = '';
  for (let i = 0; i < length(str); i += 1) {
    if (str[i] === str.toUpperCase(str)[i]) {
      result += str.toLowerCase(str)[i];
    } else
    result += str.toUpperCase(str)[i];
  }
  return result;
}
```
# #5 Переворот числа

> Реализуйте и экспортируйте по умолчанию функцию reverseInt, которая переворачивает цифры в переданном числе и возвращает новое число.

```js
//js code
const length = (str) => str.length;

const reverseInt = num => {
  let numAbs = Math.abs(num);
  let result = '';
  for (let i = length(String(numAbs)) - 1; i >= 0; i -= 1) {
    result = result + String(numAbs)[i];
  }
  if (num < 0) {
    return Number('-' + result);
  }
  return Number(result);
}
```
# #4 Fizz Buzz

> Реализуйте и экспортируйте по умолчанию функцию, которая выводит (console.log) в терминал числа в диапазоне от begin до end. При этом:

Если число делится без остатка на 3, то вместо него выводится слово Fizz
Если число делится без остатка на 5, то вместо него выводится слово Buzz
Если число делится без остатка и на 3, и на 5, то вместо числа выводится слово FizzBuzz
В остальных случаях выводится само число
Функция принимает два параметра (begin и end), определяющих начало и конец диапазона (включительно). Для простоты считаем, что эти параметры являются целыми числами больше нуля. Если диапазон пуст (в случае, когда begin > end), то функция просто ничего не печатает.

```js
//js code
const fizzBuzz = (begin, end) => {
  for (let i = begin; i <= end; i += 1) {
    if (i % 3 === 0 && i % 5 === 0) {
      console.log('FizzBuzz');
    } else
    if (i % 3 === 0) {
      console.log('Fizz');
    } else
    if (i % 5 === 0) {
      console.log('Buzz')
    } else
    console.log(i);
  }
}
```
# #3 Сумма квадратов 

> Напишите функцию sumSquareDifference, которая принимает аргумент n и возвращает разницу между квадратом суммы и суммой квадратов первых n натуральных чисел.

```js
//js code
const sumSquareDifference = num => {
  let sumSquare = 0;
  let sum = 0;
  for (let i = 0; i <= num; i += 1) {
    sumSquare += i ** 2;
    sum += i;
  }
  return sum ** 2 - sumSquare;
}
```
# #2 Идеальные числа

> Создайте функцию isPerfect, которая принимает число и возвращает true, если оно совершенное, и false — в ином случае.

```js
//js code
const isPerfect = num => {
  if (num === 0) {
    return false;
  }
    let i = 0;
    let sumOfDivisors = 0;
    while (i < num) {
      if (num % i === 0) {
        sumOfDivisors += i;
      }
      i += 1;
    }
  return num === sumOfDivisors;
}
```
# #1 Разница углов

> Напишите функцию diff, которая принимает два угла (integer), каждый от 0 до 360, и возвращает наименьшую разницу между ними.

```js
//js code
const diff = (integer1, integer2) => {
  if (Math.abs(integer1 - integer2) < 360 - Math.abs(integer1 - integer2)) {
    return Math.abs(integer1 - integer2);
  }
  return 360 - Math.abs(integer1 - integer2);
}
```

// Template

# 

> 

```js
//js code

```