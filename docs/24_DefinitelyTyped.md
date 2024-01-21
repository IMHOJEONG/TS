### DefinitelyTyepd 

- TS로 작성되지 않은 패키지를 import할 때

    - 타입 정의를 일일이 다 적고 싶지 않을 때 

- d.ts 파일에 다 적어서 설명할 것인가?

- crypto 패키지 안의 함수를 다 설명해야 함 

    - `사용하려는 라이브러리나 패키지마다 정의 파일을 만들고 있을 순 없어`

- 그래서, TS에게 패키지 안의 타입에 대해서 설명해주고, TS의 보호 장치를 사용할 수 있게 하고 싶단 말 

- TS에게 일일이 다 설명해주고 싶지는 않은데, TS의 보호는 받고 싶음 

- 타입 정의 하나도 없고, TS가 아닌 패키지는 어떻게 관리?

- DefinitelyTyped라는 repo로 가보자 

- https://github.com/DefinitelyTyped/DefinitelyTyped

- DefinitelyTyped

    - 엄청나게 큼 & 많은 사람이 이용 

    - 오직 타입 정의만 있음 

    - npm에 존재하는 거의 모든 패키지에 대해 있음 

- 여러 자원봉사자가 참여한 레포 

- 여러 개발자들이 여러 repo에 대해서 정의해둠 

    - 정의만 존재 

- 전체복사보다, 콘솔에 설치 

    - @types/node

- 최근에는 설치할 필요가 없어짐 

    - d.ts 파일을 포함하는 경우도 많음 

- TS 한테 node 안에 있는 정보를 다 알려주려면..

    - @types/node

    


