---
description: https://hudi.blog/data-transfer-object/
---

# 🟥 DTO(Data transfer Object)

DTO란 Data Transfer Object의 약자로 **계층 간 데이터 전송**을 위해 **도메인 모델** 대신 사용되는 객체이다

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

이 때 계층이란, Presentation(View, Controller) , Business ( Service) , Persistence ( DAO, Repository )등을 의미 한다.





> The difference between data transfer objects and business objects or data access objects is that a DTO does not have any behavior except for storage, retrieval, serialization and deserialization of its own data (mutators, accessors, parsers and serializers). In other words, DTOs are simple objects that should not contain any business logic but may contain serialization and deserialization mechanisms for transferring data over the wire.
>
> [_영문 위키피디아 - Data transfer object_](https://en.wikipedia.org/wiki/Data\_transfer\_object)

DTO는 순수하게 데이터를 저장하고 데이터에 대한 getter , setter만을 가져야 한다. 위키피디아에 \
따르면 DTO는 어떠한 비지니스 로직을 가져서는 안되며, 저장, 검색, **직렬화, 역직렬화** 로직만을 가져야 한다.



* 제대로 된 객체가 아니라 그냥 무기력한 데이터 덩어리. C/C++ 등에선 구조체(struct)로 구분할 수 있지만, Java에선 불가능. 최신 Java에선 record를 활용할 수 있지만, 오래된 Bean 관련 라이브러리에선 지원하지 않음.

### 도메인 모델 대신 사용하면 좋은 이유

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption><p><a href="https://martinfowler.com/eaaCatalog/dataTransferObject.html">https://martinfowler.com/eaaCatalog/dataTransferObject.html</a></p></figcaption></figure>

위 사진을 보면, 필요로 하는 데이터가 Album의 title과 artist의 이름 정도라면, 굳이 Album의 모든 데이터 정보나 Artist 의 모든 데이터 정보를 노출 시켜줄 필요가 없다. 이런 모든 데이터 모델 속성이 외부에 노출되면 보안문제가 발생할 수 있고,  또 그만큼 많은 데이터를 전달 해주다 보니 통신 비용이 그만큼 더 들어간다.\
\
또한, 도메인 모델을 계층간 전송에 사용하면 모델과 뷰가 강하게 결합될 수 있다. 뷰의 요구사항 변화로\
도메닌의 코드를 변경하는 것은 좋지 않다. DTO를 사용하면 이 결합을 느슨하게 만들 수 있다.\




### 사실 DTO는 안티 패턴이다.

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption><p><a href="https://martinfowler.com/bliki/AnemicDomainModel.html">https://martinfowler.com/bliki/AnemicDomainModel.html</a></p></figcaption></figure>

여기서 말하는 안티패턴은 무기력한 도메인 모델 또는[ 빈약한 도메인 모델(anemic domain model)](anemic-domain-model.md)이라고\
일컫는다. 왜 안티패턴인지는 anemic domain model 페이지에서 다루고 있다.
