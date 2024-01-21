```typescript
let a : number = 1; 
let b : string[] = "i1";
let c : boolean[] = [true]
```

- 콜론을 써주고 타입써주면 모든 곳에서 작동함 

- 어떤 때는 타입스크립트가 자동으로 추론하게 해주는 것도 좋음 

  - 가능한 한 TS가 할 수 잇게 해주는 게 좋아 

### Optional 

```
const player = {
  name: "nico"
}
```

- player가 name은 있지만, 몇몇은 age가 있다면? 

- name은 항상 가지고 있고, age가 있다면? 

- player가 object 타입이어야 하는가?

  - No => TS는 player에 name이 존재하는지 모른다고 함 

  - object 타입에는 name 요소가 없다고 나와있기 때문 

- 하고 싶은 것은 object의 타입을 정의

```
const player: {
  name: string, 
  age: number
} = {
  name: "nico"
}
// age를 찾지 못했기 때문 => age를 갖거나 갖지 못하게 해야 함 

const player: {
  name: string, 
  age?: number
} = {
  name: "nico"
}
```

- player는 object 타입이고, name은 string, age는 number | undefined가 됨 

    - if(player.age > 0)  // error
    - if(player.age && player.age > 0) // ok~

- optional parameter를 지정하는 방법 

---

- 계속 반복해야 한다면 => 별칭을 사용할 수 있음 

- 내 코드가 많은 타입을 재사용할 수 있게 하는 것을 좋아함 

- 과하게 재사용하는 건 좋지 않아 (코드가 깔끔해지고, 명확해질 때까지 하는 게 좋음)

```
type Age = number; 
type Name = string;
// 처음은 대문자로
type Player = {
  name: Name,
  age?: Age
}

const player: Player = {
  name: "nico"
}

```

- 함수가 return하는 타입이 무엇인지 알면, 멋진 자동 완성과 더 많은 보호장치를 줌 

- TS에게 playerMaker는 Player 타입을 return하고 있다고 말해주고 싶음 

```typescript
function playerMaker(name: string): Player{
  return {
    name
  }
}

const nico = playerMaker("nico") 
nico.age = 12 // 잘못됨 
```

- let a : 뒤에 타입을 써줄 수도 있고, 인수에서 이름을 쓰고 타입을 쓰거나, 함수에서 뒤에 타입을 써주면 돼 

```
const playerMaker = (name: string) : Player => ({name})

```

