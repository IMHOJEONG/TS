### Typescript 독특한 타입 

- 오직 TS에서만 존재, Type Checker랑 소통이 잘 됨 

- void 

- never 

- unknown 

  - API로 응답 받는데, 타입 모르면, unknown을 사용할 수 있어 

```typescript
let a : unknown; 

let b = a + 1 // 에러 

if(typeof a === 'number') {
  let b = a + 1; // 이 범위 안에서는 a가 number 
}
if(typeof a === 'string') {
  let b = a.toUpperCase();
}
```

- void : 아무것도 return하지 않는 함수를 대상으로 사용해 

```javascript
function hello():  {
  console.log('x')
}
```

- 보통 void를 따로 지정해줄 필요는 없어 

- TS는 이 함수가 아무것도 return하지 않는다는 것을 자동으로 인식해

- void 타입에는 toUpperCase가 없음 

### never

- never는 함수가 절대 return하지 않을 때 발생해 

- 예를 들어, 함수에서 exception(예외)이 발생할 때! 

```typescript
function hello(): never {
    return "X" // 오류 생김 
}

// return 하지 않고, 오류를 발생시킴 
function hello(): never {
    throw new Error("xxx")  
}
```

- 또한, never는 타입이 두가지일 수도 있는 상황에 발생할 수 있음 

```typescript
function hello(name: string | number) {
  
  if(typeof name === "string") {
    name
  } else if (typeof name === "number") {
    name
  } else {
    name // 타입은 never
  }

}
```