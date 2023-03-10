# ๐ป async/await

<br />

## ๐จ๐ปโ๐ป async/await ์ด๋?

- async/await๋ `ES8(ECMAScript2017)`์ ๊ณต์ ์คํ์ผ๋ก ๋น๊ต์  ์ต๊ทผ์ ์ ์๋ ๋ฌธ๋ฒ์ด๋ค.
- async/await๋ฅผ ์ฌ์ฉํ๋ฉด ๋น๋๊ธฐ ์ฝ๋๋ฅผ ์์ฑํ  ๋ ๋น๊ต์  ์ฝ๊ณ  ๋ชํํ๊ฒ ์ฝ๋๋ฅผ ์์ฑํ  ์ ์๋ค.
- ์๋ฐ์คํฌ๋ฆฝํธ๋ `์ฑ๊ธ ์ค๋ ๋ ํ๋ก๊ทธ๋๋ฐ ์ธ์ด`์ด๊ธฐ ๋๋ฌธ์ ๋น๋๊ธฐ์ฒ๋ฆฌ๊ฐ ํ์์ ์ด๋ค.
- ๋น๋๊ธฐ ์ฒ๋ฆฌ๋ ๊ทธ ๊ฒฐ๊ณผ๊ฐ ์ธ์  ๋ฐํ๋ ์ง ์ ์ ์๊ธฐ ๋๋ฌธ์ ์ด๋ฅผ ๋๊ธฐ์์ผ๋ก ์ฒ๋ฆฌํ๋ ๊ธฐ๋ฒ๋ค์ด ์ฌ์ฉ๋์ด์ผ ํ๋ค. ๋ํ์ ์ผ๋ก `setTimeout`,`Callback`,`Promise`์ด๋ค.
- ์ 3๊ฐ์ง ๊ธฐ๋ฒ๋ค๋ ํ๋ฅญํ์ง๋ง ๋ฌธ์ ์ ์ด ์กด์ฌํ๋ค. async/await๋ ์ด๋ฅผ ํด๊ฒฐํจ๊ณผ ๋์์ ์ฌ์ฉ๋ฒ์ด ๊ฐ๋จํด์ก๋ค.

<br />

## ๐จ๐ปโ๐ป async ํค์๋

- async ํค์๋๋ ํญ์ function ์์ ์์นํฉ๋๋ค.

```js
async function f() {
  return 1;
}

console.log(f()); // Promise { 1 }
console.log(f().then()); // Promise { <pending> }
f().then((res) => console.log(res)); //1
```

- ๐ function ์์ async๋ฅผ ๋ถ์ด๋ฉด ํด๋น ํจ์๋ ํญ์ Promise๋ฅผ ๋ฐํํ๋ค.
- ๐ Promise๊ฐ ์๋ ๊ฐ์ ๋ฐํํ๋๋ผ๋ `์ดํ ์ํ์ ํ๋ผ๋ฏธ์ค(resolved promise)`๋ก ๊ฐ์ ๊ฐ์ธ ์ดํ๋ Promise๊ฐ ๋ฐํ๋๋๋ก ํ๋ค.

<br />

```js
async function f() {
  return Promise.resolve(1);
}

console.log(f()); // Promise { <pending> }
console.log(f().then()); // Promise { <pending> }
f().then((res) => console.log(res)); // 1
```

- ์ ์ฝ๋์ ๊ฐ์ด ๋ช์์ ์ผ๋ก Promise๋ฅผ ๋ฐํํ๋ ๊ฒ๋ ๊ฐ๋ฅํ๋ฐ, ๊ฒฐ๊ณผ๋ ๊ฑฐ์ ๋์ผํ๋ค.

<br />

## ๐จ๐ปโ๐ป await ํค์๋

- ์๋ฐ์คํฌ๋ฆฝํธ๋ await ํค์๋๋ฅผ ๋ง๋๋ฉด Promise๊ฐ `์ฒ๋ฆฌ(Settled)`๋  ๋๊น์ง ๊ธฐ๋ค๋ฆฐ๋ค. ๊ฒฐ๊ณผ๋ ๊ทธ ์ดํ ๋ฐํ๋๋ค.

```js
async function f() {
  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("์๋ฃ!"), 1000);
  });
  let result = await promise; // ํ๋ผ๋ฏธ์ค๊ฐ ์ดํ๋  ๋๊น์ง ๊ธฐ๋ค๋ฆผ (*)

  console.log(result); // "์๋ฃ!"
}

f();
```

- ์ ์ฝ๋์์ ํจ์๋ฅผ ํธ์ถํ๊ณ , ํจ์ ๋ณธ๋ฌธ์ด ์คํ๋๋ ๋์ค์ `(*)`๋ก ํ์ํ ์ค์์ ์คํ์ด ์ ์ `์ค๋จ`๋์๋ค๊ฐ Promise๊ฐ ์ฒ๋ฆฌ๋๋ฉด ์คํ์ด ์ฌ๊ฐ๋๋ค.
- ์ด๋ ํ๋ผ๋ฏธ์ค ๊ฐ์ฒด์ ๊ฒฐ๊ณผ ๊ฐ์ด ๋ณ์ result์ ํ ๋น ๋๋ค. ๋ฐ๋ผ์ ์ ์ฝ๋๋ฅผ ์คํํ๋ฉด 1์ด ๋ค์ `์๋ฃ!`๊ฐ ์ถ๋ ฅ๋๋ค.

<br />

- ๐ `await(๊ธฐ๋ค๋ฆฌ๋ค๋ผ๋ ๋ป์ ๊ฐ์ง ์๋จ์ด)`๋ ๋ง ๊ทธ๋๋ก Promise๊ฐ ์ฒ๋ฆฌ๋  ๋๊น์ง ํจ์ ์คํ์ ๊ธฐ๋ค๋ฆฌ๊ฒ ๋ง๋ ๋ค.
- Promise๊ฐ ์ฒ๋ฆฌ ๋๋ฉด ๊ทธ ๊ฒฐ๊ณผ์ ํจ๊ป ์คํ์ด ์ฌ๊ฐ๋๋ค. Promise๊ฐ ์ฒ๋ฆฌ๋๊ธธ ๊ธฐ๋ค๋ฆฌ๋ ๋์์ `์์ง์ด ๋ค๋ฅธ ์ผ(๋ค๋ฅธ ์คํฌ๋ฆฝํธ ์คํ, ์ด๋ฒคํธ ์ฒ๋ฆฌ ๋ฑ)`์ ํ  ์ ์๊ธฐ ๋๋ฌธ์ CPU ๋ฆฌ์์ค๊ฐ ๋ญ๋น๋์ง ์๋๋ค.
- await์ `promise.then()`๋ณด๋ค ์ข ๋ ์ธ๋ จ๋๊ฒ ํ๋ก๋ฏธ์ค์ ๊ฒฐ๊ณผ ๊ฐ์ ์ป์ ์ ์๋ค.

<br />

## ๐จ๐ปโ๐ป async/await ๊ธฐ๋ณธ ์์ 

```js
function fetchItems() {
  return new Promise(function (resolve, reject) {
    let items = [1, 2, 3];
    resolve(items);
  });
}

async function logItems() {
  var resultItems = await fetchItems();
  console.log(resultItems); // [1,2,3]
}

logItems();
```

- fetchItems() ํจ์๋ Promise ๊ฐ์ฒด๋ฅผ ๋ฐํํ๋ ํจ์์ด๋ค. (Promise๋ `์๋ฐ์คํฌ๋ฆฝํธ ๋น๋๊ธฐ ์ฒ๋ฆฌ๋ฅผ ์ํ ๊ฐ์ฒด`)
- fetchItems() ํจ์๋ฅผ ์คํํ๋ฉด Promise๊ฐ ์ดํ(Resolved)๋๋ฉฐ ๊ฒฐ๊ณผ ๊ฐ์ `items`๋ฐฐ์ด์ด๋ค.
- logItems() ํจ์๋ฅผ ์คํํ๋ฉด fetchItems() ํจ์์ ๊ฒฐ๊ณผ ๊ฐ์ธ `items`๋ฐฐ์ด์ด `resultItems` ๋ณ์์ ๋ด๊ธด๋ค.
- ์ฌ๊ธฐ์ await์ ์ฌ์ฉํ์ง ์์๋ค๋ฉด ๋ฐ์ ์ฝ๋ ์ฒ๋ผ ๋ฐ์ดํฐ๋ฅผ ๋ฐ์์จ ์์ ์ ์ฝ์์ ์ถ๋ ฅํ  ์ ์๊ฒ `์ฝ๋ฐฑ ํจ์`๋ `.then()` ๋ฑ์ ์ฌ์ฉํด์ผ ํ๋ค.

```js
function fetchItems() {
  return new Promise(function (resolve, reject) {
    let items = [1, 2, 3];
    resolve(items);
  });
}

function logItems() {
  var resultItems = fetchItems();
  resultItems.then((res) => console.log(res)); // [1,2,3]
}

logItems();
```

<br />

## ๐จ๐ปโ๐ป async/await ์์ธ ์ฒ๋ฆฌ

- async/await์์ ์์ธ๋ฅผ ์ฒ๋ฆฌํ๋ ๋ฐฉ๋ฒ์ `try/catch`์ด๋ค.
- Promise์์ ์๋ฌ ์ฒ๋ฆฌ๋ฅผ ์ํด `.catch()`๋ฅผ ์ฌ์ฉํ๋ ๊ฒ์ฒ๋ผ async์์ `catch () { ... }`๋ฅผ ์ฌ์ฉํ๋ค.

```js
async function logTodoTitle() {
  try {
    const user = await fetchUser();
    if (user.id === 1) {
      const todo = await fetchTodo();
      console.log(todo.title); // delectus aut autem
    }
  } catch (error) {
    console.log(error);
  }
}
```

<br />

## ์ฐธ๊ณ 

https://joshua1988.github.io/web-development/javascript/js-async-await/
https://ko.javascript.info/async-await
https://blueshw.github.io/2018/02/27/async-await/
