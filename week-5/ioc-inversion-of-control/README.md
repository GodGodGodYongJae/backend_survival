# 🟥 IoC(Inversion of Control)

### 정의

제어의 역전 (IoC)란 소프트웨어 설계 원칙 중 하나로 프로그래밍에 있어, 객체의 생성 관리 책임을 개발자에서 전체 에플리케이션 또는 프레임워크에 위임하는 디자인 원칙을 일컫는다.



### 핵심

IoC의 핵심"아이디어는    "어떻게" 가 아니라 "누가" 객체의 생성 및 관리 책임을 가지냐에 있다.

즉, 우리는 어떻게 객체들이 생성되고 관리되는지 보다 누구에 의해서 생성되고 관리되는지에 초점을

맞출 필요가 있다.&#x20;



### 예시

```
// Some code
print "enter your name"
read name
print "enter your address"
read address
etc...
store in database
```

사용자가 입력한 변수를 read를 통해 받고, 정해진 순서에 따라 마지막에 사용자 정보를 입력하고 데이터 베이스에 저장하는 예시 코드다.



앞선 위 예시 코드는 IoC원칙을 지키지 않은 코드이며&#x20;

```
// Some code
when the user types in field a, store it in NAME
when the user types in field b, store it in ADDRESS
when the user clicks the save button, call StoreInDatabase
```

위 코드는 IoC원칙을 지켜 흔히 우리가 사용하는 GUI ( Windowing System)을 예로 들수 있다.

사용자가 filed a에 타이핑 했을 때 name을 저장한다. 여기서 핵심은 when the user types이다.

화면에 수 많은 기능들이 있겠지만 해당 기능을 언제 실행할지는 사용자가 결정한다.

