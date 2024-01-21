### Polymorphism

- 다형성 

- 타입스크립트가 어떻게 다형성을 주는가? 

   - generic 

- poly : manyu, several, much 

  - morpho : form, structure

- 여러가지 다른 구조들이라는 의미 

- 함수는 기본적으로 여러가지 모양, 형태를 가짐 

- 제네릭이 어떻게 좀 더 도움을 줄 수 있는가?

```typescript

type SuperPrint = {
  (arr: number[]): void 
  (arr: boolean[]): void
  (arr: string[]): void
}


const superPrint: SuperPrint = (arr) => {
  arr.forEach(i => console.log(i))
}
```

- 문제가 존재: number, boolean 등 다양한 타입으로 받을 수도 있는데?

- superPrint(['a','b'])는 동작하지 않아 => 추가할 수 있지만, 더 좋은 방법이 있음 

- concrete type : 우리가 전부터 봐왔던 타입을 말함 

    - generic => 타입의 placeholder같은 것 

- concrete type을 사용하는 것 대신 generic을 쓸 수 있음 

- type SuperPrint = {
  (arr: number[]): void 
  (arr: boolean[]): void
  (arr: string[]): void
}

=> 3개의 call signature가 존재 

- 만약? superPrint([1,2,true,false])를 준다면? 

     - 제대로 동작 안함 : 이것들에 대한 call signature가 없기 때문 

- 하지만, 나는 어떤 타입이라도 동작하게 하고 싶은데? 

- (arr: (number|boolean)[]): void는?

    - 이러한 방법을 별로 좋아하지 않음, 모든 가능성을 다 조합해서 만들어야 하기 때문 

---

=> 대신 Generic을 사용해야 함 

- 타입스크립트가 그 타입을 유추해야 하는 부분 

- call signature를 작성하는데, concrete type을 알 수 없을 때 

  - generic을 사용함 

1. 타입스크립트에 generic을 사용한다고 알려줘야 해 

```typescript
  -  type SuperPrint = {
  <TypePlaceholder>(arr: TypePlaceholder[]): void 
}
```

- superPrint([1,2,3,4]) : 이 명령어 라인에서 superPrint가 number 타입의 배열로 동작하는 것을 알게 됨 

    - 타입스크립트는 [1,2,3,4] 값을 보고 타입을 유추

    - 기본적으로 그 유추한 타입으로 call signature를 보여줌 

- 우리가 하지 않았는데도, 타입을 만들어줌 

- generic : 함수에 타입을 입력하는 것을 허용함

- 타입스크립트에 타입을 유추하도록 알려주는 방법 

```typescript
type SuperPrint = {
    <TypePlaceholder>(arr: TypePlaceholder[]): TypePlaceholder
}

const superPrint: SuperPrint = (arr) => arr[0]

const a = superPrint([1,2,3,4])
const b = superPrint([true, false, true])
const c = superPrint(["a", "b", "c"])
const d = superPrint([1,"2",3,4])
```
