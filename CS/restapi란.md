# Rest란?
-자원을 URI로 표시하고 해당 자원의 상태를 주고 받는 것을 의미한다.<br/>
이때, Rest구성 요소는 자원=URI , 행위= HTTP METHOD, 표현 이렇게 3가지로 이루어져 있다.<br/>
즉 Rest는 URI를 통해 자원을 표시하고, HTTP METHOD를 이용하여 해당 자원의행위를 정해주며 그 결과를 받는것을 말한다.<br/>

# Rest특징
1. Uniform Interface 유니폼 인터페이스이다.
* HTTP 표준만 따른다면 어떤 언어 혹은 어떤 플랫폼에서 사용하여도 사용이 가능한인터페이스 스타일이다.
2. Stateless (상태 정보 유지를 하지 않아도 된다.)
* Rset는 상태 정보를 유지하지 않는다. 
* 서버는 각각의 요청을 완전히 다른 것으로 인식하고 처리한다.
* 이전 요청이 다음 요청 처리에 연관이 되면 안된다.
3. Casheable(캐시 가능하다.)
HTTP의 기존 웹 표준을 그대로 사용하기 때문에 HTTP가 가진 캐싱 기능 적용이 가능하다.
4. Self-descriptiveness(자체 표현 구조)
* Rest API 메세지만 보고도 쉽게 이해할 수 있는 자체 표현 구조로 되어 있다.
5. Client-Server
* Rest 서버는 API 제공을 하고 클라이언트는 사용자 인증에 관련된 일들을 직접 관리한다.
자원이 있는 쪽을 Server라고 하고 자원을 요청하는 쪽이 Client가 된다.
서로간의 의존성이 줄어들기 때문에 역할이 확실하게 구분되어 개발해야할 내용들이 명확해진다.
6. Layerd System (계층화)
* 클라이언트는 Rest API 서버만 호출한다.
* Rest 서버는 다중 계층으로 구성될수 있으면 로드 밸런싱, 암호화, 사용자 인증 등을 추가하여 구조상의유연성을 둘 수 있다.

# Rest API란
* Rest 기반의 규칙들을 지켜서 설계된 API를 Rest API혹은 Restful API라고 한다.

# Restful API란
* 누군가 공식적으로 발표한 것이 아니고 개발자들이 비공식적으로 의견을 제기한 것이라 명확한 정의가 없다.<br/>
하지만 Restful의 목적은 이해하기 쉽고 사용하기 쉬운 Rest API를 만드는 것이다.<br/>

* 해당하는 매소드의 이벤트를 직관적으로 설계하는 기법.
GET : /users/{userid}/devices - rest api
GET: /users/:id/nickname - restful api
