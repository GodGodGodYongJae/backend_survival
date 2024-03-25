# 🟦 REST(Representational State Transfer)

아키텍처 스타일 중 REST란 것이 있다.\
정의는 자원(Resource)의 표현 (Representation)에 의한 상태 전달

자원을 이름으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든것을 의미한다.

여기서 Resource는 Entity ( 객체 )와 비슷하다.\


<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

객체지향의 사실과 오해의 표현에서도 앨리스라는(객체)의 키가 커지던 작아지던 항상 앨리스이며\
이 정보를 조작하는 것이 Representation이라 볼 수 있다.\


REST 구성요소\


1. 자원 ( Resource ) URI

* 모든 자원에 고유한 ID가 존재하고 이 자원은 Server에 존재한다.
* HTTP URI로 자원을 구별한다.
* Client는 URI를 이용해서 자원을 지정하고 해당 자원의 상태(정보)에 대한 조작을 Server에 요청한다.

2. 행위(Verb) : HTTP Method

* HTTP 프로토콜의 Method를 사용한다.
* HTTP 프로토콜은 GET,POST,PUT,DELTE와 같은 메소드를 제공한다.

3. 표현(Representation of Resource )

* Client가 자원의 상태에 대한 조작을 요청하면 Server는 이에 적절한 응답을 보낸다.
* REST에서 하나의 자원은 JSON,XML,TEXT,RSS등 여러 형태로 표현 할 수 있다.

\-[https://velog.io/@alwaysryu13/REST-%ED%86%B5%EC%8B%A0%EC%9D%B4%EB%9E%80-Java%EB%A1%9C-REST%ED%86%B5%EC%8B%A0%EA%B5%AC%ED%98%84%ED%95%B4%EB%B3%B4%EA%B8%B0](https://velog.io/@alwaysryu13/REST-%ED%86%B5%EC%8B%A0%EC%9D%B4%EB%9E%80-Java%EB%A1%9C-REST%ED%86%B5%EC%8B%A0%EA%B5%AC%ED%98%84%ED%95%B4%EB%B3%B4%EA%B8%B0)\
특징 정리.. TODO
