### Declaration Files 

- 타입스크립트가 localStorage, Math, Window 등의 타입을 이해하고 인지한다는 것을 알게 됨 

- 어떻게 타입스크립트가 그것들을 아는가 알아보자 

- Specify a set of bundled library declaration files that describe the target runtime environment.

- 핵심 : 타입스크립트라 기본 정의는 가지고 있다 

    - 누군가 시간을 들여서, TS에게 localStorage 구조, 매개변수, 리턴값, 리턴 타입을 설명해 준 것 

    - 이것이 타입 정의!

- 타입 정의: TS에게 몇몇 JS 코드의 타입을 설명해주기 위해 사용하는 것 

- 타입 정의를 써야 하는 이유 = ts를 사용하는 목적과 연결되어 있음 

    - 타입스크립트와 다양한 것에 대해 소통해야 함 

- 대부분의 경우, 다른 패키지, 프레임워크, 라이브러리를 사용함 

    - 그 패키지나, 프레임워크, 라이브러리는 ts가 아닌 js로 만들어짐 

    - 그래서 js로 만들어진 라이브러리를 ts 프로젝트에 쓰려고 한다면?
         
        - ts는 그것들의 타입에 대해 알 수가 없음 

- TS는 JS 코드를 쓸 수 있도록 해주는데, 그게 안 되면 아무도 TS를 쓰지 않을 것 
    
    - TS는 대부분 우리가 JS lib, package를 사용한다는 것을 알기 때문에..

    - TS에게 우리가 불러올 JS 함수의 모양을 설명하려면 타입 정의가 필요함 

- import { init } from "myPackage" 해도, 클릭하면 init 함수로 이동하지 않아

    - 하지만! init()처럼 쓰면 함수는 작동 

    - TS가 나를 보호해주지 못한다는 증거 

- TS가 우리를 보호해주지 못하는 이유는 TS가 strict 모드로 설정되지 않아서 그럼 

    - strict: true

- Could not find a declaration file for module 'myPackage'. 'e:/typescript_block_chain/typechain/src/myPackage.js' implicitly has an 'any' type.ts(7016)


    - strict: true 시 바로 에러 뜨는 거 확인 가능 

- localStorage작성 후 클릭 하면, 정의 파일로 이동되는 것과 같은 예 

    - TS에게 localStorage 옵션을 설명해줄 수 있는 것 

- 자동완성은 마법처럼 일어나는 일이 아님 

    - TS가 d.ts라는 정의 파일을 가지고 있기에 가능한 것 

- d.ts에서 TS는 우리가 사용하는 정의 파일을 찾아냄 

    - myPackage.d.ts = declare module "myPackage" {}

- TS가 그것이 존재한다는 것은 알지만, init이라는 것이 있는지는 모름 

```typescript
interface Config {
    url: string;
}
declare module "myPackage" {
    function init(config:Config): boolean;
}
```

- TS에게 타입을 알려주는 것 

- TS는 내가 쓰는 모든 것에 대한 타입을 이해하고 있어야 함 

- 설명도, 타입 정의 파일에 있는 주석을 읽어줄 뿐 

- TS에게 패키지가 어떻게 생겼는지, 어떤 함수랑 다른 것들이 있는지를 설명해줘야 함 

- lib 옵션을 수정하면, 통합된 라이브러리의 정의 파일을 지정할 수 있게 돼 

- lib.dom.d.ts

- npm 파일이나 프로젝트를 다운받았는데, 타입이 없어서 TS가 불만을 표시하고 있으면..

- 다운로드 받는 모든 모듈에 이럴 필요는 없구 

---

- npm과 node_modules에 있는 패키지를 사용하는 것처럼하는 대신에 

    - 실제 파일에서 호출해보자 

import { init } from "myPackage"

=> import { init } from "./myPackage"

- 다른 케이스이지만, 모두 일어날 수 있는 상황 