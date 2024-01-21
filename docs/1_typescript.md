- 코드를 실행하고 나서야, 알게 되는 에러 

    - 런타임 에러 : 실제 유저가 알게됨 

- 이상적으로, 코드를 실행하기 전에 에러를 알고 싶어서 

---

- 타입스크립트의 경우에는 작성한 코드가 자바스크립트가 됨 

- 변환하는 이유는, 브라우저는 자바스크립트를 이해하기 때문 

   - Node.js는 타입스크립트, 자바스크립트 둘 다 이해할 수 있음 

- 타입스크립트가 그저 코드를 자바스크립트로 변환해줄 뿐이라면, 우릴 어떻게 보호해줄까? 

- 컴파일은 그저 작성한 타입스크립트 코드를 일반적인 자바스크립트로 바꾸어줌 

- 타입스크립트가 제공하는 보호장치는

    - 타입스크립트 코드가 자바스크립트로 변환되기 전에 발생 

- 즉, 타입스크립트가 먼저 우리의 코드를 확인한 다음에 

    - 변환된 자바스크립트 안에서 바보같은 실수가 일어나지 않게 확인을 해줘 

- 일단 타입스크립트 코드를 작성해서, 그 코드를 컴파일하면, 보호장치 없는 정신 나간 자바스크립트 코드가 됨 

- 하지만. 타입스크립트 코드에 에러가 있으면, 그 코드는 자바스크립트로 컴파일되지 않아 

    - 타입스크립트가 에러가 발생할 것 같은 코드를 감지하면 

        - 자바스크립트로 아예 컴파일되지 않아 

- 이런 보호장치가 유저가 코드를 실행하는 런타임에 발생하는 게 아님 

    - 유저는 그냥 일반 JS 코드를 사용할 뿐 

---

- 만약 타입스크립트가 성공적으로 컴파일되어 자바스크립트 코드를 주면 

    - 타입스크립트 코드도 제대로 작성된 거고, 데이터 타입에도 문제가 없었단 것 

    - 자바스크립트 코드에 버그가 전혀 없단 뜻 

```
const nico = {
    nickname: 'nick'
}

nico.hello()

Errors in code
Property 'hello' does not exist on type '{ nickname: string; }'.

[1,2,3,4] + false

Operator '+' cannot be applied to types 'number[]' and 'boolean'.

function divide(a, b) {
    return a / b
}

divide('hello')

Parameter 'a' implicitly has an 'any' type.
Parameter 'b' implicitly has an 'any' type.
Expected 2 arguments, but got 1.

const player = {
    age: 12
}

player.age = false

Type 'boolean' is not assignable to type 'number'.

```

- 위와 같이, 에러를 알려주고 공지해줍니다 

- 타입 추론 때문에 이렇게 에러를 알 수 있음 


