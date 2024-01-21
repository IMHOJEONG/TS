### TS에서의 함수 

- call signatures

- 다형성 

- 오버로딩 

- 제네릭 


#### call signatures

```typescript
function add(a: number, b: number) {
  return a + b
}

const add = (a: number, b: number) => a+ b
// const add: (a: number, b: number) => number
```

- 함수를 어떻게 호출하는지 알려줌 

```typescript
type Add = (a: number, b: number) => number;

const add:Add = (a, b) => a+b;
```

- 타입을 만들 수 있고, 함수가 어떻게 작동하는지 서술해둘 수 있음 

- 함수를 구현하기 전에 알 수 있고, 첫 번째로 네가 타입을 생각하도록 해줌 

- 먼저 함수의 타입을 설명하고, 그리고나서 코드를 구현하게 되지 

- type Add = (a: number, b: number) => number; ===> call signature이다.

- props => 함수를 보내게 되면, 타입스크립트한테 설명해줘야 해... / 어떻게 함수가 작동하는지 

1. 프로그램을 디자인하면서, 타입을 먼저 생각하고 코드를 구현할 수 있음 

2. const add:Add = (a, b) => a+b; => 여기에는 안 보여도 되는 것 


