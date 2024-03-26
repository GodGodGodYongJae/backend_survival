# 🟦 캡슐화와 정보은닉

정보은닉이란?

\-> 객체에 대한 구체적인 정보를 노출  시키지 않도록 하는 기법.

일단 소프트웨어 개발론에서 객체지향적 설계에 대한 이야기를 한 번쯤은 들어봤을 것이다.

소프트웨어에서의 유연성을 확보하는 단 한 가지 방법만 있다면, 그것은 객체(클래스)간에 서로를 모르게 한다는 것이다.\
\
간단히 풀어서 설명해보자면 1학년 1반 교실이 있고 해당 교실에는 3 명의 학생이 존재한다고 해보자.

철수와 영희 그리고 짱구가 해당 1학년 1반에 배정 받았을 때 교실의 입장에서 이 3명의 학생(객체)에 대한 정보를 사실 알 필요가 없다.  철수,영희,짱구 모두 영원히 1학년 1반에서 지낼 것이 아니기 때문에 교실에 대한 정보를 알 필요가 없다.\
\
간단히 교실은 3명의 학생 ( Student )가 존재하는 것만 알고 있으면 되고, 철수영희짱구는 현재 자신이 속한 교실(Class) 만 알고 있으면 된다.\
\
이게 뭔 소린가 싶을텐데.  서로를 모른다는 것은 서로의 코드에 상대 객체나 클래스에 대한 코드가 단 한줄도 없다는 의미이다. 만약 두 객체간에 전혀 관계가 없다면 어느 하나가 수정되거나 사라져도 다른 객체는

전혀 영향 받지 않는다. 따라서 두 객체간의 유연성이 확보된다.&#x20;

\
캡슐화란?

정보은닉의 개념 중 하나다.\
단순히 아까  예로 설명했던   교실 입장에서, 철수와영희 그리고 짱구에 대한 몸무게나 키 따위를 알 이유가 없다. 다만 졸업을 위해 나이를 알아야 한다면, 해당 철수와 영희 그리고 짱구에게 하나의 공통된 인터페이스를 만들어 알려주면 된다.   또,  철수와 영희 짱구의 장례희망을 알고 싶다고 하여도 공통된 인터페이스만\
알고 있으면 된다.&#x20;

위 두 개념을 간단히 코드로 표현해보자면 아래와 같다.

<figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>

위와 같이 classRoom에선, 철수 짱구 영희를 직접적으로 참조 받는 것이 아닌 그들을 공통적으로 묶은 student만 알면  되고, 그들의 장례희망 또한 각각 내부적으로 구현된 SpeakPlan을 구현해준 곳에서 알 수 있다.



또 classRoom에서 GetStudentsFuters라는 API를 통해 사용자가내부에서 어떻게 구현되었는지는 모르지만, 호출만하면 해당 모든 교실의 학생의 장례희망을 얻을 수 있다 .\
\