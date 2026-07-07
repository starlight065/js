---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: true
  metadata:
    visible: false
  tags:
    visible: true
  actions:
    visible: true
---

# В чем разница между архитектурой CommonJS и ES-модулями?

#### 1. Синтаксис

Это самое заметное различие для разработчика.

*   **CommonJS:** использует функцию `require()` для импорта и объект `module.exports` для экспорта.

    ```javascript
    const add = (a, b) => a + b;
    module.exports = { add };

    const { add } = require('./math.js');
    ```
*   **ES-модули:** используют ключевые слова `import` и `export`.

    ```javascript
    export const add = (a, b) => a + b;

    import { add } from './math.js';
    ```

#### 2. Синхронность vs Асинхронность

* CommonJS (Синхронный): `require()` блокирует выполнение потока, пока модуль не загрузится. Это отлично работает на сервере (в Node.js), где файлы лежат на жестком диске и загружаются мгновенно. Но это плохо для браузеров, где загрузка файла по сети вызвала бы "зависание" интерфейса.
* ES-модули (Асинхронные): Они спроектированы так, чтобы сначала разобрать структуру файлов, загрузить их асинхронно по сети и только потом выполнить.

#### 3. Доступ к глобальным переменным окружения

* В CommonJS у вас есть автоматический доступ к переменным `__dirname` (путь к текущей папке) и `__filename` (путь к файлу).
* В ES-модулях этих переменных нет. Вместо них используется объект `import.meta.url`.
