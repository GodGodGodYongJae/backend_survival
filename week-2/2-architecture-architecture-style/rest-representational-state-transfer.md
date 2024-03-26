---
description: >-
  참고
  -https://velog.io/@alwaysryu13/REST-%ED%86%B5%EC%8B%A0%EC%9D%B4%EB%9E%80-Java%EB%A1%9C-REST%ED%86%B5%EC%8B%A0%EA%B5%AC%ED%98%84%ED%95%B4%EB%B3%B4%EA%B8%B0
---

# 🟦 REST(Representational State Transfer)

## REST 정의

아키텍처 스타일 중 REST란 것이 있다.\
정의는 자원(Resource)의 표현 (Representation)에 의한 상태 전달

자원을 이름으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든것을 의미한다.

여기서 Resource는 Entity ( 객체 )와 비슷하다.\


<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

객체지향의 사실과 오해의 표현에서도 앨리스라는(객체)의 키가 커지던 작아지던 항상 앨리스이며\
이 정보를 조작하는 것이 Representation이라 볼 수 있다.\


REST 구성요소\



1. 자원 ( Resource )

* 모든 자원에 고유한 ID가 존재하고 이 자원은 Server에 존재한다.
* HTTP URI로 자원을 구별한다.
* Client는 URI를 이용해서 자원을 지정하고 해당 자원의 상태(정보)에 대한 조작을 Server에 요청한다.

2. 행위(Verb) : HTTP Method

* HTTP 프로토콜의 Method를 사용한다.
* HTTP 프로토콜은 GET,POST,PUT,DELTE와 같은 메소드를 제공한다.

3. 표현(Representation of Resource )

* Client가 자원의 상태에 대한 조작을 요청하면 Server는 이에 적절한 응답을 보낸다.
* REST에서 하나의 자원은 JSON,XML,TEXT,RSS등 여러 형태로 표현 할 수 있다.

\


## REST 특징

### Server - Client ( 서버 클라이언트 구조 )

Server(Rest Server)&#x20;

* 자원(Resource)를 가지고 있는 쪽. API를 제공하고 비지니스 로직 처리 및 저장을 책임진다.

Client&#x20;

* 자원을 요청하는 쪽. 사용자 인증이나, context(세션, 로그인 정보) 등을 직접 관리하고 책임진다.

### Stateless(무상태)

* HTTP 프로토콜은[ **Stateless Protocol**](rest-representational-state-transfer.md#stateless) 이므로 REST 역시 무상태성을 갖는다.
* Client의 context를 Server에 저장하지 않는다.
* Server는 각각의 요청을 완전히 별개의 것으로 인식하고 처리한다.
* 이전 요청이 다음 요청에 영향을 주면 안된다.
* Server의 처리 방식에 일관성을 부여하고 부담이 줄어들며, 서비스의 자유도가 높아진다.

### Casheable ( 캐시 처리 가능 )

* HTTP 표준에서 사용하는 **Last-Modified** 태그나 E-Tag를 이용하면 캐싱 구현이 가능하다.
* 캐시 사용을 통해 응답시간이 빨라지고 Rest Server 트랜잭션이 발생하지 않기 때문에 전체 응답시간,성능 서버의 자원을 효율적으로 향상 시킬 수 있다.

### Layerd System ( 계층화 )

* API Server는 순수 비지니스 로직을 수행하고, 그 앞단에 보안, 로드 밸런싱, 암호화, 사용자 인증 등을 계층화 하여, 구조상의 유연성을 줄 수 있다.



### Uniform Interface ( 인터페이스 일관성 )

* [URI](../3-uri-uniform-resource-identifire.md)로 지정한 Resource에 대한 조작을 통일되고 한정적인 인터페이스로 수행한다.
* HTTP에 따르는 모든 플랫폼에서 사용이 가능하다. 특정 언어나 기술에 종속되지 않는다.
