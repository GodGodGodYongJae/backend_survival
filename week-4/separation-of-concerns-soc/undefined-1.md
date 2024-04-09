# 응집도



<figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption><p><a href="https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4%EC%9D%98-%EA%B2%B0%ED%95%A9%EB%8F%84-%EC%9D%91%EC%A7%91%EB%8F%84-%EC%9D%98%EB%AF%B8%EC%99%80-%EB%8B%A8%EA%B3%84-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EC%89%BD%EA%B2%8C-%EC%A0%95%EB%A6%AC">https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4%EC%9D%98-%EA%B2%B0%ED%95%A9%EB%8F%84-%EC%9D%91%EC%A7%91%EB%8F%84-%EC%9D%98%EB%AF%B8%EC%99%80-%EB%8B%A8%EA%B3%84-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EC%89%BD%EA%B2%8C-%EC%A0%95%EB%A6%AC</a></p></figcaption></figure>

### 응집도란?

응집도는 한 모듈 내의 구성 요소간의 밀접한 정도를 의미한다. 한 모듈이 하나의 기능(책임)을 갖고 있는 것은 응집도가 높은 것이고, 한 모듈이 여러 기능을 갖고 있는 것은 응집도가 낮은 것이다.\
\
응집도가 높은 모듈은 하나의 모듈 안에 함수나 데이터와 같은 구성 요소들이 하나의 기능을 구현하기 위해 필요한 것들만 배치되어 있고 긴밀하게 협력한다.\
\
예를들어 쇼핑몰 프로젝트에서 주문 처리를 담당하는 클래스에서 회원의 정보를 업데이트하는 메서드가 있다면, 이건 응집도가 낮은 것이다. 회원 정보는 회원만 담당하는 클래스에서 따로 분리하여 처리하는 것이 옳기 때문이다.

{% hint style="info" %}
Tip\
응집도가 높은 클래스의 특징

* 단일 책임원칙을 잘 지킨 클래스
* 다른 클래스와 잘 협력하는 클래스
{% endhint %}



### 기능적 응집도 ( Functional Cohesion )

1. 가장 응집도가 높은 형태로 가장 좋은 형태
2. 모듈 내부의 모든 기능이 단일 목적을 위해 수행되는 경우
3. 대입 되는 변수가 공통적으로 사용되는 경우
4. 대표적으로 수학 연산에 관련된 모듈들을 모은 math 클래스를 들 수 있음

```java
// Some code
public class Stack {
	
    private int topOfStack = 0;
    private List<Integer> elements = new LinkedList<Integer>();
    
    public int size() {
    	return topOfStack;
    }
    
    public void push(int element) {
    	topOfStack++;
        elements.add(element);
    }
    
    public int pop() throws PoppedWhenEmpty {
    	if (topOfStack == 0) {
        	throw new PoppedWhenEmpty();
        }
        int element = elements.get(--topOfStack);
        elements.remove(topOfStack);
        return element;
    }
}
```

보통 메서드가 인스턴스 변수를 많이 사용하면 할 수록 메서드와 클래스는 응집도가 높아지는데, 위의 코드에서는 각 메서드 마다 인스턴스 변수를 이용해 자료를 업데이트 해줌으로써 응집도를 높였다.



### 순차적 응집도 ( Sequential Cohesion )

1. 모듈 내에서 한 활동으로 부터 나온 출력값이 다음 활동의 입력데이터로 사용할 경우
2. 어떤 모듈이 특정 파일을 읽고 처리하는 기능을 하는 등과 같다.

```java
// Some code
class Sequential {
    
    void processGrade(Grade grade) {
        String numberGrade = grade.getGrade(); // 어느 모듈의 출력값이
        String letterGrade = grade.computeLetter(numberGrade); // 바로 다음 입력값으로 이용
        grade.displayLetter(letterGrade); // 다시 전의 반환값이 바로 다음 입력값으로 이용
        // 앞의 값이 있어야 뒤의 모듈을 실행할 수 있기 때문에 처리 순서가 있음
        // 메소드의 리턴 된 결과가 다음 메소드의 입력 파라미터로 쓰이는 경우
	}
}
```

### 교환적 응집도 (Communication Cohesion)

1. 통신적 응집도라고 불림.
2. 동일한 입력과 출력을 사용하여 다른 기능을 수행하는 활동들이 모여있는 경우
3. 메소드 호출에 공통된 파라미터가 입력되는 경우
4. 순차적 응집도와 차이점은 대신에 처리 순서가 중요치 않다는 것.

```java
// Some code
class Communicational {

    void Compute_MatrixMatrix(Matrix marix) {
        int[][] aMatrix = marix.setGraph({ // 어느 모듈의 출력값이
        	{0, 0, 0}, 
            {0, 0, 0}
        });
        
        transform_matrix = marix.trans(aMatrix); // 바로 다음 입력값으로 이용 
        inverse_matrix = marix.inverse(aMatrix); // 바로 다음 입력값으로 이용 
        // 다만 앞의 값으로 서로 다른 기능의 모듈을 수행하는 것이기 때문에 모듈 처리 순서는 상관 없음
        // 메소드 호출에 공통된 파라미터가 입력
    }
}
```

첨언하자면,  파라메터 값이 같은데 처리 결과가 다른 메소드가 많은 경우를 의미하는 듯 하다.



### 절차적 응집도 ( Procedural Cohesion )

1. 모듈이 다수 관련 기능을 가질 때 모듈 안의 구성요소가 그 기능을 순차적으로 수행할 경우
2. 하나의 클래스에 있는 메소드들을 여러개 호출하는 경우

```java
// Some code
class Procedural extends Letter {

    void sendLetter() { 
    	// 하나의 클래스에 있는 메소드들을 여러 개 호출하는 경우
        this.writerBody();
        this.writerSalutation();
        this.send();
    }
}
```



### 시간적 응집도 ( Temporal Cohesion )

1. 일시적 응집도라고 불림
2. 각 기능 요소들이 순서에 상관없이 특정 시점에 반드시 수행되는 경우 ( Unity에서 Init , Start 함수 )
3. 연관된 기능이라기 보단 특정 시간에 처리되어야 하는 활동들을 한 모듈에서 처리할 경우
4. 메소드 호출이 일어나지 않고 변수의 초기화만 실행되거나 Exception 에러로그를 보내거나 등

```java
// Some code
class Temporal {
    int no_student;
    int no_department;
    String university_name;

    void Init_Variables() {
    	// 특정 시간에 처리되어야 하는 활동들을 한 모듈에서 처리 (변수 초기화)
        no_student = 0;
        no_department = 0;
        university_name = "Hongik University";
    }
}
```



### <mark style="color:red;">논리적 응집도 ( Logical Cohesion )</mark>

1. 유사한 성격을 갖거나 특정 형태로 분류되는 처리 요소들이 한 모듈에서 처리되는 경우&#x20;
2. 논리적으로 비슷한 기능을 수행하지만 서로의 관계는 밀접하지 않은 형태
3. switch 문이 쓰여 case 에 따라 비슷하지만 다른 작업을 수행하는 경우&#x20;

```java
// Some code
class Logical {
    public void solve_equation(int no_equ, long x) {
    	// switch문으로 논리적으로 분리된 기능을 수행하는 것처럼 보이지만, 서로 다른 모듈을 실행하는 관계가 없는 상태
        switch (no_equ) {
            case 1:
                // 모듈 실행
                break;
            case 2:
                // 또다른 모듈 실행
                break;
            case 3:
                // 또다른 또다른 모듈 실행
                break;
        }
    }
}
```

```java
// Some code
class SetProp {
	// height와 width 인스턴스 값을 동시에 설정하는 Setter 모듈
    public void setValue(String name, int value) {
    	// 기능 동작 자체로는 문제는 없지만, 하나의 메서드에서 전부 처리하는것보다, 각각의 메서드에 하나의 인스턴스를 처리하도록 짜는게 좋다.
        if ("height".equals(name)) {
            this.height = value;
        }
        if ("width".equals(name)) {
            this.width = value;
        }
    }
}
```

필자는사실상 응집도에 관련해선 해당 논리적 응집도를 발견하면 무조건 리팩토링을 한다. switch 문은 유지보수 때 어려움을 주며 하드코딩 된 저 부분도 어떻게든 고친다.
