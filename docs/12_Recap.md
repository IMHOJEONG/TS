### Recap

- private, protected, public이 와도 Javascript에서는 보이지 않는다는 것 => 매우 중요해 

- 추상 클래스 : 직접적으로 인스턴스를 만들지 못하는 클래스이지만, 그 클래스를 상속할 수 있어 

- 메소드를 보호 가능 

```typescript
abstract class User {
      
    constructor(
        private firstName: string, 
        private lastName: string,
        protected nickname: string,
    ) {}
    abstract getNickName(): void
    protected getFullName() {

    }

}

class Player extends User{
    getNickName() {
        this.getFullName(); // 여기는 가능
        console.log(this.nickname)
    }
}

const nico = new Player("nico", "las", "니꼬")

nico.getFullName() // 에러 
```

- 추상 메서드는 구현이 되어 있지 않은 (코드가 없는) 메소드 

- call signature만 가지고 있고, 함수의 이름과 argument를 안 받을 때도 있지만

    - argument를 받을 경우, argument의 이름과 타입 그리고 함수의 리턴타입을 정의하고 있어 

- 추상 메소드가 있는 경우, 추상 클래스를 상속받는 클래스에서 넌 추상 메소드를 구현해주어야 해 

- TS에서 제공하는 기능들 : 추상 클래스, 추상 메소드, private, public 

```typescript
abstract class User {
      
    constructor(
        private firstName: string, 
        private lastName: string,
        protected nickname: string,
    ) {}
    abstract getNickName(): void
    protected getFullName() {

    }

}

class Player extends User{
    getNickName() {
        this.getFullName();
        console.log(this.nickname)
    }
}

const nico = new Player("nico", "las", "니꼬")

new User("nico", "las", "니꼬")

//Cannot create an instance of an abstract class.(2511)
```

### 모든 보호 기능은 TypeScript에서 작동해 

```typescript
type Words = {
    [key:string]: string
}
```

- 제한된 양의 property 혹은 key를 가지는 타입을 정의해주는 방법 

- property의 타입만 알고 있을 때 사용하면 됨 

```typescript

class Dict {
    private words: Words
}

//Property 'words' has no initializer and is not definitely assigned in the constructor.(2564)

// 아래와 같이 작성하면 적용됨 
type Words = {
    [key:string]: string
}

class Dict {
    private words: Words
    constructor() {
        this.words = {}
    }
}

```

- words는 initializer가 없고, Constructor에서 정의된 sign이 아니라는 에러 

- 클래스를 타입처럼 사용할 수 있음 (근사함)

ㅜ 

