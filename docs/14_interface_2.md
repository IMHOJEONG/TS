ㅣ### interface vs type 

- 상속하는 방법이 각각 다름 

- 각각 인터페이스는 타입스크립트가 알아서 합쳐주지만, type은 이걸 할 수가 없음 

- 이 둘은 타입스크립트에게 오브젝트의 구조를 알려주는 같은 작업을 수행할 수 있지만, 

- 둘 중 하나를 더 선호하게 만드는 기능 존재 

#### 추상 클래스 복습 

- 다른 클래스가 가져야 할 프로퍼티랑 메소드를 명시할 수 있도록 도와줘 

```typescript
abstract class User {
    constructor(
        protected firstName: string,
        protected lastName: string
    ) {}
    abstract sayHi(name: string): string
    abstract fullName(): string
}
```

- 현재까지 아무것도 구현하지 않고, 다른 클래스가 따라야 할 청사진(설계도)만을 제시했을 뿐 

```typescript
abstract class User {
    constructor(
        protected firstName: string,
        protected lastName: string
    ) {}
    abstract sayHi(name: string): string
    abstract fullName(): string
}

class Player extends User {
    fullName() {
        return `${this.firstName} ${this.lastName}`
    }

    sayHi(name: string) {
        return `Hello ${name}. My Name is ${this.fullName()}`
    }
}
```
- protected는 추상 클래스로부터 상속받은 클래스들이 프로퍼티에 접근하도록 해줌 

- private을 쓰면, firstName, lastName을 Player가 접근할 수 없어 

---

- 추상화를 원할 때, 클래스와 인터페이스를 사용할 때의 차이점?

- 추상 클래스는 인스턴스를 만드는 것을 허용하지 않아 

- 클래스에게 어떻게 구현할지에 대해서는 알려주지 않지만 

    - 무엇을 구현해야 할 지는 알려줌 

- 추상 클래스의 문제점 

    - 자바스크립트에는 abstract의 개념이 없다는 것 

### 중요한 점 

- 추상 클래스를 만들면 보이는 것처럼 결국 클래스로 변해버림 

- 그러면 왜 추상 클래스를 만드는 것일까?

- 다른 클래스들이 표준화된 프로퍼티와 메소드를 갖도록 해주는 청사진을 만들기 위해! 사용

```typescript
abstract class User {
    constructor(
        protected firstName: string,
        protected lastName: string
    ) {}
    abstract sayHi(name: string): string
    abstract fullName(): string
}

class Player extends User {
    fullName() {
        return `${this.firstName} ${this.lastName}`
    }

    sayHi(name: string) {
        return `Hello ${name}. My Name is ${this.fullName()}`
    }
}

class User {}
```

- 우리는 많은 Player를 만들 것 

- User를 직접적으로 만들지도 않는데?

- 하지만! 여전히 이 코드는 JavaScript 코드 결과에 존재함 

- 바로 지금이! 인터페이스를 써야할 때

---

`인터페이스는 가벼워. 인터페이스는 컴파일하면 JS로 바뀌지 않고 사라짐`

- 또 다른 질문 

    - 인터페이스를 쓸 때, 클래스가 특정 형태를 따르도록 어떻게 강제하냐 

- 하고 싶은 것 

    - 추상클래스를 인터페이스로 바꾸는 것 

- 인터페이스는 constructor, abstract 이런 것들이 없음 

    - 하지만, 인터페이스는 오브젝트나 클래스의 모양을 묘사하도록 해줌 

```typescript
interface User {
    firstName: string,
    lastName: string,
    sayHi(name: string): string
    fullName(): string
}

class Player implements User {
    fullName() {
        return `${this.firstName} ${this.lastName}`
    }

    sayHi(name: string) {
        return `Hello ${name}. My Name is ${this.fullName()}`
    }
}
```

- extends를 쓰게 되면, 자바스크립트로 바뀜 

- 자바스크립트는 클래스 뒤에 extends를 붙이는 문법을 사용해, 클래스를 상속받을 수 있어

#### implements를 썼을 때 장점 

- 가장 먼저, 코드가 가벼워져 

- 인터페이스는 타입스크립트에서만 존재함 

    - 자바스크립트에서는 존재하지 않게 됨 

- 하지만, 타입스크립트가 Player는 User 인터페이스를 상속해야 한다고 알려주고 있음 

```typescript
interface User {
    firstName: string,
    lastName: string,
    sayHi(name: string): string
    fullName(): string
}

class Player implements User {
    constructor(
        private firstName: string, // public이 되어야 함 
        private lastName: string  // public이 되어야 함 
    ) {}
}

// Class 'Player' incorrectly implements interface 'User'.
//  Type 'Player' is missing the following properties from type 'User': firstName, lastName, sayHi, fullName
```

- 하지만, 타입스크립트는 Player가 User 인터페이스를 사용해야 한다고 알려줌 

- 클래스가 원하는대로 행동하고, 프로퍼티를 강제하게 만듬 

- 추상클래스는 자바스크립트에서 클래스로 바뀌어 

- 그래서. 인터페이스는 타입스크립트에서만 존재 

### 문제 

- 인터페이스를 상속할 떄는 프로퍼티를 private으로 만들지 못함 

    - 항상 public이 되어야 함 

- 인터페이스는 고유한 사용처가 존재 

    - 클래스의 모양을 알려준다는 점에서 매우 유용 
 
- 인터페이스를 상속하는 것의 문제점 중 하나는 private property들을 사용하지 못한다는 것 

- 하나 이상의 인터페이스를 동시에 상속 가능 

---

- 어댑터 패턴과 같은 디자인 패턴을 사용하여 팀과 함께 일할때 정말 중요 

    - 인터페이스를 만들어두고 팀원이 원하는 각자의 방식으로 클래스를 상속하도록 하는 건 

    - 모두가 같은 인터페이스를 가지게 될 수 있는 것 

- 인터페이스를 타입으로 지정 가능 

```typescript

data: User

function makeUser(user: User) {

}

makeUser({
    firstName: "nico",
    lastName: "las",
    fullName: () => "xx",
    sayHi: (name) => ''
})
```

- 인터페이스를 반환한다면? => new User 같은 게 필요 없어 

    - 인터페이스의 내용만 넣어주면 됨 

    
