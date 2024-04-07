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

### [3. Estructura del Programa](https://eloquent-javascript-es.vercel.app/04_data.html))

- La suma de un rango

```js
// Tu código aquí.

//function range(ini, end, inc=1) {
//  let result = []
//  for (a=ini; ini < end ? a <= end : a >= end; a += inc) {
//    result.push(a)
//    }
//  return result
//  }

//const range = (ini, end, inc = 1) => Array.from({ length: Math.ceil((end - ini + 1) / inc) }, (_, i) => ini + (i * inc));

const range = (ini, end, inc=1) => Array(Math.abs(end-ini)+1).
  fill(0).map( (_, b) => ini+(b*inc))

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
