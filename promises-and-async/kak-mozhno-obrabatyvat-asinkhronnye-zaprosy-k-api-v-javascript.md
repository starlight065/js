# Как можно обрабатывать асинхронные запросы к API в JavaScript?

**1. Callbacks (устаревший подход)**

```javascript
function getData(callback) {
  fetch('/api/data').then(res => callback(res));
}
```

Минус: callback hell при вложенных запросах.

**2. Promises**

```javascript
fetch('/api/data')
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

Методы: `.then()`, `.catch()`, `.finally()`.

**3. Async/await (современный стандарт)**

```javascript
async function getData() {
  try {
    const res = await fetch('/api/data');
    const data = await res.json();
    return data;
  } catch (err) {
    console.error(err);
  }
}
```

Синтаксический сахар над промисами, читается как синхронный код.

### Полезные методы Promise для интервью

* `Promise.all(promises)` — принимает массив промисов. Если все выполнились успешно — возвращает массив результатов в том же порядке. Если хотя бы один промис отклонён (reject) — сразу падает с этой ошибкой, не дожидаясь остальных.
* `Promise.allSettled(promises)` — принимает массив промисов. Всегда дожидается завершения всех, независимо от результата. Возвращает массив объектов вида `{ status: 'fulfilled', value }` или `{ status: 'rejected', reason }` для каждого промиса.
* `Promise.race(promises)` — возвращает результат того промиса, который завершится первым (успешно или с ошибкой). Остальные игнорируются.
* `Promise.any(promises)` — возвращает результат первого успешно выполненного промиса. Если все промисы отклонены — падает с ошибкой `AggregateError`.

### Инструменты для запросов

* `fetch()` — встроенный в браузер API
* `axios` — популярная библиотека (авто-парсинг JSON, интерцепторы, отмена запросов)
* `XMLHttpRequest` — старый способ, почти не используется

### Что важно знать про Event Loop

JS однопоточный. Асинхронные операции (запросы, таймеры) уходят в **очередь микрозадач/макрозадач**, и выполняются после того как освободится main thread (call stack). Промисы — микрозадачи, они выполняются раньше макрозадач (setTimeout и т.д.).
