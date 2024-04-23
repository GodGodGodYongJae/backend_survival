# 🟥 #1 HTTP의 이해

## [**HTTP** ](#user-content-fn-1)[^1] **(HyperText Transfer Protocol)**

<figure><img src="../.gitbook/assets/image (8) (1).png" alt=""><figcaption><p><a href="https://developer.mozilla.org/ko/docs/Web/HTTP">https://developer.mozilla.org/ko/docs/Web/HTTP</a></p></figcaption></figure>

요약하자면,<mark style="background-color:orange;">**하이퍼 미디어(HyperText)를 전송하는 (Transper) 규약(**</mark>[<mark style="background-color:orange;">**Protocol**</mark>](#user-content-fn-2)[^2]<mark style="background-color:orange;">**)**</mark> 이다.

하이퍼 미디어(Hypermedia)란 문자와 숫자와 같은 텍스트외에도 그림 애니메이션 등 다양한\
정보매체를 곧바로 접근할 수 있도록 표현하는 기능을 말한다.\
\
왜 나왔을까에 대한 근본적인 이유는, 여러가지가 있겠지만 필자의 생각엔 물리적인 기록 방법 예를 들어 \
공책에 필기를 하게 되면, 공간적 문제, 시간에 따른 유지비용 등 실물세상에서 산재하는 기록방법을\
공간적 제한이 없는  온라인상으로 영구  지속적으로 보존 및 공유할 수 있다는 장점이 있기 때문에 \
탄생했다고 본다.



여하튼, <mark style="background-color:orange;">**이러한 하이퍼 미디어를 온라인상으로 전송 또는 받기 위해선 몇  가지 규약 사항을 지켜야하고**</mark>\ <mark style="background-color:orange;">**이를 HTTP라 일컫는다.**</mark>



그럼 지켜야 하는 규약 사항이 무엇일까?

### Protocol과 OSI

우선, 왜 굳이 Protocol을 지키며 통신을 해야하는지 의문이 들 수있다.\
하지만 간단하게 예를들어 생각해보면  간단하다. 우리가 누군가와 통화를 하기 위해선 상대방의 번호를 \
입력해야 한다. 또 문자를 하기 위해선 번호와 보낼 내용을 입력해야한다.\
\
굳이 어렵게 생각하지 않아도 일상생활에서 우린 통신규약을 지키며 상대방과 문자나 목소리를 전달한다.

만약 통신규약을 어기고, 전화번호를 입력할 때 왜 010 과 같은 번호를 입력 해야하는지. 전화번호에 왜 ABCD-EFGH 와 같은 영어문자로된 번호로는 전화를 할 수 없는지에 대한 생각을 하면, 단순하게 이미 그렇게 누군가가  만들었고 우린 그걸 편하게 사용할 뿐이다. 물론 필자나 당신이 ABCD-EFGH로 통화가 가능한\
새로운 통신규약을 만들었다고 쳐도, 이미 대부분의 모든 사람이 010과 같은 숫자로된 번호로 통신규약을지키고 있기 때문에 만들어봐야 제대로 쓰이질 못한다.



이와 같이, <mark style="background-color:orange;">**하이퍼 미디어를 온라인상으로  통신하기  위해선, Protocol을 지켜야한다.**</mark>\
그리고 아까와 같이 문자나 전화를 예시로 든 것 처럼, 어떤 통신을하냐에 따라 Protocol이 달라진다.

### OSI

<figure><img src="../.gitbook/assets/image (4) (1) (1) (1) (1).png" alt=""><figcaption><p><a href="https://ko.wikipedia.org/wiki/OSI_%EB%AA%A8%ED%98%95">https://ko.wikipedia.org/wiki/OSI_%EB%AA%A8%ED%98%95</a></p></figcaption></figure>

일단 정의는 위 사진과 같다. 하지만 설명이 조금 어려우니 쉽게 풀어 설명해보겠다.\
우선 Protocol을 언급하였듯, 하이퍼 미디어를 온라인상 주고 받기 위해선 통신규약을 지켜야한다고 했다.\
\
하지만, OSI 계층은 그 이전의 문제를 조금 깊이 있게 다룬다고 생각해야한다.

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption><p><a href="https://shlee0882.tistory.com/110">https://shlee0882.tistory.com/110</a></p></figcaption></figure>

#### 물리계층 (Physical layer)

먼저 <mark style="background-color:orange;">**컴퓨터는 0과 1로 통신을 한다. 더 깊게 설명하면 전기 신호를 보내면 1, 보내지 않으면 0으로**</mark>\ <mark style="background-color:orange;">**인식하며 이것만으로도 다른 컴퓨터와 통신이 가능하다.**</mark>

<mark style="background-color:orange;">**이를 OSI 계층 구조에선 물리 계층이라고 부른다.**</mark>

<figure><img src="../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption><p><a href="https://www.youtube.com/watch?v=1pfTxp25MA8">https://www.youtube.com/watch?v=1pfTxp25MA8</a></p></figcaption></figure>

위 사진에서의 핵심은, 두 대의 컴퓨터가 서로 통신할려면, 전선을 연결하고 주파수를 통해 통신을 할 수 있는데 이 주파수의 범위가 0\~무한대의 Hz를 가지기 때문에 이러한 전기신호를 통과시킬 수 있는 전선이\
물리적으로 존재하지 않고, **이걸 아날로그 신호로 변화하여 이를 전선을 통해 보내고 다시금 수신받는**\
**쪽에서 해석하여 데이터를 주고 받을 수 있다**. \
\
이를 요약하자면 아래와 같다.

* 0과 1의 나열을 아날로그 신호로 바꾸어 전선으로 흘려보낸다 ( Encoding)
* 아날로그 신호가 들어오면 0과 1의 나열로 해석한다 ( Decoding )
* 물리적으로 연결된 두 대의 컴퓨터가 0과 1의 나열을 주고 받을 수 있게 된다.

실제로 사용되는 곳은 하드웨어적으로 구현이 되어있다.

#### 데이터 링크계층(Data Link Layout)

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

1계층에선, 두 대의 컴퓨터만 통신이 가능했다라고 한다면 여러 대의 컴퓨터가 통신을 하기 위해선\
라우터와 같은 스위치가 필요하다. 이에 대한 자세한 설명은 참고 영상을 확인해주길 바라며, 이 계층에서의**핵심은 여러대의 컴퓨터가 동시에 데이터를 보냈을 때, 섞이지 않고 누가 어떤 걸 보냈는지 알기 위해 만들어졌다고 볼 수 있다.**

<figure><img src="../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

어떻게 누가  어떤   데이터를 보냈는지를    구분하는 방법은 위 사진과 같이 구분자를 넣고 데이터를 넣는데\
좀 더 깊게 다루자면&#x20;

<figure><img src="../.gitbook/assets/image (7) (1).png" alt=""><figcaption><p><a href="https://blog.naver.com/lunarispars/221436602441">https://blog.naver.com/lunarispars/221436602441</a></p></figcaption></figure>

위 사진과 같이 MAC주소나 크기나 데이터등을 보내어 구분한다. MAC에 대해선 너무 많은 내용을 다루고 있기 때문에 우선은 누가 보냈는지 어디까지 보냈는지를 구분 할 수 있는 정도라 생각해두자.

#### 네트워크 계층

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Data Link Layer 계층까진 라우터 즉, 물리적으로 라우터와전선이 연결이 가능한 공간에서의 통신이

가능하다. 하지만 저 멀리 외국에 있는 B의 컴퓨터와 통신을 하기 위해선, 위 사진과 같이 Data 앞에

각 컴퓨터들이 갖고 있는 고유한 IP주소를 붙여 보내야 한다.

결국 NetworkLayer의 핵심은 아래와 같다.

* IP주소를 이용해서 길을 찾고 ( Routing )
* 자신 다음의 라우터에게 데이터를 넘겨주는 것  ( Forwarding  )

#### Transport Layer

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

전송 계층은 간단하게 실행된여러 프로세스 중  어느 곳에 데이터를 적용해야할지 등을 Port를 통해  넣어준다.

<figure><img src="../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

현재에 이르러서는 OSI 모델을사용하지 않고 TCP/IP 모델을 사용한다.  그리고 5계층과 6계층이

7계층에 통합된걸 볼 수 있다.



Application Layer

그리고 7계층이 바로 앞서 설명했던 HTTP와 같은 프로토콜을 통해, 웹 상에서 하이퍼텍스트를 서로 주고 받을 수 있게 된다.

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p><a href="https://developer.mozilla.org/ko/docs/Web/HTTP/Overview">https://developer.mozilla.org/ko/docs/Web/HTTP/Overview</a></p></figcaption></figure>

[^1]: 

[^2]: 컴퓨터 내부에서, 또는 컴퓨터 사이에서 데이터의 교환 방식을 정의하는 규칙 체계\
    기기 간 통신은 교환되는 데이터의 형식에 대해 상호 합의를 요구합니다. 이런 형식을 정의하는 규칙의 집합을 프로토콜이라고 합니다.
