# Как связать объекты через прототип?

Связь наследования между объектами обычно создают через `Object.create()`.

```js
const animal = {
  eats: true
};

const dog = Object.create(animal);
console.log(dog.eats); // true
```

Также есть:

* `Object.setPrototypeOf(obj, proto)` — меняет прототип объекта;
* `Object.getPrototypeOf(obj)` — возвращает прототип объекта.

```js
Object.getPrototypeOf(dog) === animal; // true
```

`Object.setPrototypeOf()` существует, но его стараются использовать реже. Он может ухудшать производительность.

Короткий ответ для собеседования:

> Наследование между объектами обычно создают через `Object.create(proto)`. Для чтения прототипа используют `Object.getPrototypeOf`, а для изменения — `Object.setPrototypeOf`, хотя менять прототип на лету нежелательно.
