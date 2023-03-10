# π» XMLHttpRequestμ Fetch

<br />

## π¨π»βπ» XMLHttpRequest

- `XMLHttpRequest(XHR)` κ°μ²΄λ μλ²μ μνΈμμ©νκΈ° μν΄ μ¬μ©λ©λλ€.
- μ μ²΄ νμ΄μ§ μλ‘κ³ μΉ¨ μμ΄λ `URL`λ‘λΆν° λ°μ΄ν°λ₯Ό λ°μμ¬ μ μμ΅λλ€.
- μ΄λ μΉνμ΄μ§κ° μ¬μ©μκ° νκ³ μλ κ²μ λ°©ν΄νμ§ μμΌλ©΄μ νμ΄μ§μ μΌλΆλ₯Ό μλ°μ΄νΈ ν  μ μλλ‘ ν΄μ€λλ€.
- `XMLHttpRequest`λ `Ajax`νλ‘κ·Έλλ°μ΄ μμ£Ό μ¬μ©λ©λλ€.

<br />

```js
var xhr = new XMLHttpRequest();
xhr.onreadystatechange = function () {
  if (xhr.readyState === xhr.DONE) {
    if (xhr.status === 200 || xhr.status === 201) {
      console.log(xhr.responseText);
    } else {
      console.error(xhr.responseText);
    }
  }
};
xhr.open("GET", "http://localhost:3000/single-json");
xhr.send();
```

- μμ μ½λλ XHRμ κΈ°λ³Έ μμ μ΄λ€.

<br />

## π¨π»βπ» XMLHttpRequest λ©μλ

- new XMLHttpRequest( ): μλ‘μ΄ XMLHttpRequest κ°μ²΄ μμ±
- abort( ): νμ¬ μμ²­μ μ·¨μ.
- getAllResponseHeaders( ): `ν€λ μ λ³΄`λ₯Ό λ°ν.
- getResponseHeader( ): `νΉμ  ν€λ μ λ³΄`λ₯Ό λ°ν.
- open (method, url, async, user, psw): `HTTP μμ²­μ λν μμ±`μ μ§μ νλ€.
  - method : νλΌλ―Έν° μ μ‘ λ°©λ²μ μ§μ , `GET` λλ `POST`λ‘ μ§μ ν  μ μλ€.
  - url : HTTP μμ²­μ λ³΄λΌ μκ²© νμ΄μ§μ μ£Όμ.
  - async : μμ²­μ `λκΈ°`, `λΉλκΈ°` μ²λ¦¬ν μ§μ μ¬λΆ `true`μ΄λ©΄ λΉλκΈ°μ²λ¦¬, `false`λ©΄ λκΈ°λ‘ μ²λ¦¬(μλ΅ κ°λ₯)
  - user, pwd: http μμ²­μ λν μΈμ¦μ΄ νμν  κ²½μ° μ§μ ν  μ μλ κ³μ  μ λ³΄(μλ΅ κ°λ₯)
- send( ): μλ²μ μμ²­ λ³΄λ΄κΈ°. `GET λ°©μ` μμ²­μΌ λ μ¬μ©.
- send(string): μλ²μ μμ²­ λ³΄λ. `POST λ°©μ` μμ²­μΌ λ μ¬μ©.
- setRequestHeader( ): `key/value`μμ HTTP ν€λλ₯Ό μ μ‘ λͺ©λ‘μ λνλ€.

<br />

## π¨π»βπ» XMLHttpRequest μμ±

- .onreadystatechange: HTTPμμ²­μ `μν λ³ν`μ λ°λΌ νΈμΆλλ `μ΄λ²€νΈ νΈλ€λ¬`μλλ€. μ¦ μ΄ ν¨μλ μλ²μμ μλ΅μ΄ λμ°©ν  λκΉμ§ `readyState` νλ‘νΌν° κ°μ λ³νμ λ°λΌ μ΄ 5λ² νΈμΆλλ€.
  - 0 (UNSENT) : XMLHttpRequest κ°μ²΄κ° μμ±λ¨.
  - 1 (OPENED) : open() λ©μλκ° μ±κ³΅μ μΌλ‘ μ€νλ¨.
  - 2 (HEADERS_RECEIVED) : HTTP μμ²­μ λ³΄λ΄μ΄ μ²λ¦¬νκ³  μλ μ€. ν€λλ μ½μ μ μλ μν.
  - 3 (LOADING) : μμ²­ν λ°μ΄ν°λ₯Ό μ²λ¦¬ μ€μ.
  - 4 (DONE) : μμ²­ν λ°μ΄ν°μ μ²λ¦¬κ° μλ£λμ΄ μλ΅ν  μ€λΉκ° μλ£λ¨. λΉλ‘μ responseText μ responseXML μμ±μ μ½μ μ μλ μν.

```js
switch (httpRequest.readyState) {
  case XMLHttpRequest.UNSET:
    currentState += "νμ¬ XMLHttpRequest κ°μ²΄μ μνλ UNSET μλλ€.<br>";
    break;

  case XMLHttpRequest.OPENED:
    currentState += "νμ¬ XMLHttpRequest κ°μ²΄μ μνλ OPENED μλλ€.<br>";
    break;

  case XMLHttpRequest.HEADERS_RECIEVED:
    currentState +=
      "νμ¬ XMLHttpRequest κ°μ²΄μ μνλ HEADERS_RECEIVED μλλ€.<br>";
    break;

  case XMLHttpRequest.LOADING:
    currentState += "νμ¬ XMLHttpRequest κ°μ²΄μ μνλ LOADING μλλ€.<br>";
    break;

  case XMLHttpRequest.DONE:
    currentState += "νμ¬ XMLHttpRequest κ°μ²΄μ μνλ DONE μλλ€.<br>";
    break;
}
```

<br />

- .responseText : μμ²­μ λν μλ΅μ `νμ€νΈ`λ‘ λ°νν©λλ€.
- .responseXML : μ°κ²°μ λν μλ΅μ `XML DOM`μΌλ‘ λ³νν©λλ€. XML λ¬Έμμ΄μ΄ μλλΌ XML DOMμΌλ‘ λ°ννλ€λ κ²μ μΌλν΄ λμΈμ.
- .status : `HTTP μν μ½λ`λ₯Ό `μ«μ`λ‘ λ°νν©λλ€. μλ₯Ό λ€λ©΄ OKμ λν΄μ 200μ, νμ΄μ§λ₯Ό μ°Ύμμ μμμ λλ 404λ₯Ό λ°νν©λλ€.
- .statusText : `HTTP μν μ½λ`μ λν `λ¬Έμμ΄`μ λ°νν©λλ€. μλ₯Ό λ€λ©΄ "OK", "Not Found" λ±μ΄ λ μ μμ΅λλ€.

<br />

## π¨π»βπ» Fetch

- μλ°μ€ν¬λ¦½νΈλ₯Ό μ¬μ©νμ¬ `Ajax λΉλκΈ° ν΅μ `μ μν΄ λ³λμ `λΌμ΄λΈλ¬λ¦¬`λ₯Ό λ§μ΄ μ¬μ©νκ³  μμ΅λλ€. μλ₯Όλ€λ©΄ jQueryμ `ajax()`, μλλ©΄ `axios` λ±μ Ajax κ΅¬νμ μν λͺ©μ μΌλ‘ μΆκ°ν΄ μ¬μ©ν΄μμ΅λλ€.
- μλνλ©΄ μμ μλ°μ€ν¬λ¦½νΈλ λΉλκΈ° ν΅μ μ΄ μ΄λ ΅κ³  λΉν¨μ¨μ μ΄κΈ° λλ¬Έμ΄λ€. νΉν XMLHttpRequestλ μνλ κΈ°λ₯μ κ΅¬ννκΈ° μν΄μλ λλ¬΄ λ³΅μ‘νκ³  `Promise`κ°μ²΄λ₯Ό μ¬μ©νλ κ²λ μ΄λ ΅κΈ° λλ¬Έμ΄λ€.
- μ΄ν, `fecth API`κ° ES6νμ€μΌλ‘ λ±μ₯νλ©΄μ `fetch` μ¬μ©μ΄ μΌλ°μ μ΄κ² λμλ€.
- `fetch`λ ES6μ λΉλκΈ° ν΅μ  λ°©λ²μΌλ‘, μμ²΄μ μΌλ‘ `Promise`κ°μ²΄λ₯Ό λ°ννκΈ°μ `Promise`μ ν¨κ» μ¬μ©νκΈ°λ νΈλ¦¬νλ€.

<br />

## π¨π»βπ» Fetch(Promise κΈ°λ°)μ¬μ©λ²

### π GET

```js
fetch("https://jsonplaceholder.typicode.com/posts/1").then((response) =>
  console.log(response)
);
```

- `fetch()`λ λν΄νΈλ‘ GET λ°©μμΌλ‘ μλνκ³  GET λ°©μμ μμ²­ μ λ¬Έμ λ°μ§ μκΈ° λλ¬Έμ μ΅μ μΈμκ° νμκ° μμ΅λλ€.
- μΆλ ₯ κ²°κ³Όλ λ€μκ³Ό κ°λ€.

```
  Response {status: 200, ok: true, redirected: false, type: "cors", url: "https://jsonplaceholder.typicode.com/posts/1", β¦}
```

- λλΆλΆμ `REST API`λ€μ `JSON` ννμ λ°μ΄ν°λ₯Ό μλ΅νκΈ° λλ¬Έμ, `μλ΅(response) κ°μ²΄`λ `json()` λ©μλλ₯Ό μ κ³΅νλ€.

<br />

```js
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((response) => response.json())
  .then((data) => console.log(data));
```

- `json()`λ₯Ό νΈμΆνλ©΄, `μλ΅(response) κ°μ²΄`λ‘ λΆν° JSON ν¬λ©§μ μλ΅ μ λ¬Έμ μλ°μ€ν¬λ¦½νΈ κ°μ²΄λ‘ λ³ννμ¬ μ»μ μ μμ΅λλ€.

```js
  {
    "userId": 1,
    "id": 1,
    "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
    "body": "quia et suscipitβ΅suscipit recusandae consequuntur β¦strum rerum est autem sunt rem eveniet architecto"
  }
```

<br />

### π POST

- `μκ²© API`μμ κ΄λ¦¬νκ³  μλ λ°μ΄ν°λ₯Ό μμ±ν΄μΌ νλ€λ©΄ `μμ²­ μ λ¬Έ`μ ν¬ν¨ν  μ μλ `POST λ°©μ`μ HTTP ν΅μ μ΄ νμνλ€.

```js
let body = {
  title: "Test",
  body: "I am testing!",
  userId: 1,
};

fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify(body),
}).then((response) => console.log(response));
```

- method μ΅μμ POSTλ‘ μ§μ ν΄μ£Όκ³ 
- headers μ΅μμ ν΅ν΄ JSON ν¬λ©§μ μ¬μ©νλ€κ³  μλ €μ€λ€.
- μμ²­ μ λ¬Έμ JSON ν¬λ©§μΌλ‘ `μ§λ ¬ν(JSON.stringify(body))`νμ¬ κ°μ₯ μ€μν body μ΅μμ μ€μ ν΄μ€λλ€.
- `JSON.stringify()` λ©μλλ JavaScript κ°μ΄λ κ°μ²΄λ₯Ό `JSON λ¬Έμμ΄`λ‘ `λ³ν`ν©λλ€.

```
  Response {type: "cors", url: "https://jsonplaceholder.typicode.com/posts", redirected: false, status: 201, ok: true, β¦}
```

<br />

```js
let body = {
  title: "Test",
  body: "I am testing!",
  userId: 1,
};

fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify(body),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

- λ§μ°¬κ°μ§ λ°©λ²μΌλ‘ μλ΅ κ°μ²΄μ `json() λ©μλ`λ₯Ό νΈμΆνλ©΄ μλ΅ μ λ¬Έμ `κ°μ²΄ νν`λ‘ μ»μ μ μμ΅λλ€.

```js
  {
    title: "Test",
    body: "I am testing!",
    userId: 1,
    id: 101
  }
```

<br />

### π PUT

```js
let body = {
  title: "Edit",
  body: "I am Edit Testing!",
  userId: 2,
};

fetch("https://jsonplaceholder.typicode.com/posts/1", {
  method: "PUT",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify(body),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

- `PUT`μ `method`μ μ΅μμ μ μΈνκ³  `POST`μ κ±°μ μ μ¬νλ€.

<br />

### π DELETE

```js
fetch("https://jsonplaceholder.typicode.com/posts/1", {
  method: "DELETE",
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

- `DELETE` λ°©μμμλ λ³΄λΌ λ°μ΄ν°κ° μκΈ° λλ¬Έμ, `headersμ body μ΅μμ΄ νμκ° μλ€.`

<br />

## μ°Έκ³ 

https://babtingdev.tistory.com/45
https://www.daleseo.com/js-window-fetch/
https://velog.io/@khw970421/Fetch-%EC%82%AC%EC%9A%A9%EB%B2%95
https://uhou.tistory.com/102
https://meetup.toast.com/posts/92
