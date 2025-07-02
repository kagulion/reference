---
title: JavaScript
date: 2020-12-24 17:12:25
background: bg-[#ebd94e]
tags:
  - js
  - web
categories:
  - Programming
intro: |
  Шпаргалка по JavaScript с наиболее важными концепциями, функциями, методами и другим. Полное краткое справочное пособие для новичков.
plugins:
  - copyCode
  - runCode
---

## Начало работы

### Введение

JavaScript — это легковесный, интерпретируемый язык программирования.

- [Шпаргалка по JSON](/json) _(devsheet)_
- [Регулярные выражения в JavaScript](/regex#regex-in-javascript) _(devsheet)_

### Консоль

```javascript
// => Привет, мир!
console.log('Привет, мир!');

// => Привет devsheet
console.warn('привет %s', 'devsheet');

// Выводит сообщение об ошибке в stderr
console.error(new Error('Упс!'));
```

### Числа

```javascript
let amount = 6;
let price = 4.99;
```

### Переменные

```javascript
let x = null;
let name = 'Тамми';
const found = false;

// => Тамми, false, null
console.log(name, found, x);

var a;
console.log(a); // => неопределено
```

### Строки

```javascript
let single = 'Где моя бандитская шляпа?';
let double = 'Где моя бандитская шляпа?';

// => 21
console.log(single.length);
```

### Арифметические операторы

```javascript
5 + 5 = 10     // Сложение
10 - 5 = 5     // Вычитание
5 * 10 = 50    // Умножение
10 / 5 = 2     // Деление
10 % 5 = 0     // Остаток от деления
```

### Комментарии

```javascript
// Эта строка обозначает комментарий

/*
Следующую конфигурацию нужно
изменить перед деплоем.
*/
```

### Операторы присваивания

```javascript
let number = 100;

// Оба выражения добавят 10
number = number + 10;
number += 10;

console.log(number);
// => 120
```

### Интерполяция строк

```javascript
let age = 7;

// Конкатенация строк
'Томми ' + age + ' лет.';

// Интерполяция строк
`Томми ${age} лет.`;
```

### Ключевое слово let

```javascript
let count;
console.log(count); // => неопределено
count = 10;
console.log(count); // => 10
```

### Ключевое слово const

```javascript
const numberOfColumns = 4;

// TypeError: Присваивание константе...
numberOfColumns = 8;
```

## Условные операторы JavaScript

### Оператор if

```javascript
const isMailSent = true;

if (isMailSent) {
  console.log('Письмо отправлено получателю');
}
```

### Тернарный оператор

```javascript
var x = 1;

// => true
result = x == 1 ? true : false;
```

### Операторы {.row-span-2}

```javascript
true || false; // true
10 > 5 || 10 > 20; // true
false || false; // false
10 > 100 || 10 > 20; // false
```

#### Логический оператор &&

```javascript
true && true; // true
1 > 2 && 2 > 1; // false
true && false; // false
4 === 4 && 3 > 1; // true
```

#### Операторы сравнения

```javascript
1 > 3; // false
3 > 1; // true
250 >= 250; // true
1 === 1; // true
1 === 2; // false
1 === '1'; // false
```

#### Логический оператор !

```javascript
let lateToWork = true;
let oppositeValue = !lateToWork;

// => false
console.log(oppositeValue);
```

#### Оператор объединения с null ??

```javascript
null ?? 'Я победил'; //  'Я победил'
undefined ?? 'Я тоже'; //  'Я тоже'

false ?? 'Я проиграл'; //  false
```

### else if

```javascript
const size = 10;

if (size > 100) {
  console.log('Большой');
} else if (size > 20) {
  console.log('Средний');
} else if (size > 4) {
  console.log('Маленький');
} else {
  console.log('Крошечный');
}
// Выведет: Маленький
```

### Оператор switch

```javascript
const food = 'салат';

switch (food) {
  case 'oyster':
    console.log('Вкус моря');
    break;
  case 'pizza':
    console.log('Вкусная пицца');
    break;
  default:
    console.log('Приятного аппетита');
}
```

### == против ===

```javascript
0 == false; // true
0 === false; // false, different type
1 == '1'; // true,  automatic type conversion
1 === '1'; // false, different type
null == undefined; // true
null === undefined; // false
'0' == false; // true
'0' === false; // false
```

Оператор `==` сравнивает только значения, а `===` сравнивает и значения, и типы.

## Функции JavaScript

### Функции

```javascript
// Определение функции:
function sum(num1, num2) {
  return num1 + num2;
}

// Вызов функции:
sum(3, 6); // 9
```

### Анонимные функции

```javascript
// Именованная функция
function rocketToMars() {
  return 'БУМ!';
}

// Анонимная функция
const rocketToMars = function () {
  return 'БУМ!';
};
```

### Стрелочные функции (ES6) {.row-span-2}

#### С двумя аргументами

```javascript
const sum = (param1, param2) => {
  return param1 + param2;
};
console.log(sum(2, 5)); // => 7
```

#### Без аргументов

```javascript
const printHello = () => {
  console.log('привет');
};
printHello(); // => привет
```

#### С одним аргументом

```javascript
const checkWeight = (weight) => {
  console.log(`Вес: ${weight}`);
};
checkWeight(25); // => Вес: 25
```

#### Краткая запись стрелочных функций

```javascript
const multiply = (a, b) => a * b;
// => 60
console.log(multiply(2, 30));
```

[Arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) available
starting ES2015

### Ключевое слово return

```javascript
// С return
function sum(num1, num2) {
  return num1 + num2;
}

// Функция не возвращает сумму
function sum(num1, num2) {
  num1 + num2;
}
```

### Вызов функций

```javascript
// Определение функции
function sum(num1, num2) {
  return num1 + num2;
}

// Вызов функции
sum(2, 4); // 6
```

### Функциональные выражения

```javascript
const dog = function () {
  return 'Гав!';
};
```

### Параметры функции

```javascript
// Параметр — name
function sayHello(name) {
  return `Привет, ${name}!`;
}
```

### Объявление функции

```javascript
function add(num1, num2) {
  return num1 + num2;
}
```

## Область видимости JavaScript

### Область видимости

```javascript
function myFunction() {
  var pizzaName = 'Маргарита';
  // Здесь можно использовать pizzaName
}

// Здесь нельзя использовать pizzaName
```

### Переменные с блочной областью видимости

```javascript
const isLoggedIn = true;

if (isLoggedIn == true) {
  const statusMessage = 'Вход выполнен.';
}

// Uncaught ReferenceError...
console.log(statusMessage);
```

### Глобальные переменные

```javascript
// Переменная объявлена глобально
const color = 'blue';

function printColor() {
  console.log(color);
}

printColor(); // => синий
```

### let против var

```javascript
for (let i = 0; i < 3; i++) {
  // Это максимальная область видимости для 'let'
  // i доступна ✔️
}
// i недоступна ❌
```

---

```javascript
for (var i = 0; i < 3; i++) {
  // i доступна ✔️
}
// i доступна ✔️
```

`var` ограничен ближайшей функцией, а `let` — ближайшим блоком кода.

### Циклы с замыканиями

```javascript{.wrap}
// Три раза выведет 3, не то, что мы хотели.
for (var i = 0; i < 3; i++) {
  setTimeout(_ => console.log(i), 10);
}
```

---

```javascript{.wrap}
// Выведет 0, 1 и 2, как ожидалось.
for (let j = 0; j < 3; j++) {
  setTimeout(_ => console.log(j), 10);
}
```

При использовании `let` каждая итерация получает свою копию переменной, а при использовании `var` переменная общая для всех итераций.

## Массивы JavaScript

### Массивы

```javascript
const fruits = ['яблоко', 'апельсин', 'банан'];

// Разные типы данных
const data = [1, 'курица', false];
```

### Свойство .length

```javascript
const numbers = [1, 2, 3, 4];

numbers.length; // 4
```

### Индекс

```javascript
// Доступ к элементу массива
const myArray = [100, 200, 300];

console.log(myArray[0]); // 100
console.log(myArray[1]); // 200
```

### Таблица мутаций

|           | add | remove | start | end |
| :-------- | :-: | :----: | :---: | :-: |
| `push`    | ✔  |        |       | ✔  |
| `pop`     |     |   ✔   |       | ✔  |
| `unshift` | ✔  |        |  ✔   |     |
| `shift`   |     |   ✔   |  ✔   |     |

{.show-header}

### Array.push()

```javascript
// Добавление одного элемента:
const cart = ['яблоко', 'апельсин'];
cart.push('груша');

// Добавление нескольких элементов:
const numbers = [1, 2];
numbers.push(3, 4, 5);
```

Добавляет элементы в конец массива и возвращает новую длину массива.

### Array.pop()

```javascript
const fruits = ['яблоко', 'апельсин', 'банан'];

const fruit = fruits.pop(); // 'банан'
console.log(fruits); // ["яблоко", "апельсин"]
```

Удаляет элемент с конца массива и возвращает этот элемент.

### Array.shift()

```javascript
let cats = ['Боб', 'Вилли', 'Мини'];

cats.shift(); // ['Вилли', 'Мини']
```

Удаляет элемент с начала массива и возвращает этот элемент.

### Array.unshift()

```javascript
let cats = ['Боб'];

// => ['Вилли', 'Боб']
cats.unshift('Вилли');

// => ['Паф', 'Джордж', 'Вилли', 'Боб']
cats.unshift('Паф', 'Джордж');
```

Добавляет элементы в начало массива и возвращает новую длину массива.

### Array.concat()

```javascript
const numbers = [3, 2, 1];
const newFirstNumber = 4;

// => [ 4, 3, 2, 1 ]
[newFirstNumber].concat(numbers);

// => [ 3, 2, 1, 4 ]
numbers.concat(newFirstNumber);
```

Если вы хотите избежать изменения исходного массива, используйте concat.

## Множество JavaScript (Set)

### Создание Set

```javascript
// Пустой объект Set
const emptySet = new Set();

// Объект Set со значениями
const setObj = new Set([1, true, 'привет']);
```

### Добавление

```javascript
const emptySet = new Set();

// добавление значений
emptySet.add('a'); // 'a'
emptySet.add(1); // 'a', 1
emptySet.add(true); // 'a', 1, true
emptySet.add('a'); // 'a', 1, true
```

### Удаление

```javascript
const emptySet = new Set([1, true, 'a']);

// удаление значений
emptySet.delete('a'); // 1, true
emptySet.delete(true); // 1
emptySet.delete(1); //
```

### Проверка наличия

```javascript
const setObj = new Set([1, true, 'a']);

// возвращает true или false
setObj.has('a'); // true
setObj.has(1); // true
setObj.has(false); // false
```

### Очистка

```javascript
const setObj = new Set([1, true, 'a']);

// очищает set
console.log(setObj); // 1, true, 'a'
setObj.clear(); //
```

### Размер

```javascript
const setObj = new Set([1, true, 'a']);

consoloe.log(setObj.size); // 3
```

### ForEach

```javascript
const setObj = new Set([1, true, 'a']);

setObj.forEach(function (value) {
  console.log(value);
});

// 1
// true
// 'a'
```

## Циклы JavaScript

### Цикл while

```javascript
while (condition) {
  // code block to be executed
}

let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

### Обратный цикл

```javascript
const fruits = ['яблоко', 'апельсин', 'банан'];

for (let i = fruits.length - 1; i >= 0; i--) {
  console.log(`${i}. ${fruits[i]}`);
}

// => 2. банан
// => 1. апельсин
// => 0. яблоко
```

### Цикл do…while

```javascript
x = 0;
i = 0;

do {
  x = x + i;
  console.log(x);
  i++;
} while (i < 5);
// => 0 1 3 6 10
```

### Цикл for

```javascript
for (let i = 0; i < 4; i += 1) {
  console.log(i);
}

// => 0, 1, 2, 3
```

### Перебор массива

```javascript
for (let i = 0; i < array.length; i++) {
  console.log(array[i]);
}

// => Каждый элемент массива
```

### Break

```javascript
for (let i = 0; i < 99; i += 1) {
  if (i > 5) {
    break;
  }
  console.log(i);
}
// => 0 1 2 3 4 5
```

### Continue

```javascript
for (i = 0; i < 10; i++) {
  if (i === 3) {
    continue;
  }
  text += 'Число: ' + i + '<br>';
}
```

### Вложенные циклы

```javascript
for (let i = 0; i < 2; i += 1) {
  for (let j = 0; j < 3; j += 1) {
    console.log(`${i}-${j}`);
  }
}
```

### Цикл for...in

```javascript
const fruits = ['яблоко', 'апельсин', 'банан'];

for (let index in fruits) {
  console.log(index);
}
// => 0
// => 1
// => 2
```

### Цикл for...of

```javascript
const fruits = ['яблоко', 'апельсин', 'банан'];

for (let fruit of fruits) {
  console.log(fruit);
}
// => яблоко
// => апельсин
// => банан
```

## Итераторы JavaScript {.cols-2}

### Функции, присвоенные переменным

```javascript
let plusFive = (number) => {
  return number + 5;
};
// f присваивается значение plusFive
let f = plusFive;

plusFive(3); // 8
// Так как f — функция, её можно вызвать.
f(9); // 14
```

### Функции обратного вызова (Callback)

```javascript
const isEven = (n) => {
  return n % 2 == 0;
};

let printMsg = (evenFunc, num) => {
  const isNumEven = evenFunc(num);
  console.log(`${num} — чётное число: ${isNumEven}.`);
};

// Передаём isEven как callback-функцию
printMsg(isEven, 4);
// => 4 — чётное число: True.
```

### Array.reduce()

```javascript
const numbers = [1, 2, 3, 4];

const sum = numbers.reduce((accumulator, curVal) => {
  return accumulator + curVal;
});

console.log(sum); // 10
```

### Array.map()

```javascript
const members = ['Тейлор', 'Дональд', 'Дон', 'Наташа', 'Бобби'];

const announcements = members.map((member) => {
  return member + ' присоединился к конкурсу.';
});

console.log(announcements);
```

### Array.forEach()

```javascript
const numbers = [28, 77, 45, 99, 27];

numbers.forEach((number) => {
  console.log(number);
});
```

### Array.filter()

```javascript
const randomNumbers = [4, 11, 42, 14, 39];
const filteredArray = randomNumbers.filter((n) => {
  return n > 5;
});
```

## Объекты JavaScript {.cols-2}

### Доступ к свойствам

```javascript
const apple = {
  color: 'Зелёный',
  price: { bulk: '3$/кг', smallQty: '4$/кг' }
};
console.log(apple.color); // => Зелёный
console.log(apple.price.bulk); // => 3$/кг
```

### Именование свойств

```javascript
// Example of invalid key names
const trainSchedule = {
  // Invalid because of the space between words.
  platform num: 10,
  // Expressions cannot be keys.
  40 - 10 + 2: 30,
  // A + sign is invalid unless it is enclosed in quotations.
  +compartment: 'C'
}
```

### Несуществующие свойства

```javascript
const classElection = {
  date: '12 января'
};

console.log(classElection.place); // undefined
```

### Мутация {.row-span-2}

```javascript
const student = {
  name: 'Шелдон',
  score: 100,
  grade: 'A'
};

console.log(student);
// { name: 'Шелдон', score: 100, grade: 'A' }

delete student.score;
student.grade = 'F';
console.log(student);
// { name: 'Шелдон', grade: 'F' }

student = {};
// TypeError: Присваивание константе.
```

### Сокращённая запись присваивания

```javascript
const person = {
  name: 'Том',
  age: '22'
};
const { name, age } = person;
console.log(name); // 'Том'
console.log(age); // '22'
```

### Оператор delete

```javascript
const person = {
  firstName: 'Матильда',
  age: 27,
  hobby: 'вязание',
  goal: 'изучить JavaScript'
};

delete person.hobby; // или delete person[hobby];

console.log(person);
/*
{
  firstName: "Матильда"
  age: 27
  goal: "изучить JavaScript"
}
*/
```

### Объекты как аргументы

```javascript
const origNum = 8;
const origObj = { color: 'синий' };

const changeItUp = (num, obj) => {
  num = 7;
  obj.color = 'красный';
};

changeItUp(origNum, origObj);

// Выведет 8, так как числа передаются по значению.
console.log(origNum);

// Выведет 'красный', так как объекты передаются
// по ссылке и являются изменяемыми.
console.log(origObj.color);
```

### Сокращённое создание объекта

```javascript
const activity = 'Сёрфинг';
const beach = { activity };
console.log(beach); // { activity: 'Сёрфинг' }
```

### Ключевое слово this

```javascript
const cat = {
  name: 'Пайпи',
  age: 8,
  whatName() {
    return this.name;
  }
};
console.log(cat.whatName()); // => Пайпи
```

### Фабричные функции

```javascript
// Фабричная функция, принимающая параметры 'name',
// 'age' и 'breed' и возвращающая объект собаки.
const dogFactory = (name, age, breed) => {
  return {
    name: name,
    age: age,
    breed: breed,
    bark() {
      console.log('Гав!');
    }
  };
};
```

### Методы объекта

```javascript
const engine = {
  // сокращённая запись метода, с одним аргументом
  start(adverb) {
    console.log(`Двигатель запускается ${adverb}...`);
  },
  // анонимная стрелочная функция без аргументов
  sputter: () => {
    console.log('Двигатель тарахтит...');
  }
};

engine.start('громко');
engine.sputter();
```

### Геттеры и сеттеры

```javascript
const myCat = {
  _name: 'Дотти',
  get name() {
    return this._name;
  },
  set name(newName) {
    this._name = newName;
  }
};

// Обращение вызывает геттер
console.log(myCat.name);

// Присваивание вызывает сеттер
myCat.name = 'Янки';
```

## Классы JavaScript

### Статические методы

```javascript
class Dog {
  constructor(name) {
    this._name = name;
  }

  introduce() {
    console.log('Это ' + this._name + ' !');
  }

  // Статический метод
  static bark() {
    console.log('Гав!');
  }
}

const myDog = new Dog('Бастер');
myDog.introduce();

// Вызов статического метода
Dog.bark();
```

### Класс

```javascript
class Song {
  constructor() {
    this.title;
    this.author;
  }

  play() {
    console.log('Воспроизведение песни!');
  }
}

const mySong = new Song();
mySong.play();
```

### Конструктор класса

```javascript
class Song {
  constructor(title, artist) {
    this.title = title;
    this.artist = artist;
  }
}

const mySong = new Song('Богемская рапсодия', 'Queen');
console.log(mySong.title);
```

### Методы класса

```javascript
class Song {
  play() {
    console.log('Воспроизведение!');
  }

  stop() {
    console.log('Остановлено!');
  }
}
```

### extends

```javascript
// Родительский класс
class Media {
  constructor(info) {
    this.publishDate = info.publishDate;
    this.name = info.name;
  }
}

// Дочерний класс
class Song extends Media {
  constructor(songData) {
    super(songData);
    this.artist = songData.artist;
  }
}

const mySong = new Song({
  artist: 'Queen',
  name: 'Богемская рапсодия',
  publishDate: 1975
});
```

## Модули JavaScript {.cols-2}

### Экспорт

```javascript
// myMath.js

// Default export
export default function add(x, y) {
  return x + y;
}

// Normal export
export function subtract(x, y) {
  return x - y;
}

// Multiple exports
function multiply(x, y) {
  return x * y;
}
function duplicate(x) {
  return x * 2;
}
export { multiply, duplicate };
```

### Импорт

```javascript
// main.js
import add, { subtract, multiply, duplicate } from './myMath.js';

console.log(add(6, 2)); // 8
console.log(subtract(6, 2)) // 4
console.log(multiply(6, 2)); // 12
console.log(duplicate(5)) // 10

// index.html
<script type="module" src="main.js"></script>
```

### Экспорт модуля

```javascript
// myMath.js

function add(x, y) {
  return x + y;
}
function subtract(x, y) {
  return x - y;
}
function multiply(x, y) {
  return x * y;
}
function duplicate(x) {
  return x * 2;
}

// Multiple exports in node.js
module.exports = {
  add,
  subtract,
  multiply,
  duplicate
};
```

### Импорт модуля (require)

```javascript
// main.js
const myMath = require('./myMath.js');

console.log(myMath.add(6, 2)); // 8
console.log(myMath.subtract(6, 2)); // 4
console.log(myMath.multiply(6, 2)); // 12
console.log(myMath.duplicate(5)); // 10
```

## Промисы JavaScript {.cols-2}

### Состояния Promise {.row-span-2}

```javascript
const promise = new Promise((resolve, reject) => {
  const res = true;
  // Асинхронная операция.
  if (res) {
    resolve('Выполнено!');
  } else {
    reject(Error('Ошибка'));
  }
});

promise.then(
  (res) => console.log(res),
  (err) => console.error(err)
);
```

### Функция-исполнитель

```javascript
const executorFn = (resolve, reject) => {
  resolve('Выполнено!');
};

const promise = new Promise(executorFn);
```

### setTimeout()

```javascript
const loginAlert = () => {
  console.log('Вход');
};

setTimeout(loginAlert, 6000);
```

### Метод .then()

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Результат');
  }, 200);
});

promise.then(
  (res) => {
    console.log(res);
  },
  (err) => {
    console.error(err);
  }
);
```

### Метод .catch()

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject(Error('Промис отклонён безусловно.'));
  }, 1000);
});

promise.then((res) => {
  console.log(value);
});

promise.catch((err) => {
  console.error(err);
});
```

### Promise.all()

```javascript
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve(3);
  }, 300);
});
const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve(2);
  }, 200);
});

Promise.all([promise1, promise2]).then((res) => {
  console.log(res[0]);
  console.log(res[1]);
});
```

### Promise.allSettled()

```javascript
const promise1 = Promise.resolve(3);
const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject(2);
  }, 100);
});

Promise.allSettled([promise1, promise2]).then((res) => {
  console.log(res[0].status);
  console.log(res[1].status);
});
```

### Избегание вложенных Promise и .then()

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('*');
  }, 1000);
});

const twoStars = (star) => {
  return star + star;
};

const oneDot = (star) => {
  return star + '.';
};

const print = (val) => {
  console.log(val);
};

// Chaining them all together
promise.then(twoStars).then(oneDot).then(print);
```

### Создание

```javascript
const executorFn = (resolve, reject) => {
  console.log('The executor function of the promise!');
};

const promise = new Promise(executorFn);
```

### Цепочка нескольких .then()

```javascript
const promise = new Promise((resolve) =>
  setTimeout(() => resolve('dAlan'), 100)
);

promise
  .then((res) => {
    return res === 'Alan'
      ? Promise.resolve('Hey Alan!')
      : Promise.reject('Who are you?');
  })
  .then(
    (res) => {
      console.log(res);
    },
    (err) => {
      console.error(err);
    }
  );
```

### Фейковый HTTP-запрос с Promise

```javascript
const mock = (success, timeout = 1000) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (success) {
        resolve({ status: 200, data: {} });
      } else {
        reject({ message: 'Error' });
      }
    }, timeout);
  });
};
const someEvent = async () => {
  try {
    await mock(true, 1000);
  } catch (e) {
    console.log(e.message);
  }
};
```

## Async-Await JavaScript {.cols-2}

### Асинхронность

```javascript
function helloWorld() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve('Hello World!');
    }, 2000);
  });
}

const msg = async function () {
  // Асинхронное функциональное выражение
  const msg = await helloWorld();
  console.log('Сообщение:', msg);
};

const msg1 = async () => {
  // Асинхронная стрелочная функция
  const msg = await helloWorld();
  console.log('Сообщение:', msg);
};

msg(); // Сообщение: Hello World! <-- через 2 секунды
msg1(); // Сообщение: Hello World! <-- через 2 секунды
```

### Разрешение промисов

```javascript
let pro1 = Promise.resolve(5);
let pro2 = 44;
let pro3 = new Promise(function (resolve, reject) {
  setTimeout(resolve, 100, 'foo');
});

Promise.all([pro1, pro2, pro3]).then(function (values) {
  console.log(values);
});
// ожидается => Массив [5, 44, "foo"]
```

### Async Await Promises

```javascript
function helloWorld() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve('Hello World!');
    }, 2000);
  });
}

async function msg() {
  const msg = await helloWorld();
  console.log('Сообщение:', msg);
}

msg(); // Сообщение: Hello World! <-- через 2 секунды
```

### Обработка ошибок

```javascript
let json = '{ "age": 30 }'; // неполные данные

try {
  let user = JSON.parse(json); // <-- без ошибок
  console.log(user.name); // нет имени!
} catch (e) {
  console.error('Некорректные JSON-данные!');
}
```

### Оператор async await

```javascript
function helloWorld() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve('Hello World!');
    }, 2000);
  });
}

async function msg() {
  const msg = await helloWorld();
  console.log('Сообщение:', msg);
}

msg(); // Сообщение: Hello World! <-- через 2 секунды
```

## Запросы JavaScript

### JSON

```json
const jsonObj = {
  "name": "Rick",
  "id": "11A",
  "level": 4
};
```

Also see: [JSON cheatsheet](/json)

### XMLHttpRequest

```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'mysite.com/getjson');
```

`XMLHttpRequest` is a browser-level API that enables the client to script data transfers via JavaScript, NOT part of the
JavaScript language.

### GET

```javascript
const req = new XMLHttpRequest();
req.responseType = 'json';
req.open('GET', '/getdata?id=65');
req.onload = () => {
  console.log(xhr.response);
};

req.send();
```

### POST {.row-span-2}

```javascript
const data = {
  fish: 'Salmon',
  weight: '1.5 KG',
  units: 5
};
const xhr = new XMLHttpRequest();
xhr.open('POST', '/inventory/add');
xhr.responseType = 'json';
xhr.send(JSON.stringify(data));

xhr.onload = () => {
  console.log(xhr.response);
};
```

### fetch api {.row-span-2}

```javascript
fetch(url, {
    method: 'POST',
    headers: {
      'Content-type': 'application/json',
      'apikey': apiKey
    },
    body: data
  }).then(response => {
    if (response.ok) {
      return response.json();
    }
    throw new Error('Request failed!');
  }, networkError => {
    console.log(networkError.message)
  })
}
```

### Форматированный JSON

```javascript
fetch('url-that-returns-JSON')
  .then((response) => response.json())
  .then((jsonResponse) => {
    console.log(jsonResponse);
  });
```

### promise url parameter fetch api

```javascript
fetch('url').then(
  (response) => {
    console.log(response);
  },
  (rejection) => {
    console.error(rejection.message);
  }
);
```

### Функция Fetch API

```javascript
fetch('https://api-xxx.com/endpoint', {
  method: 'POST',
  body: JSON.stringify({ id: '200' })
})
  .then(
    (response) => {
      if (response.ok) {
        return response.json();
      }
      throw new Error('Request failed!');
    },
    (networkError) => {
      console.log(networkError.message);
    }
  )
  .then((jsonResponse) => {
    console.log(jsonResponse);
  });
```

### Синтаксис async await {.col-span-2}

```javascript
const getSuggestions = async () => {
  const wordQuery = inputField.value;
  const endpoint = `${url}${queryParams}${wordQuery}`;
  try {
    const response = await fetch(endpoint, { cache: 'no-cache' });
    if (response.ok) {
      const jsonResponse = await response.json();
    }
  } catch (error) {
    console.log(error);
  }
};
```
