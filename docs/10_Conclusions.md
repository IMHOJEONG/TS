- 제네릭을 실제로 어떻게 다루는가 

- 사용 사례는 정말로 중요함 

- 다른 패키지, 다른 라이브러리 => 제네릭을 사용해 생성됨 

- 제네릭이 유용한 경우가 많음 

    - nextjs, nestjs 등 

```typescript
function superPrint<V>(a: V[]) {
    return a[0]
}

const a = superPrint([1, 2, 3, 4]) // 알아서 잘 찾음 
const a1 = superPrint<boolean>([1, 2, 3, 4]) // 에러
```

- 항상 타입스크립트가 스스로 타입을 유추하도록 하는 것이 좋음 

- 제네릭을 사용해 타입을 생성할 수도 있고, 어떤 경우는 타입을 확장할 수 있음 / 코드를 저장하기도 함 

```typescript
type Player<E> = {
    name: string 
    extraInfo: E 
}

type NicoExtra = {
    favFood: string
}


type NicoPlayer = Player<NicoExtra>

const nico: NicoPlayer = {
    name: "nico",
    extraInfo: {
        favFood: 'test'
    }
}

const lynn: Player<null> = {
    name: "lynn",
    extraInfo: null
}
```

- 커스텀 타입도 사용 가능  

- 제네릭은 함수에서만 쓰이는 게 아님 

- type A = Array<Number> : 정말 자주 보는 표현 

- 제네릭은 어디에서나 쓰일 수 있음 

- useState에서도 제네릭을 함께 쓸수가 있어 

    - useState<number>()