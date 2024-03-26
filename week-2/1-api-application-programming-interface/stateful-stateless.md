---
description: >-
  https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-Stateful-Stateless-%EC%A0%95%EB%A6%AC
---

# 🟥 Stateful / Stateless

## StatleFul과 Stateless 의 차이점

Client가 Server간의 통신 상태를 유지 하냐 유지 하지 않느냐로 간단하게 정리 할 수 있다.



### Statleful

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p><a href="https://velog.io/@averycode/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-TCPUDP%EC%99%80-3-Way-Handshake4-Way-Handshake">https://velog.io/@averycode/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-TCPUDP%EC%99%80-3-Way-Handshake4-Way-Handshake</a></p></figcaption></figure>

말이 긴데, 간단하게 요약하자면 Client와 Server가 서로 데이터를 주고 받을 수 있는 상태까지의 과정을 \
3-WayHandShake라 요약할 수 있다.

그래서 Stateful 한게 무엇이냐?

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

위 이미지와 같이 서버에서 클라이언트의 정보를 메모리상으로 저장을 하고 있다가 다른 요청이 왔을 때,

이를 응답해서 알려준다.  문제는 위 이미지 2 처럼, 1번서버가 터졌을 때 모든 데이터가 다 날라가는 문제가 있다.



보통은 게임 서버에서 자주 쓰인다.

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption><p><a href="https://velog.io/@robolab1902/%EA%B2%8C%EC%9E%84%EC%84%9C%EB%B2%84%EC%97%90-Stateful%EC%9D%84-%EC%93%B0%EB%8A%94-%EC%9D%B4%EC%9C%A0">https://velog.io/@robolab1902/%EA%B2%8C%EC%9E%84%EC%84%9C%EB%B2%84%EC%97%90-Stateful%EC%9D%84-%EC%93%B0%EB%8A%94-%EC%9D%B4%EC%9C%A0</a></p></figcaption></figure>



### Stateless

앞에 설명한 Stateful과는 반대되는 개념으로 Client에서 해당 정보를 갖고 있다는 것이다.

그래서 이전 정보를 가질 수 없기 때문에 매번 Client에선 자신이 누군지를 알려줘야한다.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

그리고 핵심은 자신이 누군지를 알려주는 기술이 바로 JWT토큰이 될 수 있겠다.

