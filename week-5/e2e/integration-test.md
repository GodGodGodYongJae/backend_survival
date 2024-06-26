# 🟦 Integration Test ( 통합 테스트 )

{% hint style="info" %}
Spring의 힘을 빌려서 테스트하는 건 IoC 컨테이너를 적극적으로 활용하고 싶거나, Spring Web MVC로 구현된 부분을 테스트하고 싶을 때, 즉 Spring에서 통합 테스트라고 부르는 경우다.
{% endhint %}

통합 테스트는 유닛 테스트와 비슷한데, 큰 차이점이 하나 있다. 유닛 테스트는 다른 컴포넌트들과 독립적인 반면 통합 테스트는 그렇지 않다.

예를 들자면 유닛 테스트에서 데이터베이스에 접근하는 코드는 실제 데이터 베이스와 통신하는 것은 아니지만, 통합 테스트는 실제 통신해야 한다.

통합 테스트는 유닛 테스트만으로 충분하다고 느끼지 못할 때 사용된다.

때때로 두 개의 다른 분리된 시스템끼리 잘 통신하고 있는지 증명하고 싶을 때가 있는데(예를 들어 나의 앱과 데이터 베이스가 제대로 상호작용하고 있는지...) 이것을 통합 테스트라 한다.

통합 테스트는 대게 유닛 테스트를 작성하는 것보다 복잡하고 오랜 시간이 걸린다. (데이터베이스를 세팅할 때, 설정 파일을 읽어 오는 과정이라던가 데이터베이스가 잘 세팅되었는지 확인하는 과정이라던가)

따라서 통합 테스트가 꼭 필요한 것이 아니면 유닛 테스트를 작성하는데 집중하는 것이 좋다.
