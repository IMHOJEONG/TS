### JSDOC

- js로 만들어진 패키지에서, TS에 그 패키지의 타입을 정의하는 방법에 대해 알아봄
 
- JS 패키지를 TS 프로젝트에 설치할 일은 많았음 

- 스스로 타입 정의 파일을 써야 할 일은 많지 않아용 

- 프로젝트 안에 JS, TS 파일이 같이 있는 경우가 많음 

    - JS => TS로 이전하는 경우라면 특히 많음 

```typescript
import { init, exit } from './myPackage'

// All imports in import declaration are unused.ts(6192)
// (alias) function init(config: any): boolean
// import init
```

- TS가 엄청 불평함 => allowJs: true

- 주석 처리 부분을 보면, 함수들의 호출 시그니처를 추론하고 있음 

     - JS와 TS 파일을 섞어서 프로젝트 진행해도 괜찮음 

- 옛날 코드는 JS로 작성하고, 최신은 TS로..

- 완전히 TS로 이전하고 싶지 않다면 ??

    - 코드가 몇 천줄이나 있는 프로젝트는?

        - 파일은 그냥 JS로 두고, TS의 보호를 조금 받고 싶다?

- TS는 가능 

    - // @ts-check

        - JS 파일에 TS가 제공하는 보호 장치 쓰고 싶을 때 

        - 이럴 떄 JSDoc을 사용 

- 함수 바로 위에 코멘트를 제대로 작성하면 됨 

    - js 파일에서도 ts 파일에서처럼 하고 싶을 때 

```js

/**
 * Initailzes the project 
 * @param {object} config
 * @param {boolean} config.debug
 * @param {string} config.url 
 * @returns {void}
 */
```
- TS 코드를 작성하지 않고, 코드 안에 코멘트를 적고 싶을 뿐임 

- 만약 이 코드를 실제 웹사이트, 서버 프로덕션 환경에서 사용 중이라면...

    - 당장 코드에서 에러날 걱정은 안해도 됨 (코멘트만 더할뿐)

    - TS가 확인해주는 상황 & 브라우저에서 문제없이 실행될 것 

- `JS 파일 안에 JSDoc 코멘트만 더하면, TS가 도와줌`

```js
// @ts-check

/**
 * Initailzes the project 
 * @param {object} config
 * @param {boolean} config.debug
 * @param {string} config.url 
 * @returns {boolean}
 */
export function init(config) {
    return true;
}

export function exit(code) {
    return code + 1;
} 
```

- 코드를 완전히 TS 코드로 바꿀 필요 없이, 그냥 코멘트만 적으면 됨 

- @ts-check, allowJs: true, JSDOC 이 3가지가 준비되면 됨

1. 파일 전체를 위한 타입 정의를 생성했어 

2. jsdoc

