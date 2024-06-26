# Entity Relationship Model

## Entity

ER 모델에서 Entity는 개별적으로 다룰 수 있는 데이터를 의미한다.

OOP Class와 유사하지만  차이점이라고 한다면 OOP,DDD에서 Entity는 연속성과 식별성이 있는 객체를 의미한다. 즉 무슨 말이냐. &#x20;

### OOP,DDD에서 의미하는 Entity

고양이라는 Entity가 있으면, 그 밑에 점박이 고양이, 턱시도 고양이와 같이 여러 종류의 Entity ( 연속성,식별성 )이 강조된다.&#x20;

### ER 에서의 Entity

id 1004, name : 점박이 고양이 라는 Tuple이 존재한다면 name의 속성 값이 바뀌어도 즉 턱시도 고양이라 바뀌어도 이 Entity는 identifire가 1004 그대로이기 때문에 같은 것으로 취급한다.



### 무슨 차인가?

좀 더 쉽게 풀어 설명하면 ER에서 예시로 든 건 고양이라는 Table에 Id별로 Entity를 구분하고

OOP , DDD에선 객체의 타입으로 구분한다고 볼 수 있다. 고양이라는 객체를 상속 받은 점박이 고양이는

할당할 때 마다 새로운 객체 ( Entity ) 가 생성이 되고 이를 턱시도 고양이로 갑자기 객체 자체를 바꿔 줄순 없다.



### Entity Relation Ship Diagram ( ERD )

논리적 설계에 들어가기 전 그리는 설계도 개념.

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption><p><a href="https://commons.wikimedia.org/wiki/File:ER_Diagram_MMORPG.png">https://commons.wikimedia.org/wiki/File:ER_Diagram_MMORPG.png</a></p></figcaption></figure>

위 이미지와 같이 Account와 Character의 관계를 나타내는 것을 의미함.

