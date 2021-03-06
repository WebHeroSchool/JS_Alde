
#  JavaScript Best Practice Guide

### 1. Используйте === вместо ==

В JavaScript существует два разных типа операций сравния: === / !== и == / !=. Считается хорошим тоном всегда использовать первую пару для сравнения.

```
“Если два операнда одного типа и значения, то === вернет true, а !== false” 
```

### 2. Объявляйте переменные для 'for" вне циклов

Когда выполняете долгий цикл «for» не заставляйте делать движок больше работы чем нужно.

```js
/* Плохо */

for(var i = 0; i < someArray.length; i++) {  
   var container = document.getElementById('container');  
   container.innerHtml += 'my number: ' + i;  
   console.log(i);  
}  


/* Хорошо */

var container = document.getElementById('container');  
for(var i = 0, len = someArray.length; i < len;  i++) {  
   container.innerHtml += 'my number: ' + i;  
   console.log(i);  
} 
```

### 3. Уменьшите количество глобальных переменных

«Сведением количества глобальных переменных к одному, вы значительно снижаете шансы нежелательного взаимодействия с другими приложениями, виджетами или библиотеками.» 

Douglas Crockford
```js
/* Плохо */

var name = 'Jeffrey';  
var lastName = 'Way';  
  
function doSomething() {...}  
  
console.log(name); // Jeffrey -- or window.name  

/* Хорошо */

var DudeNameSpace = {  
   name : 'Jeffrey',  
   lastName : 'Way',  
   doSomething : function() {...}  
}  
console.log(DudeNameSpace.name); // Jeffrey 
```

### 4. Точки с запятыми обязательны
Каждое предложение должно отделяться точкой с запятой. Полагаться на автоматическую вставку точек с запятыми запрещается.
```js
/*Плохо*/
let luke = {}
let leia = {}
[luke, leia].forEach(jedi => jedi.father = 'vader')

/*Хорошо*/
let luke = {};
let leia = {};
[luke, leia].forEach((jedi) => {
  jedi.father = 'vader';
});
```

### 5.  Комментируйте ваш код

Это кажется излишним в начале, но поверьте мне вы действительно ХОТИТЕ комменировать ваш код как можно лучше. Что случится когда вы вернетесь к проекту через несколько месяце чтобы обнаружить что не помните что этот кусок кода делаете. Или что будет если ваш коллега будет смотреть ваш код в процессе код-ревью? Всегда, повторяю всегда комментируйте важные части кода.

### 6. Длинный список переменных? Опустите „var“ и используйте запятые

```js
/*Плохо*/

var someItem = 'some string';  
var anotherItem = 'another string';  
var oneMoreItem = 'one more string'; 

/*Хорошо*/

var someItem = 'some string',  
    anotherItem = 'another string',  
    oneMoreItem = 'one more string';
```

### 7.  Используйте таймер консоли для оптимизации кода

Нужен быстрый и легкий способ чтобы определить как много времени займет операция? Используйте консольный таймер для логирования результатов.

```js
function TimeTracker(){  
 console.time("MyTimer");  
 for(x=5000; x > 0; x--){}  
 console.timeEnd("MyTimer");  
}
```

### 8. Стрелочные функции предпочтительны
Стрелочные функции придают краткость синтаксису и исправляют многие сложности, с ним связанные. Отдавайте предпочтение стрелочным функциям, а не ключевым словам, особенно для вложенных функций.

```js
/*Плохо*/

[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});

/*Хорошо*/

[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```

### 9. Используйте строки шаблона вместо конкатенации
Используйте строки шаблона (отделенные с помощью `), а не сложную конкатенацию строк, особенно если задействованы несколько строковых литералов. Строки шаблона могут охватывать несколько строк.

```js
/*Плохо*/

function sayHi(name) {
  return 'How are you, ' + name + '?';
}

function sayHi(name) {
  return ['How are you, ', name, '?'].join();
}

/*Хорошо*/

function sayHi(name) {
  return `How are you, ${name}?`;
}

```

### 10. Кавычки
Всегда в коде скрипта используйте одинарные кавычки, если не требуется иного. Двойные кавычки допустимы, если в этой же строке необходимо использовать апостроф (') или одинарные кавычки для других целей.

```js
/*Плохо*/
var string = "строка";

/*Хорошо*/
var string = 'строка';
var phrase = "you're next";
```
=======

