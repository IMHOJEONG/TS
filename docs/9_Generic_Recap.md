### Generic Recap

```typescript
type SuperPrint = <T>(arr: T[]) => T

const superPrint: SuperPrint = (arr) => arr[0]

const a = superPrint([1,2,3,4])
const b = superPrint([true, false, true])
const c = superPrint(["a", "b", "c"])
const d = superPrint([1,"2",3,4])
```

- 타입스크립트는 나의 코드를 보고 알아챔 

- call signature를 요구하는 데로 생성함 

- (arr: any[]) => any 를 쓰지 않는 이유 

    - 이 방법은 우리를 지켜주지 않음 

    - 즉, 제네릭을 사용하는 이유가 됨 

- 제네릭을 사용할 때, 타입스크립트가 이 함수의 call signature를 만들어줌 

- 작성해야 할 call signature를 생각해야 할 때...

- 제네릭을 추가하려면..

```typescript
type SuperPrint = <T, M>(arr: T[], b: M) => T

const superPrint: SuperPrint = (arr) => arr[0]

const a = superPrint([1,2,3,4], "X")
const b = superPrint([true, false, true],1)
const c = superPrint(["a", "b", "c"])
const d = superPrint([1,"2",3,4])
```

- 타입스크립트는 제네릭을 처음 인식했을 때와 제네릭의 순서를 기반으로 제네릭의 타입을 알게 됨 

- any와 똑같은 과정이 아닌, 우리가 요청한 call signature를 만들어주는 것 

