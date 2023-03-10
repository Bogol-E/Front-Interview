# ๐ป Event Loop

![event-loop](https://user-images.githubusercontent.com/64779472/116123381-e7c02c80-a6fd-11eb-859b-f5375b051f01.PNG)

<br />

## ๐จ๐ปโ๐ป JS Engine(์๋จ ๊ทธ๋ฆผ์ ์ผ์ชฝ)

- ์๋ฐ์คํฌ๋ฆฝํธ ์์ง์ `Memory Heap`๊ณผ `Call Stack`์ผ๋ก ๊ตฌ์ฑ๋์ด ์๋ค.(ex. ๊ตฌ๊ธ์ V8 Engine)
- ์๋ฐ์คํฌ๋ฆฝํธ๋ `๋จ์ผ ์ค๋ ๋(Single Thread) ๊ธฐ๋ฐ ํ๋ก๊ทธ๋๋ฐ ์ธ์ด`์ธ๋ฐ, ์ด ์๋ฏธ๋ Call Stack์ด ํ๋๋ผ๋ ์ด์ผ๊ธฐ์ด๋ค.
  - Memory Heap: ๋ฉ๋ชจ๋ฆฌ ํ ๋น์ด ์ผ์ด๋๋ ๊ณณ(ex. ์ฐ๋ฆฌ๊ฐ ํ๋ก๊ทธ๋จ์ ์ ์ธํ ๋ณ์, ํจ์ ๋ฑ์ด ๋ด๊ฒจ์ ธ ์์)
  - Call Stack: ์ฝ๋๊ฐ ์คํ๋  ๋ ์์ด๋ ๊ณณ Stack ํํ๋ก ์์ธ๋ค. (Stack์ ์๋ฃ๊ตฌ์กฐ ์ค ํ๋๋ก, ํ์์ ์ถ(LIFO) ๋ฐฉ์์ด๋ค.)
- ๋จ์ผ ์ฝ ์คํ์ ๊ฐ๋ ๋ค๋ ์๋ฏธ๋, ์์ฒญ์ด `๋๊ธฐ์ ์ผ๋ก ์ฒ๋ฆฌ`๋๋ค๋ ๊ฒ์ ์๋ฏธํ๋ค.
- ๋น๋๊ธฐ ์์ฒญ์ ์ฒ๋ฆฌํ๊ธฐ ์ํด์๋ ์๋ฐ์คํฌ๋ฆฝํธ๋ฅผ ์คํํ๋ ํ๊ฒฝ์ธ `๋ธ๋ผ์ฐ์ `๋ `Node.js`๊ฐ ๋ด๋นํ๋ค.

<br />

## ๐จ๐ปโ๐ป Web API

- Web API๋ JS Engine์ด ์๋๋ค.
- Web API๋ ๋ธ๋ผ์ฐ์ ์์ ์ ๊ณตํ๋ API๋ก, DOM, AJAX, Timeout ๋ฑ์ด ์๋ค.
- Call Stack์์ ์คํ๋ ๋น๋๊ธฐ ํจ์๋ Web API๋ฅผ ํธ์ถํ๊ณ , Web API๋ ์ฝ๋ฐฑ ํจ์๋ฅผ Callback Queue์ ๋ฃ๋๋ค.

<br />

## ๐จ๐ปโ๐ป Event Loop

- Event Loop๋ Call Stack๊ณผ Callback Queue์ ์ํ๋ฅผ ์ฒดํฌํ์ฌ, Call Stack์ด ๋น ์ํ๊ฐ ๋๋ฉด, Callback Queue์ ์ฒซ๋ฒ์งธ ์ฝ๋ฐฑ ํจ์๋ฅผ Call Stack์ ๋ฃ๋๋ค.
- ์์ ๊ฐ์ ๋ฐ๋ณต์ ์ธ ํ๋์ผ ํฑ(Tick)์ด๋ผ๊ณ  ๋ถ๋ฅธ๋ค.
- **๊ณผ์  ์ ๋ฆฌ)**
  1. V8 ์์ง์์ ์ฝ๋๊ฐ ์คํ๋๋ฉด, Call Stack์ ์์ธ๋ค.
  2. Stack์ ํ์์ ์ถ์ ๋ฃฐ์ ๋ฐ๋ผ ์ ์ผ ๋ง์ง๋ง์ ๋ค์ด์จ ํจ์๊ฐ ๋จผ์  ์คํ๋๋ฉฐ, Stack์ ์์ฌ์ง ํจ์๊ฐ ๋ชจ๋ ์คํ๋๋ค.
  3. ๋น๋๊ธฐ ํจ์๊ฐ ์คํ๋๋ค๋ฉด, Web API๊ฐ ํธ์ถ๋๋ค.
  4. Web API๋ ๋น๋๊ธฐ ํจ์์ ์ฝ๋ฐฑ ํจ์๋ฅผ CallBack Queue์ ๋ฃ๋๋ค.
  5. Event Loop๋ Call Stack์ด ๋น ์ํ๊ฐ ๋๋ฉด Callback Queue์ ์๋ ์ฒซ๋ฒ์งธ ์ฝ๋ฐฑ์ Call Stack์ผ๋ก ์ด๋์ํจ๋ค.

<br />

## ๐จ๐ปโ๐ป Callback Queue

- Callback Queue์๋ `Task Queue`์ `Microtask Queue`๊ฐ ์๋ค.
- Task Queue๋ setTimeout(), setInterval(), UI๋ ๋๋ง, requestAnimationFrame()์ด ๋ด๊ธด๋ค.
- Microtask Queue๋ Promise(then), MutaionObserver๊ฐ ๋ด๊ธด๋ค.
- Event Loop๋ ์ฐ์ ์ ์ผ๋ก Microtask Queue๋ฅผ ํ์ธํ๋ค. ๋ง์ฝ, Microtask Queue์ ์ฝ๋ฐฑ์ด ์๋ค๋ฉด, ์ด๋ฅผ ๋จผ์  Call Stack์ ๋ด๋๋ค. ๊ทธ๋ฆฌ๊ณ  Microtask Queue์ ์ฒ๋ฆฌํด์ผ ํ  ์ฝ๋ฐฑ ํจ์๊ฐ ์๋ค๋ฉด, Task Queue์ ํ์ธ ํ ์ฒ๋ฆฌํ๋ค.

<br />

- **๋์ ์์ 1)**

```js
console.log('script start');

setTimeout(function () {
  console.log('setTimeout');
}, 0);

Promise.resolve()
  .then(function () {
    console.log('promise1');
  })
  .then(function () {
    console.log('promise2');
  });

console.log('script end');
```

<br />

- **๊ฒฐ๊ณผ**

```
  script start
  script end
  promise1
  promise2
  setTimeout
```

<br />

- ์ ๊ฒฐ๊ณผ์ ์ด์ ๋ Promise๋ Microtask Queue์ ๋ด๊ธฐ๊ณ , setTimeout์ Task Queue์ ๋ด๊ธฐ๊ธฐ ๋๋ฌธ์, ์ฐ์  ์์๊ฐ ๋์ Promise์ ์ฝ๋ฐฑ ํจ์๊ฐ ๋จผ์  ์คํ๋๊ณ , ๊ทธ ๋ค์ setTimeout์ ์ฝ๋ฐฑ ํจ์๊ฐ ์คํ๋๋ค.

<br />

## ๐จ๐ปโ๐ป ๊ทธ๋ฆผ์ผ๋ก ๋ณด๋ ๋์ ๋ฐฉ์

```js
  console.log('์ฝ ์คํ!');
  setTimeout(() => console.log('ํ์คํฌ ํ!'), 0);
  Promise.resolve().then(() => console.log('๋ง์ดํฌ๋กํ์คํฌ ํ!'));

  //๊ฒฐ๊ณผ
  ์ฝ ์คํ!
  ๋ง์ดํฌ๋กํ์คํธ ํ!
  ํ์คํธ ํ!
```

<br />

![eventlooptask1](https://user-images.githubusercontent.com/64779472/116126402-92861a00-a701-11eb-9965-1695d35eda8a.png)

- ์ ์ผ ๋จผ์ , '์คํฌ๋ฆฝํธ ์คํ' Task๊ฐ Task Queue์ ๋ค์ด๊ฐ๋ค.

![eventlooptask2](https://user-images.githubusercontent.com/64779472/116126407-93b74700-a701-11eb-80a1-78a2b7476d48.png)

- ์ดํ, ์ด๋ฒคํธ ๋ฃจํ๊ฐ ๊ทธ Task๋ฅผ ๊ฐ์ ธ์์ ๋ก๋ ๋ ์คํฌ๋ฆฝํธ๋ฅผ ์คํ์ํจ๋ค. ๋ฐ๋ผ์ ๋งจ ์ฒ์์ **console.log**๊ฐ ์คํ ๋๋ค.

![eventlooptask3](https://user-images.githubusercontent.com/64779472/116126408-93b74700-a701-11eb-9e8d-6dbc6b8f77d5.png)

- ๊ทธ ๋ค์, setTimeout() ์ด Call Stack์ผ๋ก ๊ฐ๊ณ  Web API๊ฐ ์ด๋ฅผ ๋ฐ์์ ํ์ด๋จธ๋ฅผ ๋์์ํจ๋ค.

![eventlooptask4](https://user-images.githubusercontent.com/64779472/116126412-944fdd80-a701-11eb-970c-5a147c91f2c2.png)

- ํ์ด๋จธ๊ฐ ๋๋๋ฉด, setTimeout()์ ์ฝ๋ฐฑ ํจ์๋ฅผ Task Queue์ ๋ฃ๋๋ค.

![eventlooptask5](https://user-images.githubusercontent.com/64779472/116126414-944fdd80-a701-11eb-9ee2-9f639c9a126f.png)

- Promise๊ฐ Call Stack์ผ๋ก ๊ฐ๊ณ  ์ฝ๋ฐฑ ํจ์๋ฅผ Microtask Queue์ ๋ฃ๋๋ค.

![eventlooptask6](https://user-images.githubusercontent.com/64779472/116126415-94e87400-a701-11eb-81bb-6fa5592f8253.png)

- ์ด๋ฒคํธ ๋ฃจํ๋ Microtask Queue์์ ์ ์ผ ์ค๋๋ Task์ธ Promise์ ์ฝ๋ฐฑ ํจ์๋ฅผ ๊ฐ์ ธ์ Call Stack์ ๋ฃ๋๋ค.

![eventlooptask7](https://user-images.githubusercontent.com/64779472/116126417-95810a80-a701-11eb-9bb0-0b92e38603b6.png)

- Promise์ ์ฝ๋ฐฑ ํจ์๊ฐ ๋๋๊ณ  Task Queue์์ ์ ์ผ ์ค๋ ๋ Task์ธ setTimeout()์ ์ฝ๋ฐฑ ํจ์๋ฅผ ๊ฐ์ ธ์ Call Stack์ ๋ฃ๋๋ค.

![eventlooptask8](https://user-images.githubusercontent.com/64779472/116126419-95810a80-a701-11eb-8de9-19ae91d34d07.png)

- setTimeout()์ ์ฝ๋ฐฑ ํจ์๊ฐ ๋๋๋ฉด Call Stack์ด ๋น๊ฒ ๋๊ณ  ํ๋ก๊ทธ๋จ์ด ์ข๋ฃ๋๋ค.

<br />

## ์ฐธ๊ณ 

https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/event-loop.md <br /> https://velog.io/@thms200/Event-Loop-%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%A3%A8%ED%94%84 <br />
