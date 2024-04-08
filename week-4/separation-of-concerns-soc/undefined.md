# 결합도

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption><p><a href="https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4%EC%9D%98-%EA%B2%B0%ED%95%A9%EB%8F%84-%EC%9D%91%EC%A7%91%EB%8F%84-%EC%9D%98%EB%AF%B8%EC%99%80-%EB%8B%A8%EA%B3%84-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EC%89%BD%EA%B2%8C-%EC%A0%95%EB%A6%AC">https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4%EC%9D%98-%EA%B2%B0%ED%95%A9%EB%8F%84-%EC%9D%91%EC%A7%91%EB%8F%84-%EC%9D%98%EB%AF%B8%EC%99%80-%EB%8B%A8%EA%B3%84-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EC%89%BD%EA%B2%8C-%EC%A0%95%EB%A6%AC</a></p></figcaption></figure>



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

