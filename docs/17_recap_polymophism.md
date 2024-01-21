### 다형성, 제네릭, 클래스, 인터페이스를 모두 합쳐보자 

- 다형성 : 다른 모양의 코드를 가질 수 있게 해주는 것 

- 다형성을 이룰 수 있는 방법은 제네릭을 사용하는 것 

- 제네릭은 placeholder 타입을 쓸 수 있도록 해줌 

- concrete 타입이 아니라, placeholder 타입 

    - 때가 되면, 타입스크립트가 placeholder 타입을 concrete 타입으로 바꾸어 줄 것 

- 코드를 더 예쁘게 해주고, 같은 코드를 다른 타입에 대해서 쓸 수 있도록 해줌 

- call signature, 클래스를 만들어 볼 것 

```typescript
interface Storage {
    
}

// This Web Storage API interface provides access to a particular domain's session or local storage. It allows, for example, the addition, modification, or deletion of stored data items.
```
- 타입스크립트에 의해 이미 선언된 자바스크립트의 웹 스토리지 API를 위한 인터페이스 

- 다른 인터페이스를 오버라이드하기 싫으면, 인터페이스 이름을 변경해라 

- string, boolean 혹은 number만을 위한 로컬스토리지를 만들고 싶다면? 

    - localStorage를 초기화할 때, 타입스크릅트에게 T라고 불리는 제네릭을 받을 계획이라고 알려줄 거야 

- 제네릭에 대해 한 가지 놀라운 것은 

    - 이걸 다른 타입에게 물려줄 수 있다는 것 

- 제네릭은 클래스 이름에 들어오지만, 같은 제네릭을 인터페이스로 보내준다?

```typescript
interface SStorage<T> {
    [key: string]: T
}

class LocalStorage<T> {
    private storage: SStorage<T> = {
        
    }
}

```

- 제네릭을 클래스로 보내고, 클래스는 제네릭을 인터페이스로 보낸 뒤에 

    - 인터페이스는 제네릭을 사용해 

```typescript
interface SStorage<T> {
    [key: string]: T
}

class LocalStorage<T> {
    private storage: SStorage<T> = {
        
    }
    set(key: string, value: T) {
        this.storage[key] = value;
    } 
    remove(key: string) {
        delete this.storage[key];
    }
    get(key: string): T {   
        return this.storage[key]
    }
    clear() {
        this.storage = {}
    }
}
// 로컬스토리지 API를 따라해봄 => 그렇지만, 제네릭을 쓰고 있지 
```

- 타입스크립트는 놀랍게도 제네릭을 바탕으로 call signature를 만들어줌 

```typescript
interface SStorage<T> {
    [key: string]: T
}

class LocalStorage<T> {
    private storage: SStorage<T> = {
        
    }
    set(key: string, value: T) {
        this.storage[key] = value;
    } 
    remove(key: string) {
        delete this.storage[key];
    }
    get(key: string): T {   
        return this.storage[key]
    }
    clear() {
        this.storage = {}
    }
}

const stringsStorage = new LocalStorage<string>()

stringsStorage.get("key")

const booleansStorage = new LocalStorage<boolean>()

booleansStorage.get('true')

```

- 제네릭, 다형성, 클래스와 인터페이스를 합쳐서 작업하는 게 얼마나 쉬운가 

- 타입스크립트가 하는 것은 이 T인 value를 string인 value로 바꾸어주는 것 

(method) LocalStorage<string>.set(key: string, value: string): void

(method) LocalStorage<boolean>.set(key: string, value: boolean): void
