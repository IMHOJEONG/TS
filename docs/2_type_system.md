### Typescript : Type System 

- 변수가 number이고, 항상 명시해 주어야 함 

- 두 가지 접근 방식을 정의 

    1. 데이터와 변수의 타입을 명시적으로 정의할 수도 있음 

    2. 아니면, JS 처럼 변수를 생성만 하고 넘어가 

        - Typescript가 타입을 추론해준다는 장점 

let a = "hello";

- 이렇게 하는 것만으로, a의 타입을 추론해 줌 

a = "bye" // 문제없음 (a를 string => string)

a = 1 // 에러 (JS에서는 가능하지만, TS에는 아님-버그될 수 있음 )

- 보통 변수 생성하고 타입을 바꾸지 않아 

---

- let b : boolean = "hello" // 에러 (b는 boolean이어야 함)

  - 우리가 Type Checker와 소통하는 방법 

  - Type Checker가 타입을 확인해줌 

- 보통 let b = "ee" 하는 방식을 추천 

```typescript
let c : number[] = [1,2,3]
c.push("1") // 에러 => 바보 같은 실수에서 나오는 게 좋음 
```

- `TypeScript가 타입을 추론하지 못할 때, 명시적으로 적어주는 게 좋아`

- 보통 명시적 표현은 최소한으로 사용해주는 게 좋음 

- 모든 에러가 추론이 발생해서 찾을 수 있게 되는 것 


 