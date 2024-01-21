- 참고

  - Typescript 투어일 뿐 

  - 코드를 보고 기억할 필요는 없음 

  - 이해가 제일 중요 => 프로젝트 해보자 

- readonly 속성을 추가할 수도 있음 

    - 요소들을 읽기 전용으로 만들 수 있어

```typescript
type Player = {
  readonly name: Name
  age?: Age
}

nico.name = 'las' // 에러 발생

/////////////

const numbers: readonly number[] = [1,2,3,4]
numbers.push(1) // readonly라서
const names: readonly string[] = ["1", "2"]
names.push() // => 불변성을 가질 수 있음 
```
- 아직 Javascript에서는 이 코드를 바꿀 수 있음

  - Typescript에서는 방지 가능 

- Tuple : Array를 생성할 수 있게 함 

  - 특정 위치에 특정 타입이 있어야 함 

```typescript
const player: readonly [string, number, boolean] = ["nico", 12, false]; // readonly도 추가 가능 
player[0] = 1 // 허용되지 않음 
```

- 이러한 보호장치를 가지는 것은 좋음 

- 코드를 저장하고 실제 프로덕션에서 문제 발생하는 것보다 나음 

```typescript 
let a : undefined = undefined;
let b : number = number;
```

- any

    - TS로부터 빠져나오고 싶을 때, 사용하는 타입 

    - 말 그대로 아무 타입도 될 수 있음 

    - any 사용을 막기 위해 추가할 수 있는 몇 가지 규칙이 존재 

    - TS를 비활성화시킴 









