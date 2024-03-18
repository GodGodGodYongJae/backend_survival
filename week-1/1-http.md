# 🟥 #1 HTTP의 이해

## [**HTTP** ](#user-content-fn-1)[^1] **(HyperText Transfer Protocol)**

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p><a href="https://developer.mozilla.org/ko/docs/Web/HTTP">https://developer.mozilla.org/ko/docs/Web/HTTP</a></p></figcaption></figure>

요약하자면,<mark style="background-color:orange;">**하이퍼 미디어(HyperText)를 전송하는 (Transper) 규약(**</mark>[<mark style="background-color:orange;">**Protocol**</mark>](#user-content-fn-2)[^2]<mark style="background-color:orange;">**)**</mark> 이다.

하이퍼 미디어(Hypermedia)란 문자와 숫자와 같은 텍스트외에도 그림 애니메이션 등 다양한\
정보매체를 곧바로 접근할 수 있도록 표현하는 기능을 말한다.\
\
왜 나왔을까에 대한 근본적인 이유는, 여러가지가 있겠지만 필자의 생각엔 물리적인 기록 방법 예를 들어 \
공책에 필기를 하게 되면, 공간적 문제, 시간에 따른 유지비용 등 실물세상에서 산재하는 기록방법을\
공간적 제한이 없는  온라인상으로 영구  지속적으로 보존 및 공유할 수 있다는 장점이 있기 때문에 \
탄생했다고 본다.



여하튼, <mark style="background-color:orange;">**이러한 하이퍼 미디어를 온라인상으 전송 또는 받기위해선 몇  가지 규약 사항을 지켜야하고**</mark>\ <mark style="background-color:orange;">**이를 HTTP라 일컫는다.**</mark>



그럼 지켜야 하는 규약 사항이 무엇일까?

### Protocol과 OSI



[^1]: 

[^2]: 컴퓨터 내부에서, 또는 컴퓨터 사이에서 데이터의 교환 방식을 정의하는 규칙 체계\
    기기 간 통신은 교환되는 데이터의 형식에 대해 상호 합의를 요구합니다. 이런 형식을 정의하는 규칙의 집합을 프로토콜이라고 합니다.
