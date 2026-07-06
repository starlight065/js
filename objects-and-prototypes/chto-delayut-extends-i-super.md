# Что делают extends и super?

`extends` используют, чтобы один класс наследовался от другого.

`super` используют, чтобы обратиться к родительскому классу.

```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log('Sound');
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name);
  }

  speak() {
    super.speak();
    console.log('Woof');
  }
}
```

Важно:

* в дочернем классе `super()` надо вызвать до `this`;
* `super.method()` вызывает метод родителя.

Короткий ответ для собеседования:

> `extends` создаёт наследование между классами. `super` даёт доступ к конструктору и методам родительского класса. В наследуемом классе `super()` нужно вызвать до использования `this`.
