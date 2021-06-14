### Makefile

#### Makefile의 구성

1. 목적파일
   - 명령어가 수행되어 나온 결과를 저장할 파일
2. 의존성
   - 목적파일을 만들기 위해 필요한 재료
3. 명령어
   - 실행되어야 할 명령어들
4. 매크로
   - 코드를 단순화시키기 위한 방법

#### Makefile 기본구조

![image-20210614093925535](C:\Users\083726\AppData\Roaming\Typora\typora-user-images\image-20210614093925535.png)

#### Makefile 작성규칙

> 목표파일 : 목표파일을 만드는데 필요한 구성요소들
>
> (tab) 커맨드1
>
> (tab) 커맨드2

- 매크로 정의 : Makefile에 정의한 string으로 치환
- 명령어의 시작은 반드시 탭으로 시작
- Dependency가 없는 타겟도 사용 가능



#### Makefile 개선 : 매크로 사용

- 중복되는 파일 이름들을 특정 단어로 치환

##### 매크로 작성규칙

> - 매크로를 참조할 때는 소괄호나 중괄호로 둘러싸고 앞에 $를 붙임
> - 탭으로 시작해서는 안되고, ,:,=,#,"등은 매크로 이름에 사용할 수 없음
> - 매크로는 반드시 치환될 위치보다 먼저 정의되어야 함

![image-20210614095938614](C:\Users\083726\AppData\Roaming\Typora\typora-user-images\image-20210614095938614.png)

#### Makefile 개선2 :  내부 매크로 사용

##### 내부 매크로 작성규칙

> "$@": 현재 타겟의 이름
>
> "$^" : 현재 타겟의 종속 항목 리스트

![image-20210614100001499](C:\Users\083726\AppData\Roaming\Typora\typora-user-images\image-20210614100001499.png)

