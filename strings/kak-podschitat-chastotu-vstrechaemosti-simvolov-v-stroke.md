# Как подсчитать частоту встречаемости символов в строке?

```javascript
function countCharacters(str) {
    const charCount = {};

    for (const char of str) {
        // Если символ уже есть в объекте, увеличиваем счетчик на 1.
        // Если символа нет, то (charCount[char] || 0) вернет 0, и мы прибавим 1.
        charCount[char] = (charCount[char] || 0) + 1;
    }

    return charCount;
}

const result = countCharacters("банан");
console.log(result); 
// Вывод: { б: 1, а: 2, н: 2 }
```

