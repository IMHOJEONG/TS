```typescript
class Word {
    constructor(
        public term: string, 
        public def: string
    ) {}
}

const kimchi = new Word("kimchi", "한국의 음식");


```

- 단어를 추가할 때, word를 보내면, 사용해야 하는데 

- 누군가 단어의 내용을 수정하게 하고 싶지는 않다면? 

- 어떻게 하면, public 이지만 더 이상 변경할 수 없도록 만들 수 있게 하려면?

    - 값을 보여주고는 싶지만 수정은 불가능하게 하고 싶은 것 

- public term: string =>         public readonly term: string로 만들어주면 됨 

kimchi.def = 'xxx' : 에러 발생함 


- def가 읽기 전용인 프로퍼티라서

- 주로 다른 누군가가 데이터를 덮어쓰는 것을 방지하기 위해서, private 이나 protected 프로퍼티를 사용하는데...

- 이 예제에서는 property들을 public으로 두고, 이걸 타입스크립트의 힘을 빌려 읽기 전용으로 만들면 => 타입스크립트는 저걸 수정하는 것으로부터 데이터를 보호함

- readonly는 자바스크립트에서는 보이지 않음 

#### static 

- 클래스의 static 메소드 같다고 생각하면 안 됨 

- js의 것 
```
class Dict {
    static hello() {
        return `hello`;
    }
}

Dict.hello()
```

### interface 

- 타입과 비슷하지만, 두 가지 부분에서 다른 점을 이해해야 함 

1. 타입스크립트에서 타입을 사용하는 것은 매우 유용 

```typescript
type Player = {
    nickname: string,
    healthBar: number 
}

const nico: Player = {
    nickname: "nico",
    healthBar: 10
}

// 이런식으로 타입스크립트의 보호 기능을 사용할 수 있어 
```

- 타입스크립트에게 오브젝트의 모양을 설명해줄 수 있어 

```typescript
type Food = string;

const kimchi: Food = "delicious"
```

- 타입은 굉장히 여러 방면으로 쓰일 수 있어 

- object의 모양을 알려줄 수 있고, 타입이 string이라고 알려줄 수 있음 

- type 키워드를 이용해 타입스크립트에서 만들고 싶은 무수히 많은 종류의 타입을 설명하면 됨 

- 타입을 지정된 옵션으로만 제한도 가능 

- 타입을 특정 값을 가지도록 하는 부분 

    - string 전체가 아니라, 특정 값들을 가짐, 엄청 유용한 기능 

```typescript
type Team = "red" | "blue" | "yellow"
type Health = 1 | 5 | 10
type Player = {
    team: Team
}

const nico: Player = {
    team: "pink" // error
}
```

#### 오브젝트의 모양을 설명하는 다른 방법인 인터페이스 

- 약간의 차이점은 있지만, 거의 비슷하다는 것을 알려주기 위함 

```typescript
type Team = "red" | "blue" | "yellow"
type Health = 1 | 5 | 10

interface Player {
    nickname: string,
    healthBar: Health 
    team: Team
}

const nico: Player = {
    team: "pink" // error
}
```

- 가장 먼저 이해해야 할 것 

    - 타입은 내가 원하는 모든 것이 될 수 있어 

- 인터페이스는 오직 한 가지의 특징만 있음 

    - 오브젝트의 모양을 특정해주기 위한 것 

    - 리액트를 이용해 작업을 할 때 많이 사용함 

- 타입스크립트에게 오브젝트의 모양을 알려주는 방법에는 두 가지가 존재 

    1. type을 쓰고 오브젝트의 모양을 써주는 방법이 있고 

    2. 다른 하나는 인터페이스 

- 하지만, 다른 점은 type 키워드는 interface 키워드에 비해 좀 더 활용할 수 있는 게 많다는 것 

- interface Hello = string 처럼은 할 수 없음 

- interface는 오로지 오브젝트의 모양을 타입스크립트에게 설명해주기 위해서만 사용되는 키워드 

```typescript
interface User {
    name: string 
}

interface Player extends User{
    name: string 
}

const nico: Player = {
    name: "nico"
}
```

- interface는 클래스와 닮아보임 

- 인터페이스는 타입스크립트에게 오브젝트의 모양을 설명해주기 위해 존재함 

- & : and를 의미함 

- 객체지향 프로그래밍처럼 보여서 인터페이스로 오브젝트의 모양을 설명하는 게 더 편하다고 하심 

---

- 인터페이스를 3번 각각 만들면, 타입스크립트가 알아서 하나로 합쳐준다?

```typescript
interface User {
    name: string
}
interface User {
    lastName: string
}
interface User {
    health: number 
}

const nico: User = {
    name: '1',
    lastName: '2', 
    health: 1
}
```



