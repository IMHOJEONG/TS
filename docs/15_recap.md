### 타입과 인터페이스의 차이점 정리 

- 인터페이스는 네가 원하는 메소드와 프로퍼티를 클래스가 가지도록 강제할 수 있게 해줌 

- 인터페이스는 자바스크립트로 컴파일되지 않아 

- 추상 클래스와 비슷한 보호를 제공하지만, 인터페이스는 자바스크립트 파일에서 보이지 않지 

    - 추상 클래스를 쓰면 이건 자바스크립트에서는 일반적인 클래스로 바뀜 

    - 파일 크기가 커지고, 추가 클래스가 만들어진다는 뜻 

- 만약 추상 클래스를 다른 클래스들이 특정 모양을 따르도록 하기 위한 용도로 쓴다면 

    - 인터페이스를 사용하는 게 좋음 

---

1. 타입을 쓰고 싶다면 type 키워드 

```typescript
type Player = string | '1'

type Player = {
    name: string
}

const player: Player = {
    name: "nico"
}

/////

interface PlayerB {
    name: string
}

const player: PlayerB = {
    name: "nico"
}

```

- 타입, 인터페이스는 목표는 동일하지만, 뭔가 할 수 있도록 허용 범위가 다름 

2. 타입을 상속하려면, 또 다른 타입 하나를 만들어서 알려주어야 함 

```typescript
type PlayerA = {
    name: string
}

type PlayerAA = PlayerA & {
    lastName: string 
}

const playerAA: PlayerAA = {

}
```

- 인터페이스를 상속하는 방법은 객체지향 프로그래밍의 컨셉과 매우 유사함 

```typescript
interface PlayerB = {
    name: string
}

interface PlayerBB extends PlayerB {
    lastName: string    
}

const PlayerBB: PlayerBB = {

}
```

- 타입과 인터페이스는 위처럼 결과는 같지만, 과정이 다름 

- 나중에 프로퍼티를 타입에 추가하려면?

    - 이전과 같은 방식으론, 타입이 이미 정의되어서 중복될 수 있음 (그 때마다 타입을 새로 만들 수 없어)

- 하지만 인터페이스는 같은 이름으로 바로 추가할 수 있음 

```typescript
interface PlayerBB extends PlayerB {
    lastName: string    
}

interface PlayerBB  {
    health: string    
}

const PlayerBB: PlayerBB = {

}
```

- 원한다면, 인터페이스와 타입 모두 추상 클래스를 대체해서 쓸 수 있음 

```typescript
type PlayerA = {
    name: string
}

interface PlayerBB  {
    health: string    
}

class User implements PlayerBB 
// class User implements PlayerA도 가능 
{
    constructor(
        public name: string,
        public health: string
    ) {}
}
```

- 타입스크립트 커뮤니티에서는 클래스나 오브젝트의 모양을 정의하고 싶으면, 인터페이스를 사용하고, 다른 모든 경우에서는 타입을 쓰라고 하고 있음 

    - 인터페이스를 상속시키는 방법이 직관적이어서!

- 타입 alias나, 특정 값으로 타입을 제한하는 경우와 같이 다른 경우에는 타입을 쓸 수 있음 

- https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces

    - 타입은 새로 프로퍼티를 추가해서 타입 정의가 가능하지만, 인터페이스는 항상 상속이 가능 

- 클래스는 인터페이스를 상속할 수도 있고, 타입을 상속할 수도 있어