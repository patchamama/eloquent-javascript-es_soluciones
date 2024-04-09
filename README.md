# Soluciones al curso de Javascript Eloquent 4ta edición

Curso en español: https://eloquent-javascript-es.vercel.app/

Curso original en inglés: https://eloquentjavascript.net

Code sandbox y ejercicios: https://eloquentjavascript.net/code/

Debug online: https://pythontutor.com/render.html#mode=display

Javascript references: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference

## Ejemplos interesantes

- [3. Funciones](https://eloquent-javascript-es.vercel.app/03_functions.html)

```js
function multiplier(factor) {
  return (number) => number * factor;
}

let twice = multiplier(2);
console.log(twice(5));
// → 10
```

### Cortocircuito de operadores lógicos
 El operador ?? se asemeja a ||, pero devuelve el valor de la derecha solo si el de la izquierda es null o undefined, no si es algún otro valor que se pueda convertir en false. A menudo, este comportamiento es preferible al de ||. El operador && funciona de manera similar pero en sentido contrario. Cuando el valor a su izquierda es algo que se convierte en false, devuelve ese valor, y de lo contrario devuelve el valor de su derecha.

```js
console.log(null || "usuario")
// → usuario
console.log("Agnes" || "usuario") // aquí nunca "usuario" se evalua
// → Agnes
console.log(0 || 100);
// → 100
console.log(0 ?? 100);
// → 0
console.log(null ?? 100);
// → 100
console.log(false && 100);  //aquí 100 no se valua
// → false

```

## Respuesta a ejercicios

### [2. Estructura del Programa](https://eloquent-javascript-es.vercel.app/02_program_structure.html)

- Haciendo un triángulo con bucles

```js
//for (character = "#"; character.length <= 7; character += "#") {
//  console.log(character);
//}

console.log(
  Array(7)
    .fill("#")
    .map((_, index) => "#".repeat(index + 1))
    .join("\n")
);
```

- FizzBuzz

```js
//for (num = 1; num <= 100; num++) {
//  let word = "";
//  if (num % 3 === 0) {
//    word = "Fizz";
//  }
//  if (num % 5 === 0) {
//    word += "Buzz";
//  }
//  console.log(word ? word : num);
//}

for (let num = 1; num <= 100; num++)
  console.log((num % 3 ? "" : "Fizz") + (num % 5 ? "" : "Buzz") || num);
```

- Tablero de ajedrez

```js
let len = Number(prompt("Ancho del tablero? "));
if (Number.isNaN(len)) {
  console.error("Ancho del tablero debe de ser un número.");
} else {
  //  for (row = 0; row < len; row++) {
  //    let whiteSt = row % 2 === 0 ? " " : "#";
  //    let blackSt = row % 2 === 0 ? "#" : " ";
  //    let rowSt = "";
  //    for (col = 0; col < len; col++) {
  //      rowSt += col % 2 === 0 ? whiteSt : blackSt;
  //    }
  //    console.log(rowSt);
  console.log(
    Array(len)
      .fill("")
      .map((_, index) => (index % 2 === 0 ? "# " : " #").repeat(len))
      .join("\n")
  );

  // Mejora con una sola línea y una función
  const generateBoard = (size) =>
    [...Array(size)]
      .map((_, y) =>
        [...Array(size)].map((_, x) => ((x + y) % 2 === 0 ? " " : "#")).join("")
      )
      .join("\n");
  console.log(generateBoard(10));
}
```

### [3. Funciones](https://eloquent-javascript-es.vercel.app/03_functions.html)

- Mínimo

```js
const min = (a, b) => (a < b ? a : b);

console.log(min(0, 10));
// → 0
console.log(min(0, -10));
// → -10
```

- Recursión

```js
//const isEven = n => {
//  if (n < 0) return "??";
//  if (n === 0) return true
//  else if (n === 1) return false
//  else return isEven(n-2);
//}

const isEven = (n) =>
  n < 0 ? "??" : n === 0 ? true : n === 1 ? false : isEven(n - 2);

console.log(isEven(50));
// → true
console.log(isEven(75));
// → false
console.log(isEven(-1));
// → ??
```

- Contando frijoles

```js
//const countBs = str => {
//  let count = 0
//  for (p = 0; p < str.length; p++) {
//    count += (str.at(p) === 'B') ? 1: 0;
//  }
//  return count
//}

const countBs = (str) =>
  str.split("").reduce((a, b) => (b === "B" ? a + 1 : a), 0);

//const countChar = (str, char) => {
//  let count = 0
//  for (p = 0; p < str.length; p++) {
//    count += (str.at(p) === char) ? 1: 0;
//  }
//  return count
//}

const countChar = (str, char) =>
  str.split("").reduce((a, b) => (b === char ? a + 1 : a), 0);

console.log(countBs("BOB"));
// → 2
console.log(countChar("kakkerlak", "k"));
// → 4
```

### [4. Estructura del Programa](https://eloquent-javascript-es.vercel.app/04_data.html)

- La suma de un rango

```js
//function range(ini, end, inc=1) {
//  let result = []
//  for (a=ini; ini < end ? a <= end : a >= end; a += inc) {
//    result.push(a)
//    }
//  return result
//  }

const range = (ini, end, inc=1) => Array(Math.abs((end-ini)+1/inc))
  .fill(0).map( (_, b) => ini+(b*inc))

//function sum(arr) {
//  let result = 0
//  for (num of arr) {
//    result += num
//    }
//  return result
//  }

const sum = (arr) => arr.reduce( (a, b) => a+b,0)

console.log(range(1, 10));
// → [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
console.log(range(5, 2, -1));
// → [5, 4, 3, 2]
console.log(sum(range(1, 10)));
// → 55

```

- Reversión de un array

```js
//function reverseArray(arr) {
//  let result = [];
//  for (elem of arr) {
//    result.unshift(elem);
//    }
//  return result;
//  }

const reverseArray = arr => 
  arr.reduce((acc, curr) => [curr, ...acc], []);

//function reverseArrayInPlace(arr) {
//  let temp = [...arr];
//  const tempLen = temp.length;
//  for (a=1; a <= tempLen; a++) {
//    const last = temp.pop()
//    arr.shift();
//    arr.push(last);
//    }
//  }

const reverseArrayInPlace = (arr) => { 
  for (let i = arr.length - 1; i >= 0; i--) arr.push(arr.splice(i, 1)[0]);
  }


let myArray = ["A", "B", "C"];
console.log(reverseArray(myArray));
// → ["C", "B", "A"];
console.log(myArray);
// → ["A", "B", "C"];
let arrayValue = [1, 2, 3, 4, 5];
reverseArrayInPlace(arrayValue);
console.log(arrayValue);
// → [5, 4, 3, 2, 1]
```

- Lista

```js
const arrayToList = (arr) => (!arr.length) 
  ? null
  : {value: arr[0], rest: arrayToList(arr.slice(1))}

const listToArray = (list) => (!list.rest) 
   ? list.value 
   : [].concat(list.value, listToArray(list.rest) )


function prepend(value, list) {
  return {value, rest: list}
  }

function nth(arr, pos) {
  return listToArray(arr)[pos]
  }

function nth1(arr, pos) {
  let i = 0;
  for (let nodo = arr; nodo; nodo = nodo.rest) {
    if (i === pos) {
      return nodo.value
      }
    i++
    }
  }

console.log(arrayToList([10, 20]));
// → {value: 10, rest: {value: 20, rest: null}}
console.log(listToArray(arrayToList([10, 20, 30])));
// → [10, 20, 30]
console.log(prepend(10, prepend(20, null)));
// → {value: 10, rest: {value: 20, rest: null}}
console.log(nth(arrayToList([10, 20, 30]), 1));
// → 20
console.log(nth1(arrayToList([10, 20, 30]), 1));
// → 20
```

- Comparación profunda

```js
//function deepEqual(val1, val2) {
//  if (typeof val1 !== typeof val2) return false
//  if ((typeof val1 == "object" && val1 != null) && 
//     (typeof val2 == "object" && val2 != null)) {
//    if (Object.keys(val1).length !== Object.keys(val2).length) return false;
//    for (vkey of Object.keys(val1)) {
//      if (!Object.keys(val2).includes(vkey)) return false
//      if ( !deepEqual(val1[vkey], val2[vkey]) ) return false
//    }
//  } else {
//    return val1 === val2
//  }
//  return true
//}


function deepEqual(val1, val2) {
  if (typeof val1 !== typeof val2) return false;
  
  if (typeof val1 !== "object" || val1 === null) {
    return val1 === val2;
  }
  
  const keys1 = Object.keys(val1);
  const keys2 = Object.keys(val2);
  
  if (keys1.length !== keys2.length) return false;
  
  return keys1.every(key => deepEqual(val1[key], val2[key]));
}

let obj = {here: {is: "an"}, object: 2};
console.log(deepEqual(obj, obj));
// → true
console.log(deepEqual(obj, {here: 1, object: 2}));
// → false
console.log(deepEqual(obj, {here: {is: "an"}, object: 2}));
// → true
```
