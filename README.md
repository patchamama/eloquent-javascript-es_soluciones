# Soluciones al curso de Javascript Eloquent 4ta edición

Url del curso: https://eloquent-javascript-es.vercel.app/

Debug online: https://pythontutor.com/render.html#mode=display

## Ejemplos interesantes

- [3. Funciones](https://eloquent-javascript-es.vercel.app/03_functions.html)

```js
function multiplier(factor) {
  return (number) => number * factor;
}

let twice = multiplier(2);
console.log(twice(5));
// → 10
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
