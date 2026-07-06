# Shallow copy vs deep copy в JavaScript

**Поверхностная копия** копирует только верхний уровень объекта. Вложенные объекты остаются по той же ссылке.

```js
const original = { user: { name: 'Ann' } };
const copy = { ...original };

copy.user.name = 'Bob';
console.log(original.user.name); // Bob
```

**Глубокая копия** создаёт новые копии для всех вложенных структур.

```js
const original = { user: { name: 'Ann' } };
const copy = structuredClone(original);

copy.user.name = 'Bob';
console.log(original.user.name); // Ann
```

Частые способы:

* shallow copy — `...spread`, `Object.assign()`;
* deep copy — `structuredClone()`;
* `JSON.parse(JSON.stringify(obj))` подходит только для простых данных.

Короткий ответ для собеседования:

> Shallow copy копирует только первый уровень. Вложенные объекты остаются общими. Deep copy создаёт полностью независимую копию всей структуры. Для shallow copy обычно используют spread или `Object.assign`, для deep copy — `structuredClone`.
