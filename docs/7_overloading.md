### Overloading (function overloading, method overloading)

- 실제로 많은 오버로딩된 함수를 직접 작성하지 않을 건데..

- 대부분의 시간을 다른 사람들이 만든 외부 라이브러리를 사용할텐데 

- 이런 패키지나 라이브러리들은 오버로딩을 엄청 많이 사용해 

```
type Add = (a:number, b:number) => number
```

- call signature 

  - 타입스크립트에게 이 함수가 어떻게 호출되는지 설명해주는 부분 

  - 파라미터, 리턴타입 

```
type Add = {
  (a: number, b: number): number 
}
```

- 오버로딩은 함수가 여러 개의 call signatures를 가지고 있을 때 발생시킴 

    - 서로 다른 여러 개 Call Signature를 가졌을 때입니다 

```
type Add = {
  (a: number, b: number): number
  (a: number, b: string): number
}

const add: Add = (a,b) => a+b
```

- 위의 두 가지 모양으로 부를 수도 있어 => TS는 이게 잘못되었다는 걸 알게 됨 

- b가 string도 될 수 있고 number도 될 수 있어서 string과 number는 더할 수 없다 


```javascript
// 매우 나쁜 예시
type Add = {
  (a: number, b: number): number
  (a: number, b: string): number
}

const add: Add = (a,b) => {
  if(typeof b === "string") return a;
  return a + b
}
```

- 매우 나쁜 예시 => 소수의 함수만 이런식으로 할 수 있음 

- 다시 말하면, 오버로딩은 여러 call signatures가 있는 함수일 뿐이야 

- 일상에서 개발을 할 때 볼 수 있는 오버로딩 

```typescript
// next.js

Router.push("/home") // home 페이지로 이동 
Router.push({
  path: "/home",
  state: 1
}) // 추가적으로 뭔가를 더 넣어서 같이 보낼 수도 있앙
```

- 위에 있는 코드를 어떻게 개선하는가? 

```typescript
// 매우 좋은 예시
Push라는 타입을 만들어주고, 

type Config = {
  path: string,
  state: object
}

type Push = {
  (path: string): void
  (config: Config): void
}
// 이런 config를 받고, 아무것도 리턴하지는 않아 
const push: Push = (config) => {
  if(typeof config === "string") console.log(config)

  else {
    console.log(config.path)
  }
}
```

- 위의 코드는 패키지나 라이브러리를 디자인할 때 많은 사람들이 사용해 

- 어쩔땐 이걸, 어쩔땐 저걸 보내줄 수도 있음 

    - 타입스크립트는 내부에서 그 타입을 체크하도록 해줘 

- 오버로딩에 대해 알아야 할 것 

  - 다른 여러 개의 argument를 가지고 있을 때 발생하는 효과 있음 

- 지금은 타입 객체가 다름 

```typescript
type Push = {
  (path: string): void
  (config: Config): void
}
```

- 하나의 call signature는 두 개의 파라미터를 가지고 있음 

- 다른 하나는 6개의 파라미터를 가질 수 있음

```typescript
type Push = {
  (a: number, b: number): number
  (a: number, b: number, c: number): number
}

const add: Add = (a,b,c?: number) => {
  return a + b;
}
```

- 타입스크립트가 행복하지 않은 이유는? 다른 개수의 파라미터를 가지기 때문 

- 다른 개수의 파라미터를 가지게 되면, 나머지 파라미터도 타입을 지정해줘야 해 

```
const add: Add = (a,b,c?: number) => {

  if(c) return a+b+c
  return a + b;
}

add(1, 2)
add(1, 2, 3)

```

