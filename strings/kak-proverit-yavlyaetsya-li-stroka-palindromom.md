# Как проверить, является ли строка палиндромом?

```javascript
function isPalindrome(str) {
    // 1. Приводим к нижнему регистру и удаляем все символы, кроме букв и цифр
    const cleanStr = str.toLowerCase().replace(/[^a-z0-9а-яё]/g, '');

    // 2. Разворачиваем строку: 
    // split('') - разбиваем на массив символов
    // reverse() - переворачиваем массив
    // join('') - собираем обратно в строку
    const reversedStr = cleanStr.split('').reverse().join('');

    return cleanStr === reversedStr;
}
```

