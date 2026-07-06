# Какие есть способы создать объект в JavaScript?

Основные способы:

* литерал объекта — самый частый вариант;
* `new Object()` — старый и менее удобный способ;
* функция-конструктор;
* `class`;
* `Object.create()`.

```js
const a = { name: 'Ann' };
const b = new Object();
const c = Object.create(null);

function User(name) {
  this.name = name;
}
const d = new User('Ann');

class Admin {
  constructor(name) {
    this.name = name;
  }
}
const e = new Admin('Bob');
```

На практике чаще всего используют литералы, `class` и иногда `Object.create()`.

Короткий ответ для собеседования:

> Объект можно создать через литерал `{}`, через `new Object()`, через функцию-конструктор, через `class` и через `Object.create()`. Чаще всего используют литерал как самый простой и читаемый способ.
