### Typescript - 객체 지향 프로그래밍 

- Typescript가 많은 양의 반복되는 코드들을 쓰지 않도록 어떻게 막아주는가?

- 클래스

- 파라미터들을 써주기만 하면, Typescript가 알아서 Constructor 함수를 만들어줌 

```typescript
class Player {
    
    constructor(
        private firstName: string, 
        private lastName: string,
        public nickname: string

    ) {}
}

const nico = new Player("nico", "las", "니꼬")
```

- 거의 모든 객체지향 프로그래밍 언어들이 가지고 있는 특징 

- private 부분은 JavaScript에서는 안 보임 

    - TS가 오직 우리를 보호하기 위해서 사용함 


```typescript
class Player {
    
    constructor(
        private firstName: string, 
        private lastName: string,
        private nickName: string,
    ) {}
}

const nico = new Player("nico", "las", "니꼬")

nico.firstName
// Property 'firstName' is private and only accessible within class 'Player'.(2341)
```

### 추상 클래스 (abstract Class)

- 추상 클래스는 다른 클래스가 상속받을 수 있는 클래스 

- 하지만, 이 클래스는 직접 새로운 인스턴스를 만들 수는 없어 

```typescript
abstract class User {
      
    constructor(
        private firstName: string, 
        private lastName: string,
        private nickName: string,
    ) {}
}

class Player extends User{
    
}

const nico = new User("nico", "las", "니꼬")
//Cannot create an instance of an abstract class.(2511)
```

- 추상 클래스 : 오직 다른 곳에서 상속받을수만 있는 클래스 

- 추상 클래스 안의 메소드 vs 추상 메서드 

```typescript
abstract class User {
      
    constructor(
        private firstName: string, 
        private lastName: string,
        private nickName: string,
    ) {}

    private getFullName() {
        return `${this.firstName} ${this.lastName}`
    }

}

class Player extends User{
    
}

const nico = new Player("nico", "las", "니꼬")

nico.getFullName()
// Property 'getFullName' is private and only accessible within class 'User'.(2341)
```

- TS가 에러가 생기기 전에 어떻게 보호해주는지 알려줌  

- 그러면, 추상 메서드는?

    - 메소드를 클래스 안에서 구현하지 않으면 돼 

    - 오직 메소드의 call signature만 적어둬야 해 

```typescript
abstract class User {
      
    constructor(
        private firstName: string, 
        private lastName: string,
        private nickName: string,
    ) {}
    abstract getNickName(): void // here 
    getFullName() {

    }

}

class Player extends User{
    
}
// input.tsx(8, 14): Non-abstract class 'Player' does not implement inherited abstract member 'getNickName' from class 'User'.
```

- 추상 메소드는 추상 클래스를 상속받는 모든 것들이 구현을 해야하는 메소드를 의미함 

- 구현은 어떻게 되어도 상관없지만, 구현은 되어야 해

```typescript
abstract class User {
      
    constructor(
        private firstName: string, 
        private lastName: string,
        private nickName: string,
    ) {}
    abstract getNickName(): void
    getFullName() {

    }

}

class Player extends User{
    getNickName() {
        console.log(this.nickname)
        // Property 'nickname' does not exist on type 'Player'.(2339)

    }
}
```

- 만약 property를 private으로 만든다면, 클래스를 상속하였을지라도, Player가 User를 상속받지만, 접근할 수 없음 

- private, public, protected 

    - private : 인스턴스 밖에서 접근할 수 없고, 다른 자식 클래스에서도 접근할 수 없음 


- 만약 필드가 외부로부터는 보호되지만, 다른 자식 클래스에서는 사용되기를 원한다면 

    - protected를 사용하는 게 나음 

```typescript
abstract class User {
      
    constructor(
        private firstName: string, 
        private lastName: string,
        protected nickname: string,
    ) {}
    abstract getNickName(): void
    getFullName() {

    }

}

class Player extends User{
    getNickName() {
        console.log(this.nickname)
    }
}

```
