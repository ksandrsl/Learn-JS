**Символы**

Все спецсимволы начинаются с обратного слеша, `\` — так называемого «символа экранирования».

```js
alert( 'I_\'_m the Walrus!' ); // _I'm_ the Walrus!
```
- `\n` Перевод строки
- `\\` Обратный слеш
- `\uXXXX`Символ в кодировке UTF-16 с шестнадцатеричным кодом `XXXX`, например, `\u00A9` — юникодное представление знака копирайта, `©`. Код должен состоять ровно из 4 шестнадцатеричных цифр.
```js
// © 
alert( "\u00A9" );
// Длинные юникодные коды
// 😍, лицо с улыбкой и глазами в форме сердец 
alert( "\u{1F60D}" );
```

---

**Длина строки**

`str.length` содержит длину строки — это числовое свойство, а не функция, добавлять скобки не нужно.

---

**Доступ к символам**

```js
let str = `Hello`; 
// получаем первый символ 
alert( str[0] ); // H 
alert( str.charAt(0) ); // H 

// получаем последний символ 
alert( str[str.length - 1] ); // o
```

если символ отсутствует, тогда `[]` вернёт `undefined`, а `charAt` — пустую строку.

Также можно перебрать строку посимвольно, используя `for..of`:

```js
for (let char of "Hello") { 
alert(char); // H,e,l,l,o (char — сначала "H", потом "e", потом "l" и т. д.) 
}
```

**Строки неизменяемы**

```js
let str = 'Hi'; 
str[0] = 'h'; // ошибка

str = 'h' + str[1]; // можно заменить строку
```

---

**Изменение регистра**

```js
alert( 'Interface'.toUpperCase() ); // INTERFACE 
alert( 'Interface'.toLowerCase() ); // interface

alert( 'Interface'[0].toLowerCase() ); // 'i'
```

---

**Поиск подстроки**

- `str.indexOf(substr, pos)` - ищет подстроку `substr` в строке `str`, начиная с позиции `pos`, и возвращает позицию, на которой располагается совпадение, либо `-1` при отсутствии совпадений.

Чтобы найти все вхождения подстроки, нужно запустить `indexOf` в цикле.
```js
let str = "Ослик Иа-Иа посмотрел на виадук"; 
let target = "Иа";

let pos = -1; 
while ((pos = str.indexOf(target, pos + 1)) != -1) { 
alert( pos ); 
}
```

- `str.lastIndexOf(substr, pos)` ищет с конца строки к её началу.

- `str.includes(substr, pos)` - возвращет `true`, если в строке `str` есть подстрока `substr`, либо `false`, если нет.

- `str.startsWith` и `str.endsWith` проверяют, начинается ли и заканчивается ли строка определённой строкой:

```js
alert( "Widget".startsWith("Wid") ); // true, "Wid" — начало "Widget" 
alert( "Widget".endsWith("get") ); // true, "get" — окончание "Widget"
```

---

**Получение подстроки**

Есть 3 метода для получения подстроки:

- `slice(start, end)` 
	- возвращает часть строки от `start` до `end` (не включая `end`) 
	- можно передавать отрицательные значения

- `substring(start, end)` 
	- возвращает часть строки между `start` и `end` 
	- отрицательные значения равнозначны `0`

- `substr(start, length)` 
	- возвращает `length` символов, начиная от `start` 
	- значение `start` может быть отрицательным

---
```js
let str = "stringify"; 

// 'strin', символы от 0 до 5 (не включая 5)
alert( str.slice(0, 5) ); 

// ringify, с позиции 2 и до конца
alert( str.slice(2) ); 

// начинаем с позиции 4 справа, а заканчиваем на позиции 1 справа 
alert( str.slice(-4, -1) ); // gif

// для substring эти два примера — одинаковы 
alert( str.substring(2, 6) ); // "ring" 
alert( str.substring(6, 2) ); // "ring"

// ring, получаем 4 символа, начиная с позиции 2 
alert( str.substr(2, 4) );

// gi, получаем 2 символа, начиная с позиции 4 с конца строки 
alert( str.substr(-4, 2) );
```
---
**Сравнение строк**

- `str.codePointAt(pos)` возвращает код для символа, находящегося на позиции `pos`.
- `String.fromCodePoint(code)` создаёт символ по его коду `code`
-  Все строчные буквы идут после заглавных, так как их коды больше.
-  Такие буквы как `Ö` находятся вне основного алфавита, их код больше, чем у любой буквы от `a` до `z`.

-  `str.localeCompare(str2)` возвращает число, которое показывает, какая строка больше в соответствии с правилами языка:
	- Отрицательное число, если `str` меньше `str2`.
	- Положительное число, если `str` больше `str2`.
	- `0`, если строки равны.

---
У этого метода есть два дополнительных аргумента:
- указать язык
- дополнительные правила (чувствительность к регистру, различия между `"a"` и `"á"`).

---
Строки также имеют ещё кое-какие полезные методы:

-   `str.trim()` — убирает пробелы в начале и конце строки.
-   `str.repeat(n)` — повторяет строку `n` раз.

---

[[Primitives]]