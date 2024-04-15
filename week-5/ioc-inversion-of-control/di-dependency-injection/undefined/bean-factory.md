# Bean Factory

### 정의

Spring Bean을 관리하는 Factory ( 객체를 직접 만들지 않고, 객체를 생성하는 책임만 가진 것 )



### 목적

앞서 설명한 싱글톤 패턴은 런타임 시, 싱글톤객체를 생성해주는데 Spring에선 이를 Bean을 통해 관리한다.

보통은 Bean에 대한 정보를 XML파일로 써줬는데 요즘엔 Annotation으로 처리한다 ( Component ) ( Component - Scan ) 따위로
