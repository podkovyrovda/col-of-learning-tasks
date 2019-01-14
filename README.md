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