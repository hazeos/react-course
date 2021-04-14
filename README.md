# Описание
Справочная информация по курсу JS фреймворка [React](https://www.udemy.com/course/react-the-complete-guide-incl-redux/)

# Оглавление
1. [Arrow Functions](#arrow-functions)
1. [Exports & Imports](#exports-&-imports)

# Arrow Functions
Варианты использования:

```javascript
// при отсутствии параметров
const print = () => {
    console.log('');
}
```

```javascript
// при использовании нескольких параметров
const print = (value, counter) => {
    console.log(counter + value);
}
```

```javascript
// при использовании только одного параметра
const print = counter => {
    console.log(value);
}
```

```javascript
// возврат значения
const multiply = number => number * 2;
```

# Exports & Imports
Разные типы экспорта и иморта модулей, функций и так далее.
persons.js
```javascript
const person = {
    name: 'Max'
}
export default person
```

utility.js
```javascript
export const clean = (smth) = {...};
export const baseData = 10;
```

app.js
```javascript
//обычный экспорт
import person from './person.js'
import prs from './person.js'

//именованный импорт
import {baseData} from './utility.js'
import {clean} from './utility.js'

//именованный импорт с переименовыванием
import {baseData as Base} from './utility.js'

// импорт всего содержимого как объекта
// переменные и функции будут доступны через точку (bundle.baseData)
import * as bundle from './utility.js'
```

# Classes
Класс - шаблон для объекта.

```javascript
class Person {
    name = 'Max' //свойство
    call = () => {/*some actions*/} //метод
}
```

Использование класса
```javascript
const myPerson = new Person();
myPerson.call();
console.log(myPerson.name);
```

Наследование
```javascript
class Person extends Master {
    
}
```

Пример класса и его использования

```javascript
class Human {
    constructor() {
        this.gender = 'male';
    }
    
    printGender () {
        console.log(this.gender);
    }
}

class Person extends Human {
    // метод запускающийся при создании экземпляра класса
    constructor() {
        super();// вызывает конструктор родительского класса
        this.name = 'Max';
        this.gender = null;
    }
    
    printName() {
        console.log(this.name);
    }
}

const person = new Person();
person.printName();
person.printGender();
```

## Пример класса на новом поколении ES6 / ES7

```javascript
class Human {
    gender = 'male';
    
    printGender = () => {
        console.log(this.gender);
    }
}

class Person extends Human {
    name = 'Max';
    gender = null;
    
    printName = () => {
        console.log(this.gender);
    }
}

const person = new Person();
person.printName();
person.printGender();
```

# Spread & Rest Operators

## Spread
`...` - берет **все** элементы старого массива и пишет в новый
```javascript
const newArray = [...oldArray, 1, 2];
const newObject = {...oldArray, newProp: 5};
```

## Rest
`...` - пишет **все** аргументы функции в массив, в последствии на массив можно
применять функции для работы с массивами
```javascript
sortArgs = (...args) => {
    return args.filter(el => el === 1);
}

console.log(sortArgs(1,2,3));
```

## Destructing
Позволяет извлекать **определенные (одиночные)** элементы массивов или свойства объектов для хранения в переменных.

### Array Destructing

```javascript
[a, b] = ['Hello', 'World'];
console.log(a);// Hello
console.log(b);// World

const number = [1, 2, 3];
[num1, ,num3] = numbers;
console.log(num1, num3); // 1 3
```

### Object Destructing

```javascript
({name} = {name: 'Max', age: 28});
console.log(name);// Max
console.log(age);// Undefined
```

# Reference and Primitive Types Refresher
Примитивные типы данных:
- `string` Строки
- `number` Числа
- `boolean` Булево

При переназначении переменных, значение копируется.
```javascript
const number = 1;
const secondNumber = number;

console.log(secondNumber); // Prints 1
```

Ссылочные типы данных:
 - `object` объекты
 - `array` массивы

Объект хранится в памяти, но переменная `person` хранит в себе только указатель (ссылку) 
на это место в памяти.
```javascript
const person = {
    name: 'Max'
}
const secondPerson = person;

console.log(secondPerson.name); // prints 'Max' 
```
По умолчанию, при переназначении переменной копируется указатель, а не значение.
```javascript
const person = {
    name: 'Max'
}
const secondPerson = person;

person.name = 'Manu'

console.log(secondPerson.name); // prints 'Manu' 
```
Выводит имя 'Manu', потому что переменная указывает 
на то же место в памяти, так как объект один.

Такая же история по умолчанию с массивами.

Для копирования объекта (создания нового) нужно использовать следующий синтаксис:
```javascript
const person = {
    name: 'Max'
}
const secondPerson = {
    ...person
};

person.name = 'Manu'

console.log(secondPerson.name); // prints 'Max' 
```
# Refreshing Array Functions
`.map()` - принимает на вход функцию и применяет ее к каждому элементу массива.
Возвращает **новый** массив.
```javascript
const numbers = [1, 2, 3];
const doubleNumArray = numbers.map((num) => {
    return num * 2;
});

console.log(numbers); // [1, 2, 3];
console.log(doubleNumArray); // [2, 4, 6];
```
Другие полезные функции применимые к массивам:

1. [`.find()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
1. [`.findIndex()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)
1. [`.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
1. [`.reduce()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
1. [`.concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)
1. [`.slice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
1. [`.splice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

# Build Workflow
Лучшие практики для одно страничных и многостраничных веб приложений: 
- Оптимизированный код
- Использование последних возможностей JS
- Использование пакетных менеджеров (менеджеров зависимостей) npm или yarn
- Использовать сборщик Webpack
- Использовать компилятор (Next Gen JS в обычный JS) Babel + Presets

# React Commands
`npm create-react-app <NAME> --scripts-version <VERSION>` - создает проект (папку) 
с именем указанным в команде. `--scripts-version <VERSION>` - опционально,
чем больше версия, тем больше новых возможностей есть в React. Если не указывать,
то будет задействована последняя версия скриптов.

`npm start` - запускает локальный сервер на localhost:3000

# React Common Features

## JSX
```javascript
    return (
      <div className="App">
          <h1>This is React Application.</h1>
      </div>
    );
```
Пример указанный выше — то же самое что и пример указанный ниже.
Так работает `jsx`.
```javascript
    return React.createElement('div', {className: 'App'}, 
    React.createElement('h1', null, 'This is React Application.'
    ));
```

## Props (properties)
Для использования свойств необходимо указать их в атрибутах компонента.

App.js
```javascript
<Person name="Ilya" age="23">My hobby: Nothing</Person>
```

Person.js
```javascript
const person = (props) => {
    return (
        <div>
            <p>I'm a {props.name} and I am {props.age} years old.</p>
            <p>{props.children}</p>
        </div>
    );
}
/**
 * Выведет:
 * I'm a Ilya and I am 23 years old.
 * My hobby: Nothing
 */
```
Свойства указанные в атрибутах, доступны через параметр `props.*`.
Также есть свойства по умолчанию, например `props.children`, в котором будет
содержимое компонента переданное между `<Person>` и `</Person>`

## TODO Описать State по лекции 395-396. Props & State
