# REST API

- Representational State Transfer
- www와 같은 분산 하이퍼 미디어 시스템을 위한 소프트웨어 아키텍처의 한 형식
- REST란 네트워크 아키텍처 원리의 모음
  - 네트워크 아키텍처 : 자원을 정의하고 자원에 대한 주소를 지정하는 방법 전반을 말함
- 간단한 의미로는, 웹 상의 자료를 HTTP위에서 SOAP나 쿠키를 통한 세션 트랙킹 같은 ㅇ별도의 전송계층 없이 전송하기 위한 아주 간단한 인터페이스



### 원리

##### 1. Rest 아키텍처에 적용되는 제한조건

1. 인터페이스 일관성
   - 일반적인 인터페이스로 분리되어야 함
2. 무상태(stateless) 
   - 각 요청 간 클라이언트의 콘텍스트가 서버에 저장되어서는 안됨
3. 캐시 처리 가능(Cacheable) 
   - 잘 관리되는 캐싱은 클라이언트-서버 간 상호작용을 부분적으로 또는 완전하게 제거하여 scalability와 성능을 향상
4. 계층화( layered System)
   - 클라이언트는 보통 대상 서버에 직접 연결되어 있는지, 또는 중간 서버를 통해 연결되었는지를 알 수 없음
   - 중간서버는 로드 밸런싱 기능이나 공유 캐시 기능을 제공함으로써 시스템 규모 확장성을 향상시키는 데 유용함
5. Code On demend(optional)
   - 자바 애플릿이나 자바스크립트의 제공을 통해 서버가 클라이언트가 실행시킬 수 있는 로직을 전송하여 기능을 확장시킬 수 있음
6. 클라이언트 / 서버 구조
   - 아키텍처를 단순화시키고 작은 단위로 분리함으로써 클라이언트-서버의 각 파트가 독립적으로 개선될 수 있도록 함

##### 2. 중심규칙

1. URI는 정보의 자원을 표현해야 함
2. 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE 등)으로 표현함

- > ex)
  >
  > GET /users/show/1 	(x)
  >
  > GET /users/1				(o)
  >
  > GET이라는 HTTP Method로 충분히 표한가능하기 때문에 /show/는 불필요함

3. Collection과 element로 나누어서 표현

- | Resource                                                     | GET                                                          | PUT                                         | POST                                                         | DELETE                             |
  | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------- | ------------------------------------------------------------ | ---------------------------------- |
  | **Collection** URI, such as `http://example.com/resources/`  | 컬렉션에 속한 자원들의 URI나 그 상세사항의 **목록**을 보여준다. | 전체 컬렉션은 다른 컬렉션으로 **교체**한다. | 해당 컬렉션에 속하는 새로운 자원을 **생성**한다. 자원의 URI는 시스템에 의해 할당된다. | 전체 컬렉션을 **삭제**한다.        |
  | **Element** URI, such as `http://example.com/resources/item17` | 요청한 컬렉션 내 자원을 **반환**한다.                        | 해당 자원을 **수정**한다.                   | 해당 자원에 귀속되는 새로운 자원을 **생성**한다.             | 해당 컬렉션내 자원을 **삭제**한다. |

4. 입력 Form 작성 방식

   - Form 자체도 정보로 취급해야 함

   - | HTTP Verb | Path             | action  | used for                                     |
     | --------- | ---------------- | ------- | -------------------------------------------- |
     | GET       | /photos          | index   | display a list of all photos                 |
     | GET       | /photos/new      | new     | return an HTML form for creating a new photo |
     | POST      | /photos          | create  | create a new photo                           |
     | GET       | /photos/:id      | show    | display a specific photo                     |
     | GET       | /photos/:id/edit | edit    | return an HTML form for editing a photo      |
     | PUT       | /photos/:id      | update  | update a specific photo                      |
     | DELETE    | /photos/:id      | destroy | delete a specific photo                      |

5. 접속환경에 따라 다른 정보 제공

   - 독립적인 모바일 환경을 구축할 경우 모바일 뷰와 웹페이지 뷰가 달라 적절한 디자인으로 보이지 않을 수 있음
   - 기존의 방식은 웹으로 접속한 경우와 모바일로 접속한 경우 최적화 되지 않은 디자인을 보여줌
   - REST한 URI는 **플랫폼 중립적**이어야 함
   - 정보를 보여줄 때 플랫폼을 구별해야 한다면, Request Header의 User-Agent 값을 참조



6. 버전정보와 포맷을 지정하는 방법

   - 오픈 API를 제공하거나, 클라이언트가 항상 최신버전을 유지할 수 없는 환경이라면 버전협상을 지원해야 함

   - 이외에도, 클라이언트가 html로 정보를 받을지, json으로 받을지, xml로 받을지 선택

   - Header의 Accept 헤더를 이용하여 요청환경에서 정보의 버전과 포맷을 지정

     > ex)
     >
     > vnd.example-com.foo+json; version=1.0
     >
     > - vnd는 Vender MIME Type으로,서비스 개발자가 자신의 독자적인 포맷을 규정할 수 있게 HTTP 표준에서 제공
     > - vnd. 이후에 서비스 제공자 이름을 쓰고, +로 문서의 기본포맷을 표현
     > - 추가저으로 파라미터를 이용해 버전명을 지정하는 것을 권장

7. Ajax와 REST

   - 초기에는 Ajax로 구성판 URL을 전송해도 보고있는 콘텐츠를 보여주기 불편했음
   - 최근에는 #!이후에 URI가 있으면 해당 URI로 redirect함

8. 언어

   - 언어별로 다른 URI를 서비스하는 것은 부적절
   - Request Header의 Accept-Language를 통해 받고자하는 언어를 명시



