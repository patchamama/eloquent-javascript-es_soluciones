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

[2. Estructura del Programa](https://eloquent-javascript-es.vercel.app/02_program_structure.html)

- Haciendo un triángulo con bucles

```js
for (character = "#"; character.length <= 7; character += "#") {
  console.log(character);
}
```

- FizzBuzz

```js
for (num = 1; num <= 100; num++) {
  let word = "";
  if (num % 3 === 0) {
    word = "Fizz";
  }
  if (num % 5 === 0) {
    word += "Buzz";
  }
  console.log(word ? word : num);
}
```

- Tablero de ajedrez

```js
let len = Number(prompt("Ancho del tablero? "));
if (Number.isNaN(len)) {
  console.error("Ancho del tablero debe de ser un número.");
} else {
  for (row = 0; row < len; row++) {
    let whiteSt = row % 2 === 0 ? " " : "#";
    let blackSt = row % 2 === 0 ? "#" : " ";
    let rowSt = "";
    for (col = 0; col < len; col++) {
      rowSt += col % 2 === 0 ? whiteSt : blackSt;
    }
    console.log(rowSt);
  }
}
```

- [3. Funciones](https://eloquent-javascript-es.vercel.app/03_functions.html)

- Mínimo

```js
const min = (a, b) => {
  return a < b ? a : b;
};

console.log(min(0, 10));
// → 0
console.log(min(0, -10));
// → -10
```
