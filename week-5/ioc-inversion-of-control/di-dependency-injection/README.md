# 🟥 DI(Dependency Injection )

### 정의

의존 관계 주입이며, 의존 관계란 A가 B를 의존한다 이며 해당 이 추상적인 표현을 토비의 스프링에선 다음과 같이 정의한다.

{% hint style="info" %}
의존 대상 B가 변하면, 그것이 A에 영향을 미친다.
{% endhint %}

즉 B의 기능이 추가 또는 변경되거나 형식이 바뀌면 그 영향이 A에 미친다.



이러한 객체 지향 설계 관점에서 강한결합   때문에 OCP를 위반하게 되는데 이를 해결하기 위해

interface를 사용하여 결합을 느슨하게 풀어줄 수 있다.

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p><a href="https://www.martinfowler.com/articles/injection.html">https://www.martinfowler.com/articles/injection.html</a></p></figcaption></figure>

위 사진을 보면 MovieLister는 Movie Finder라는 인터페이스를 바라보고 있으며

해당 구현부 MovifinderImpl에서 실행할 구현체를 정의하여, 구현부를 MovieLister가 몰라도 되며 구현부가 다른걸로 바뀌어도 movieLister는 OCP원칙을 지킬 수 있다라는 것이다.



### 서비스 로케이터&#x20;

그럼, MovieFinder를 상속받은 객체 즉 구현부가 여러개라고 한다면 어떤형태로 movie Lister가 알 수 있을까?

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

여러가지 방법이 있겠지만, 보편적으로 [Singleton](undefined/)으로 등록해주고 런타임 때, 구현부를 하나 생성한 뒤.

불러오는 형태다

