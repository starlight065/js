# Какие типы данных есть в JavaScript? Как проверить тип переменной?

В JavaScript есть 8 типов данных.

Примитивы:

* `string`
* `number`
* `bigint`
* `boolean`
* `undefined`
* `symbol`
* `null`

И отдельно ссылочный тип:

* `object`

Чаще всего тип проверяют через `typeof`:

```js
typeof "hello"; // "string"
typeof 42; // "number"
typeof true; // "boolean"
typeof undefined; // "undefined"
typeof {}; // "object"
typeof []; // "object"
```

Важно помнить, что `typeof null` возвращает `"object"`. Это историческая особенность JavaScript.

Для массивов лучше использовать `Array.isArray()`:

```js
Array.isArray([]); // true
Array.isArray({}); // false
```

Для точной проверки `null` обычно пишут просто:

```js
value === null
```
