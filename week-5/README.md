# 🗓️ Week 5

* Spring AOP(Aspect Oriented Programming)
* Dependency Injection
* 싱글턴 패턴
* IoC(Inversion of Control)
* Spring Bean
* BeanFactory
* V 모델
* Test Matrix
* 내적 품질(테스트 코드 작성등)을 높이면 좋은 이유
* JUnit
* 단위 테스트
* E2E 테스트
* 통합 테스트(Integration Test)
* [`@Autowired`](#user-content-fn-1)[^1]
* `@`[`SpyBean`](#user-content-fn-2)[^2]
* MockMvc[^3]
* MockBean[^4]
* [`@WebMvcTest`](#user-content-fn-5)[^5]
* [TDD 란](#user-content-fn-6)[^6]
* [TDD Cycle](#user-content-fn-7)[^7]\
  \
  \---
* 인프라[https://hudi.blog/system-design-interview-alex-xu-1/](https://hudi.blog/system-design-interview-alex-xu-1/))설계
* [https://jojoldu.tistory.com/226](https://jojoldu.tistory.com/226) - MockBean SpyBean

[^1]: 필요한 의존 객체의 “타입"에 해당하는 빈을 찾아 주입한다.

    * 생성자
    * setter
    * 필드

    &#x20;

    위의 3가지의 경우에 Autowired를 사용할 수 있다. 그리고 Autowired는 기본값이 true이기 때문에 의존성 주입을 할 대상을 찾지 못한다면 애플리케이션 구동에 실패한다. 그러면 Autowired를 사용할 때의 경우의 수가 존재하는데 각각의 상황에 대해서 정리해보자.

[^2]: `@SpyBean`은 말그대로 Spy(스파이)입니다.\
    영화를 보면 한 조직에 스파이가 침투해서 여러 교란작업을 수행합니다.\
    스파이는 조직 전체에 퍼져있지 않고, 조직 구성원 중 1명 혹은 일부분입니다.\
    스파이외에 다른 조직원들은 모두 진짜 조직원입니다.

    `@MockBean`은 `given`에서 선언한 코드 외에는 전부 사용할 수 없습니다.\
    <mark style="background-color:yellow;">반면에</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`@SpyBean`</mark><mark style="background-color:yellow;">은</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`given`</mark><mark style="background-color:yellow;">에서 선언한 코드 외에는 전부 실제 객체의 것을 사용합</mark>니다.\
    이미 존재하는 Bean을 SpyBean으로 Wrapping한 형태라고 생각하시면 됩니다.

[^3]: MockMvc는 웹 어플리케이션을 애플리케이션 서버에 배포하지 않고 테스트용 MVC환경을 만들어 요청 및 전송, 응답기능을 제공해주는 유틸리티 클래스다.

[^4]: Mock은 껍데기만 있는 객체를 얘기합니다. 인터페이스의 추상메소드가 메소드 바디는 없고 파라미터 타입과 리턴타입만 선언된 것처럼, Mock Bean은 기존에 사용되던 Bean의 껍데기만 가져오고 내부의 구현 부분은 모두 사용자에게 위임한 형태입니다. 즉, 해당 Bean의 어떤 메소드가 어떤 값이 입력 되면 어떤 값이 리턴 되어야 한다는 내용 모두 개발자 필요에 의해서 조작이 가능합니다.

[^5]: WebMvcTest는 Controller가 정상적으로 작동하는지 테스트하는 것이기 때문에 Web과 관련된 의존성만을 가지고 온다.

    &#x20;

    WebMvcTest에서 가져오는 의존성들 즉, 다음 어노테이션들만 ComponentScan해서 가져온다.

    @Controller, @ControllerAdvice, @JsonComponent, Converter, GenericConverter, Filter, HandlerInterceptor

    &#x20;

    그렇기 때문에 Service, Repository등의 어노테이션을 컨트롤러에서 사용하고 있어도 가져와서 사용하지 않는다.

[^6]: TDD란 Test Driven Development의 약자로 ‘테스트 주도 개발’이라고 한다.

    반복 테스트를 이용한 소프트웨어 방법론으로 작은 단위의 테스트 케이스를 작성하고 이를 통과하는 코드를 추가하는 단계를 반복하여 구현한다.

[^7]: 1\. 먼저 실패하는 테스트 케이스를 작성합니다.\
    2\. 테스트 케이스를 통과하기만 하는 코드를 작성합니다.\
    3\. `2`의 과정을 완료한 코드를 보기 좋고 이해하기 용이하도록 다시 작성합니다 (리팩터; 코드개선). 리팩터 과정에서는 `2`에서 작성한 코드의 논리 흐름을 바꾸지 않습니다.\
    4\. 리팩터 과정에서 실패 테스트 케이스를 추가적으로 발견할 경우 `1`의 과정으로 돌아갑니다.\


    ![](<../.gitbook/assets/image (37).png>)
