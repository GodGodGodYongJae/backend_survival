# 결합도

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption><p><a href="https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4%EC%9D%98-%EA%B2%B0%ED%95%A9%EB%8F%84-%EC%9D%91%EC%A7%91%EB%8F%84-%EC%9D%98%EB%AF%B8%EC%99%80-%EB%8B%A8%EA%B3%84-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EC%89%BD%EA%B2%8C-%EC%A0%95%EB%A6%AC">https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4%EC%9D%98-%EA%B2%B0%ED%95%A9%EB%8F%84-%EC%9D%91%EC%A7%91%EB%8F%84-%EC%9D%98%EB%AF%B8%EC%99%80-%EB%8B%A8%EA%B3%84-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EC%89%BD%EA%B2%8C-%EC%A0%95%EB%A6%AC</a></p></figcaption></figure>



### 결합도란?

결합도는 모듈 ( 클래스 파일) 간의 상호 의존 정도를 의미한다.\
예를 들면, 자동차에서 바퀴 모듈을 바꾼다고 했을 때, 핸들과의 의존성은 어느정도 생길 수 밖에 없다.\
다만, 바퀴를 교체 해야한다고 해서 핸들 까지 교체해야 된다면 이건 상식적으로 설계가 잘못 되었다고\
\
볼 수 있으며, 이러한 관점으로 프로그램을 설계할 때, 유지보수를  위해서  객체간의 결합도를 가능한 낮추어서 작업해야 한다.\


{% hint style="info" %}
Tip\
\[ 결합도가 낮은 클래스의 특징 ]

* Open Close Principle 의 원칙을 잘 지킨 클래스 ( 확장에는 열려있고 변경에는 닫혀 있음)
* 다형성을 잘 지킨 클래스
{% endhint %}



### 자료 결합도 ( Data Coupling)

1. 가장 결합도가 낮고, 가장 좋은 형태
2. 모듈끼리 단순히 데이터를 주고 받는 경우 ( 기능 수행에 있어서 로직을 제어하지 않고, 순수한 데이터를 주고 받는 것 )
3. 한 묘듈을 변경하더라도 다른 모듈에 영향을 끼치지 않는 결합 형태

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

```java
// Some codeclass 
Bill {
    // 주차 요금 청구서 모듈 (사용시간과 할인률을 인자로 받고 계산하여 주차요금 메소드를 호출)
    public static int getBillFee(int time, int discount) {
        double discountPercentage = discount / 100;
        
        // 메서드안에서 또 다른 메서드를 호출해 의존도가 있긴 하지만, 메서드에 단순 파라미터 데이터를 보내는 형태
        return Fee.calculateFee(time) * discountPercentage; 
    }
}

class Fee {
    // 주차 요금 계산 모듈
    public static int calculateFee(int time) {
        int defaultMoney = 1000;
        return defaultMoney * time; 
    }
}

public class Main {
	public static void main(String[] args) {
    	Bill.getBillFee(2, 80); // 2시간 이용, 80% 할인
    }
}
```



### 스탬프 결합도 ( Stamp Coupling )

1. 두 모듈이 인터페이스로 배열이나 오브젝트와 같은 동일한 자료 구조를 참조하는 형태
2. 만일 모듈에 쓰일 자료구조 형태가 변경되면 그것을 참조하는 모든 모듈에 영향을 주게 됨

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

```java
// Some code
// 이용기록 자료구조 형태
class Record {
	public int carNum;
    public int useTime
    private int fee
    
    Record(int carNum, int useTime) {
    	this.carNum = carNum;
        this.useTime = useTime;
    }
    
    public void setFee(int fee) {
    	this.fee += fee;
    }
    public int getFee(int fee) {
    	return this.fee;
    }
}

class BillFee {
    // 주차장 이용 청구서 작성 모듈
    public static int getBillFee(String name, int hour) {

        Record record = new Record(name, hour); // 자료구조 생성

        Bill.calculateFee(record); // 자료구조를 메서드에 넘김
        Fee.calculateFeeAnother(record); // 자료구조를 메서드에 넘김

        return record.getFee();
    }
}

class Bill {
    // 주차비용 계산 모듈
    public static void calculateFee(Record record) {
        int defaultMoney = 1000;
        record.setFee(defaultMoney * record.useTime); 
    }
}

class Fee {
    // 기타비용 계산 모듈
    public static int calculateFeeAnother(Record record) {
        int defaultMoney = 5000;
        record.setFee(defaultMoney * record.useTime); 
    }
}
```



### 제어 결합도 (Control Coupling)

1. 어떤 모듈이 다른 모듈 내부의 논리적인 흐름을 제어하는 제어요소를 전달하는 경우
2. 상위 모듈이 하위 모듈의 상세한 처리 절차를 알고 있어 이를 통제하는 경우
3. 제어 결합은 정보은닉을 위배하는 결합으로, 한 모듈이 다른 모듈 내부에 관여하여 관계가 복잡해짐

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

```java
// Some code
// 회원 정보 클래스
class User { ... }

class Bill {
    // 주차 요금 청구서 모듈
    public static int getBillFee(int time) {
        double discountPercentage = discount / 100;
        User user1 = new User();
		
        // 파라미터로 전달되는 값에 따라서 모듈 내부 로직의 처리가 달라지는 결합 형태
        return Fee.calculateFee(time, user.isJoin) * discountPercentage; 
    }
}

class Fee {
   // 주차 요금 계산 모듈
    public static int calculateFee(int time, boolean isJoin) {
        int defaultMoney = 1000;

        // 회원 여부에 따라 주차요금을 계산하는 로직이 달라지게 된다
        if(isJoin) {
            return defaultMoney * time - 400; // 회원 이면 400원 할인
        } else {
            // ...
        }
    } 
}
```



### 외부 결합도(External Coupling)

1. 모듈이 외부에 있는 다른 모듈의 데이터를 참조할 때의 결합도
2. 외부의 데이터, 통신 프로토콜 등을 공유할 때 발생 ( 참조할 데이터가 외부 모듈에 위치 )
3. 어떤 외부 모듈에서 반환한 값을 다른 모듈에서 참조하는 경우
4. 참조되는 데이터의 범위를 각 모듈에서 제한할 수 있다.

<figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

```java
// Some code
// 외부 모듈을 가져오기
import AddFee;

class Bill {
    // 주차 요금 청구서 모듈 
    public int getBillFee(int time, int discount, Addfee f) {
        double discountPercentage = discount / 100;
        return calculateFee(time, f) * discountPercentage + f.getPlusFee(); // 외부 모듈 f에 있는 데이터 참조
    }
}

class Fee {
    // 주차 요금 계산 모듈
    public int calculateFee(int time, Addfee f) {
        int defaultMoney = 1000;
        return defaultMoney * (time + f.getPlusTime); // 외부 모듈 f에 있는 데이터 참조
    }
}

public class Main {
    public static void main(String[] args) {
        int a = 1000;
        int b = 10;
        
        // 외부 모듈의 데이터를 결정하는 파라미터 a와 b를 넣어주고 외부 데이터를 반환
        Addfee addfee = new Addfee(a, b);
        getBillFee(2, 80, addfee); 
    }
}

```



### 공통 결합도 (Common Coupling)

1. 여러 개의 모듈이 하나의 공통 데이터 영역을 사용하는 결합도
2. 대표적으로 전역 변수 ( global variable)를 예로 들 수 있음
3. 공통 데이터 영역의 내용을 조금만 변경하더라도 이를 사용하는 모든 모듈에 영향을 미침
4. 위의 외부 결합도와 유사하게 볼 수 있으나, 공통 데이터가 외부냐 내부냐에 따라 차이가 있다.
5. 공통 결합도가 외부 결합도 보다 결합도가 높은 이유는 전역 변수의 값에 따라 결국은 외부의 모듈 반환 값 까지 결정 될 수 있는 가능성이 있기 때문

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

```java
// Some code
class Discount {
    public static int discount = 50; // 공통 전역 데이터
    public static int discountDefault = 500; // 공통 전역 데이터
}

class Bill {
    // 주차 요금 청구서 모듈
    public int getBillFee(int time) {
        double discountPercentage = Discount.discount / 100; // 공통 데이터 사용
        return calculateFee(time) * discountPercentage; 
    }
}

class Fee {
    // 주차 요금 계산 모듈
    public int calculateFee(int time) {
        int defaultMoney = 1000 - Discount.discountDefault; // 공통 데이터 사용
        return defaultMoney * time; 
    }
}
```



### 내용 결합도 ( Content Coupling )

1. 가장 높은 결합도를 갖으며 가장 좋지 않은 결합 형태
2. 어떤 모듈이 사용하려면 다른 모듈의 내부 기능과 데이터를 직접 참조해 그대로 가져와 사용하거나 수정 하는 경우
3. 이렇게 되면 A모듈 B모듈 모두 코드를 알고 있어야 하며, A 모듈이 변경되면 B모듈도 영향을 미쳐 변경 해야함.

### 정리 및   개인적인 견해

하지만 결합도가 높다고 해서, 모든 코드가 나쁘다고 할 수 없다. 물론 필자 또한, 결합도가 높은 코드는 가능한 지향하는 편이지만.\
\
이미 여러 개발론을 참고하고 직접 만들어보면서 공통 결합도엔, 게임에선 싱글톤이 사용되며 Spring도 내부적으로 Container를 통해 싱글톤으로 작동한다. 해당 싱글톤은 디자인 패턴 중 전역으로 접근하게 끔 하는데, 이러한 경우에도 결합도는 높지만 보편적으로 많이 사용하고 있으며 생산성에도 높은 이점을 가져다 준다. \
\
또한, 내용 결합도는 결합도가 가장 높아서 가장 지양해야하는 코드라지만, JPA\
에서 가령 Domain을 업데이트 할 때 Domain 내에서 처리하는 경우가 많기 때문에 \
\
이 또한 내용 결합도는 높지만 생산성에선 좋은 이점을 가져다 준다.\
\
다만 위와 같은 프레임워크를 사용하는 관점이 아닌 일반적인 코드를 작성할 땐 해당 결합도 여부를 가능한 줄이는 방법으론 인터페이스를 적극 활용하여 객체가 누군지 몰라도 인터페이스를 참조하는 형태로 개발한다면 결합도를 줄일 수 있는 방법으로 활용할 수 있다. <mark style="color:red;">**인터페이스만으로  참조하여 처리한다면**</mark> 확장에는 열려 있지만 변경에는 닫혀있으며 다형성 ( 하나의 객체가 여러 가지 타입을 가질 수 있음 )을 모두 지킬 수 있기 때문이다.

사실상 더 중요한 건 응집도 부분을 많이 신경 써야 할 것 같으며, 해당 부분은 응집도에서 정리하겠다.
