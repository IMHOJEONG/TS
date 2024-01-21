### Block 구현 

- 현재 코드는 빌드를 돌려야만, TS를 실행가능 

- TS-NODE 설치 

    - 빌드 없이 TS 실행

    - 프로덕션이 아닌, 개발 환경에서만 사용하는 것 

    - 빌드 없이 빠르게 새로고침하고 싶을 때 사용

    - ts-node가 컴파일할 필요없이 TS 코드를 대신 실행 

- 빌드를 계속 수행하면 작업 속도가 느려지니까..

- 원한다면 nodemon도 설치 ㄱ

    - nodemon은 자동으로 커멘드를 재실행해줌 

    - 일일히 커맨드를 다시 실행할 필요가 없어짐 (서버 재시작 필요 X)

---

### Blockchain

- 여러 개의 블록이 사슬처럼 구성 

- 블록 안에는 데이터(보호하고 싶음)

    - 다른 블록에 묶여있음 

    - 연결값은 해쉬값

- 해쉬는 그 블록 값의 고유 서명과 같은 것 

- 해쉬 값은 결정론적임 

    - 똑같은 이상한 해쉬값이 항상 나오기 때문 

- import *  as crypto from 'crypto';

    - ???

    - tsconfig.json

    - esmoduleInterop.true로 해야 위처럼 import 가능 

---

- JS에서는, 여러 모듈 시스템이 존재 

    - import, export가 기본설정이 아님 

- allowJs 설정이 없을 때만 나타나는 에러가 있음 

    - 엄청 자주 보이는 에러 

```json
{
    "include": [
        "src"
    ],
    "compilerOptions": {
        "outDir": "build",
        "target": "es6",
        "lib": ["ES6"],
        "strict": true,
        "esModuleInterop": true,
        "module": "CommonJS"
    }
}
```

- module은 브라우저 앱을 만들고 있었다면, umd를...

- 대체적으로 브라우저 앱을 만들 때는 TS 코드만 쓰지는 않음 

- 아마 웹팩을 사용할 거고, 웹팩이 TS를 사용할 것 

- d.ts 파일을 작성할 경우도 많음 

    - 효율적인 방법은 아님

    