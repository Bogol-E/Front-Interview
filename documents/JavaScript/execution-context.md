# π» Execution Context

<br />

## π¨π»βπ» μ€ν μ»¨νμ€νΈ(Execution Context)

- μ€ν μ»¨νμ€νΈλ `μ½λμ μ€ν νκ²½`μ λν μ¬λ¬κ°μ§ μ λ³΄(Scope, Hoisting, this, function, closure λ±)λ₯Ό λ΄κ³ μλ κ°λμ΄λ€.
- κ°λ¨ν λ§νλ©΄ `μλ°μ€ν¬λ¦½νΈ μμ§`μ μν΄ λ§λ€μ΄μ§κ³  μ¬μ©λλ μ½λ μ λ³΄λ₯Ό λ΄μ `κ°μ²΄μ μ§ν©`μ΄λΌκ³  ν  μ μλ€.
- μ€ν μ»¨νμ€νΈλ₯Ό λ°λ‘ μ΄ν΄νμ§ λͺ»νλ©΄ μ½λ λν΄κ° μ΄λ €μμ§λ©° λλ²κΉλ λ§€μ° κ³€λν΄ μ§ κ²μ΄λ€.

### π μ’λ₯

- μλ°μ€ν¬λ¦½νΈμμ μ€ν κ°λ₯ν μ½λλ 3κ°μ§λ‘ μ΄λ£¨μ΄μ Έ μλ€.
- μ μ­ μ½λ, ν¨μ μ½λκ° μΌλ°μ μΌλ‘ μ€ν κ°λ₯ν μ½λμ΄λ€.

<br />

```
1. μ μ­ μ½λ: μ μ­ μμ­μ μ‘΄μ¬νλ μ½λ
2. ν¨μ μ½λ: ν¨μ λ΄μ μ‘΄μ¬νλ μ½λ
3. Eval μ½λ: eval()λ‘ μ€νλλ μ½λ
```

<br />

- μλ°μ€ν¬λ¦½νΈ μμ§μ μ½λλ₯Ό μ€ννκΈ° μνμ¬ μ€νμ νμν μ¬λ¬κ°μ§ μ λ³΄λ₯Ό μκ³  μμ΄μΌ νλ€.
- μ΄λ¬ν `μ€νμ νμν μ λ³΄`λ€μ νμννκ³  κ΅¬λΆνκΈ° μν΄ μλ°μ€ν¬λ¦½νΈ μμ§μ μ€ν μ»¨νμ€νΈλ₯Ό `κ°μ²΄`μ ννλ‘ κ΄λ¦¬νλ€.

<br />

```
1. λ³μ: μ μ­ λ³μ, μ§μ­ λ³μ, λ§€κ° λ³μ, κ°μ²΄μ νλ‘νΌν°
2. ν¨μ μ μΈ
3. λ³μμ μ ν¨λ²μ (Scope)
4. this
```

<br />

- 1. μλ°μ€ν¬λ¦½νΈ μμ§μ΄ νμΌμ μ€ννκΈ° μ μ `κΈλ‘λ² μ€ν μ»¨νμ€νΈ(Global Execution Context, GEC)`κ° μμ±λλ€.
- 2. κ·Έλ¦¬κ³  ν¨μλ₯Ό νΈμΆν  λλ§λ€ `ν¨μ μ€ν μ»¨νμ€νΈ(Function Execution Context, FEC)`κ° μμ±λλ€.
- μ΄λ μ£Όμν  μ μ, κΈλ‘λ²μ κ²½μ° `μ€ν μ΄μ `μ μμ±λμ§λ§, ν¨μμ κ²½μ° `νΈμΆν  λ` μμ±λλ€λ κ²μ΄λ€.

<br />

## π¨π»βπ» μ€ν μ»¨νμ€νΈ μ€ν(Exectuion Context Stack)

- μ€ν μ»¨νμ€νΈκ° μμ±λλ©΄ νν `μ½ μ€ν(Call Stack)`μ΄λΌκ³  λΆλ¦¬λ `μ€ν μ»¨νμ€νΈ μ€ν`μ μμ΄κ² λλ€.
- `GEC`λ μ½λλ₯Ό μ€ννκΈ° μ μ μμ΄κ³ , λͺ¨λ  μ½λλ₯Ό μ€ννλ©΄ μ κ±°λλ€.
- `FEC`λ ν¨μλ₯Ό νΈμΆν  λ μμ΄κ³  νΈμΆμ΄ λλλ©΄ μ κ±°λλ€.

```js
var x = "xxx";

function foo() {
  var y = "yyy";

  function bar() {
    var z = "zzz";
    console.log(x + y + z);
  }
  bar();
}
foo();
```

- μ μ½λλ₯Ό μ€ννλ©΄ μλμ κ°μ΄ μ€ν μ»¨νμ€νΈ μ€νμ΄ μμ±λκ³  μλ©Ένλ€.
- νμ¬ μ€ν μ€μΈ μ»¨νμ€νΈμμ ν΄λΉ μ»¨νμ€νΈμ κ΄λ ¨ μλ μ½λ(ex. λ€λ₯Έ ν¨μ)λ€μ μ€νλλ©΄ μλ‘μ΄ μ»¨νμ€νΈκ° μμ± λλ€.
- μ΄ μ»¨νμ€νΈλ μ€νμ μμ΄κ² λκ³  μ»¨νΈλ‘€(μ μ΄κΆ)μ΄ μ΄λνλ€.

![μ€νμ»¨νμ€νΈμ€ν](https://user-images.githubusercontent.com/64779472/120208197-25b5f080-c268-11eb-9e5a-eb3da3b96eed.PNG)

<br />

## π¨π»βπ» μ€ν μ»¨νμ€νΈ κ΅¬μ± μμ

- μ€ν μ»¨νμ€νΈλ `Lexical Environment`, `Variable Environment`, `this λ°μΈλ©` 3κ°μ κ΅¬μ±μμλ₯Ό κ°λλ€.

<br />

### π Lexical Environment

- Lexical Environmentλ `λ³μ λ° ν¨μ λ±μ μλ³μ(Identifier) λ° μΈλΆ μ°Έμ‘°`μ κ΄ν μ λ³΄λ₯Ό κ°κ³  μλ μ»΄ν¬λνΈμ΄λ€. μ΄ μ»΄ν¬λνΈλ `Environment Record`, `outer μ°Έμ‘°` 2κ°μ κ΅¬μ±μμλ₯Ό κ°λλ€.
- Environment Recordκ° μλ³μμ κ΄ν μ λ³΄λ₯Ό κ°κ³  μμΌλ©°, outer μ°Έμ‘°λ μΈλΆ Lexical Environmentλ₯Ό μ°Έμ‘°νλ ν¬μΈν°μΈλ€.
- μ’ λ νμ΄μ°μλ©΄ Environment Recordλ `μ΅μ΄μ λ³μ`, `Arguments`, `ν¨μ μ μΈ`λ€μ μ μ₯νλ€.
- outerλ `λΆλͺ¨ Environment(reference)`λ₯Ό μ μ₯νλ€.
- μ€ν μ»¨νμ€νΈλ μμ± λ  λ, Lexical Environmentμ Variable Environmentμ κ΅¬μ± μμλ λμΌν κ°μ κ°μ§λ, μ»¨νμ€νΈ λ΄μμ μ½λλ₯Ό μ€ννλ λμ Variable Environmentμ λ¬λ¦¬ Lexical Environmentμ κ΅¬μ±μμμ κ°μ λ³κ²½λ  μ μλ€.

```js
var x = 10;

function foo() {
  var y = 20;
  console.log(x);
}
```

- μμ κ°μ μ½λκ° μμ λλ μλμ κ°μ΄ Lexical Environmentκ° νμ±λλ€.

<br />

```js
  globalEnvironment = {
    environmentRecord = { x: 10 },
    outer: null
  }

  fooEnvironment = {
    environmentRecord = { y: 20 },
    outer: globalEnvironment
  }
```

- λ°λΌμ, `foo()` μμ `x`λ₯Ό μ°Έμ‘°ν  λλ fooEnvironmentμ Environment Recordλ₯Ό μ°Ύμλ³΄κ³ , μκΈ° λλ¬Έμ outer μ°Έμ‘°λ₯Ό μ¬μ©νμ¬ μΈλΆμ Lexical Environmentμ μν΄ μλ Environment Recordλ₯Ό μ°Ύμλ³΄λ λ°©μμ΄λ€.

<br />

### π Variable Environment

- Variable Environmentλ Lexical Environmentμ λμΌν μ±κ²©μ κ°μ§λ§ `var`λ‘ μ μΈλ λ³μλ§ μ μ₯νλ€λ μ μμ λ€λ₯΄λ€.
- μ¦, Lexical Environmentλ `var`λ₯Ό μ μΈν, `let`, `ν¨μ μ μΈλ¬Έ`, `ν¨μ λ§€κ° λ³μ`λ€μ μ μ₯νλ€.
- μ½λμ μν΄ μλ‘μ΄ λ³μ/ν¨μκ° μΆκ°λλλΌλ μ λ κ°μ΄ λ³νμ§ μλλ€.
- [μ½λ μ°Έκ³ ](https://stackoverflow.com/questions/23948198/variable-environment-vs-lexical-environment/45788048#45788048)

<br />

### π this λ°μΈλ©

- thisμ λ°μΈλ©μ μ€ν μ»¨νμ€νΈκ° μμ±λ  λλ§λ€ this κ°μ²΄μ `μ΄λ»κ² λ°μΈλ©μ΄ λλμ§`λ₯Ό λνλΈλ€. μ¦, μ€ν μ»¨νμ€νΈμ `this ν€μλμ λ°ν κ°`μ μ μ₯νλ€.
- thisμ ν€μλλ `νμ¬ μ»¨νμ€νΈκ° μ°Έμ‘°νκ³  μλ κ°μ²΄`λ₯Ό κ°λ¦¬ν€λ©°, ν¨μ νΈμΆ ν¨ν΄μμν΄ κ²°μ  λλ€.
- ES6λΆν°λ thisμ λ°μΈλ©μ΄ Lexical Environment μμ μλ Environment Record μμμ μΌμ΄λλ€λ κ²μ κΈ°μ΅νμ.(κ·Έλ κ² μ€μνμ§λ μλ€.)
- GECμ κ²½μ°
  - Strict ModeλΌλ©΄ `undefined`λ‘ λ°μΈλ© λλ€.
  - Strict Modeκ° μλλΌλ©΄ κΈλ‘λ² κ°μ²΄λ‘ λ°μΈλ© λλ€.(λΈλΌμ°μ μμ  Window, λΈλμμ  Global)
- FECμ κ²½μ°
  - ν΄λΉ ν¨μκ° μ΄λ»κ² νΈμΆλμλμ§μ λ°λΌ λ°μΈλ© λλ€.

<br />

## π¨π»βπ» κ³Όμ 

- Execution Contextλ 2κ°μ§ κ³Όμ μ κ±°μΉλ€.
- Creation Phase(μμ± λ¨κ³), Execution Phase(μ€ν λ¨κ³)

### π μμ± λ¨κ³

- μμ± λ¨κ³λ λ€μ 3λ¨κ³λ‘ μ΄λ£¨μ΄μ§λ€.
- Lexical Environment μμ±, Variable Environment μμ±, this λ°μΈλ©
- μ£Όμν  μ μ κ°μ΄ λ³μμ λ§€νλμ§ μλλ€λ κ²μ΄λ€. `var`μ κ²½μ° `undefined`λ‘ μ΄κΈ°νλκ³ , `let`μ΄λ `const`λ μλ¬΄ κ°λ κ°μ§μ§ μλλ€.

<br />

### π μ€ν λ¨κ³

- μ½λλ₯Ό μ€ννλ©΄μ λ³μμ κ°μ λ§€νμν¨λ€. μμλ₯Ό λ³΄μ

```js
var a = 3;
let b = 4;

function func(num) {
  var t = 9;
  console.log(a + b + num + t);
}

var r = func(4);
```

<br />

- GECμ μμ± λ¨κ³, μ¬κΈ°μ μμ±μ΄ λ  λ μ€ν μ»¨νμ€νΈ μ€νμ μμΈλ€.

```js
  GEC {
    ThisBinding: window,
    LexicalEnvironment: {
      EnvironmentRecord: {
        b: <uninitialized>,
        func: func(){...}
      },
      outer: null
    },
    VariableEnvironment: {
      EnvironmentRecord: {
        a: undefined,
        r: undefined
      },
      outer: null
    }
  }
```

<br />

- GECμ μ€ν λ¨κ³

```js
  GEC {
    ThisBinding: window,
    LexicalEnvironment: {
      EnvironmentRecord: {
        b: 4,
        func: func(){...}
      },
      outer: null
    },
    VariableEnvironment: {
      EnvironmentRecord: {
        a: 3,
        r: undefined
      },
      outer: null
    }
  }
```

- μ΄νμ `func()`μ νΈμΆνκ³  FECλ₯Ό μμ±νλ€.

<br />

- FECμ μμ± λ¨κ³

```js
  FEC {
    ThisBinding: window,
    LexicalEnvironment: {
      EnvironmentRecord: {
        arguments: { num: 4, length: 1 },
      },
      outer: GECμ LexicalEnvironment
    },
    VariableEnvironment: {
      EnvironmentRecord: {
        t: undefined
      },
      outer: GECμ LexicalEnvironment
    }
  }
```

<br />

- FECμ μ€ν λ¨κ³

```js
  FEC {
    ThisBinding: window,
    LexicalEnvironment: {
      EnvironmentRecord: {
        arguments: { num: 4, length: 1 },
      },
      outer: GECμ LexicalEnvironment
    },
    VariableEnvironment: {
      EnvironmentRecord: {
        t: 9
      },
      outer: GECμ LexicalEnvironment
    }
  }
```

- FECκ° μ€νμμ μ κ±° λκ³  GECμ `r`μ΄ 20μΌλ‘ μ΄κΈ°ν λλ€.

<br />

```js
  GEC {
    ThisBinding: window,
    LexicalEnvironment: {
      EnvironmentRecord: {
        b: 4,
        func: func(){...}
      },
      outer μ°Έμ‘°: null
    },
    VariableEnvironment: {
      EnvironmentRecord: {
        a: 3,
        r: 20
      },
      outer μ°Έμ‘°: null
    }
  }
```

- λͺ¨λ  μ½λλ₯Ό μ€ννκ³  GECκ° μ€νμμ μ κ±°λ λ€ νλ‘κ·Έλ¨μ΄ μ’λ£λλ€.
- [μ½λ μ°Έκ³ ](https://miro.medium.com/max/1100/1*SBP65hdVDW5j0LuVryTiXw.gif)λ₯Ό μ°Έκ³ νλ©΄ λ νμ€ν μ΄ν΄ν  μ μλ€.

<br />

## μ°Έκ³ 

https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/execution-context.md
https://minjung-jeon.github.io/Execution-Context/
https://velog.io/@imacoolgirlyo/JS-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%9D%98-Hoisting-The-Execution-Context-%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85-%EC%8B%A4%ED%96%89-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8-6bjsmmlmgy
https://poiemaweb.com/js-execution-context
