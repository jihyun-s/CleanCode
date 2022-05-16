# Clean Code

## 2장 의미있는 이름 
### 1. 나쁜 코드
    - 성능이 나쁜 코드 : 불필요한 연산이 들어가서 개선의 여지가 있는 코드
    - 의미가 모호한 코드 : 이해하기 어려운 코드. 네이밍과 그 내용이 다른 코드 
    - 중복된 코드 : 비슷한 내용인데 중복되는 코드 

    (-) 깨진 유리창처럼 계속 나쁜 코드가 만들어지도록 한다.
    (-) 생산성 저하 (기술부채)
    (-) 새로운 시스템을 만들어야 한다. (현시스템 유지보수 어렵기 때문)


### 2. 클린 코드
    - 성능이 좋은 코드
    - 의미가 명확한 코드 = 가독성이 좋은 코드
    - 중복이 제거된 코드


### 3. 의미 있는 이름 짓기 
    - 루프 속 i j k 사용하지 않기 (advanced for문으로 대체, lamda 사용, 맥락에 맞는 이름 사용) 
    - 통일성 있는 단어 사용하기 
    - 변수명에 타입 넣지 않기 
    
    
### 4. Google Java Naming Guide
    - Package Naming Guide : All lover case, no underscores
    - Class Naming Guide : UppderCamelCase (대문자로 시작) 
        - 클래스는 명사, 명사구
        - 인터페이스는 명사, 명사구, (형용사) 
        - 테스트 클래스는 Test로 끝나기 
    - Method Naming Guide : LowerCamelCase (소문자로 시작) 
        - 메서드는 동사, 동사구 
        - jUnit 테스트에 underscore 사기도 함 


## 3장 함수 

### 1. SOLID
    - SRP (단일 책임 원칙) : 한 클래스는 하나의 책임만 가져야 한다.
        - 클래스는 하나의 기능만 가지며, 어떤 변화에 의해 클래스를 변경해야 하는 이유는 오직 하나뿐이어야 한다. 
        - SRP 책임이 분명해지기 때문에, 변경에 의한 연쇄작용에서 자유로워질 수 있다. 
        - 가독성 향상과 유지보수가 용이해진다. 
        - 실전에서는 쉽지 않지만 늘 상기해야 한다. 
        
    - OCP (개방-폐쇄 원칙) :  소프트웨어 요소는 확장에는 열려 있으나 변경에는 닫혀 있어야 한다. 
        - 변경을 위한 비용은 가능한 줄이고, 확장을 위한 비용은 가능한 극대화 해야 한다. 
        - 요구사항의 변경이나 추가사항이 발생하더라도, 기존 구성요소에는 수정이 일어나지 않고, 기존 구성 요소를 쉽게 확장해서 재사용한다. 
        - 객체지향의 추상화와 다형성을 활용한다. 
        
    - LSP (리스코프 치환 원칙) : 서브 타입은 언제나 기반 타입으로 교체할 수 있어야 한다. 
        - 서브 타입은 기반 타입이 약속한 규약(접근제한자, 예외 포함)을 지켜야 한다. 
        - 클래스 상속, 인터페이스 상속을 이용해 확장성을 획득한다. 
        - 다형성과 확장성을 극대화하기 위해 인터페이스를 사용하는 것이 더 좋다. 
        - 합성(composition)을 이용할 수도 있다. 
        
    - ISP (인터페이스 분리 원칙) : 자신이 사용하지 않는 인터페이스는 구현하지 말아야 한다. 
        - 가능한 최소한의 인터페이스만 구현한다. 
        - 만약 어떤 클래스를 이용하는 클라이언트가 여러 개고, 이들이 클래스의 특정 부분만 이용한다면, 여러 인터페이스로 분류하여 클라이언트가 필요한 기능만 전달한다. 
        - SRP가 클래스의 단일 책임이라면, ISP는 인터페이스의 단일 책임 
        
    - DIP (의존성 역전 원칙) : 상위 모델은 하위 모델에 의존하면 안 된다. 둘 다 추상화에 의존해야 한다. 추상화는 세부사항에 의존해서는 안 된다. 세부 사항은 추상화에 따라 달라진다.
        - 하위 모델의 변경이 상위 모듈의 변경을 요구하는 위계관계를 끊는다. 
        - 실제 사용관계는 그대로이지만, 추상화를 매개로 메시지를 주고 받으면서 관계를 느슨하게 만든다. 
    
    
### 2. 간결한 함수 작성하기
    - 작게 쪼갠다. 
    - 함수 내 추상화 수준을 동일하게 맞춘다. 
    - 한 가지만 하기(SRP), 변경에 닫게 만들기(OCP) : 계산과 타입관리를 분리, 타입에 대한 처리는 최대한 Factory에서만 
    - 함수 인수 : 인수의 갯수는 0~2개가 적당하다. 3개 이상인 경우에는 객체를 인자로 넘기기 
    
### 3. 안전한 함수 작성하기 
    - 부수 효과(Side Effect) 없는 함수 : 값을 반환하는 함수가 외부 상태를 변경하는 경우 

### 4. 함수 리팩터링 
    - 기능을 구현하는 서투른 함수를 작성한다. (길고, 복잡하고, 중복도 있다.) 
    - 테스트 코드를 작성한다. (함수 내부의 분기와 엣지값마다 빠짐없이 테스트하는 코드를 짠다.) 
    - 리팩터링한다. (코드를 다듬고, 함수를 쪼개고, 이름을 바꾸고, 중복을 제거한다.) 
    

## 4장 주석

### 1. 주석을 최대한 쓰지 말자
    - 주석은 나쁜 코드를 보완하지 못한다. 
        - 코드에 주석을 추가하는 일반적인 이유는 코드 품질이 나쁘기 때문이다. 
        - 코드로도 의도를 표현할 수 있다. (ex. 의미있는 이름으로 짓기)
    - 주석은 방치된다.
        - 코드의 변화에 따라가지 못하고, 주석은 방치된다. 
        - 코드는 컴파일되어 호출되지만, 주석은 그저 주석이기 때문에 그 자리에 방치되고 결국 의미없는 텍스트가 되어버린다. 

### 2. 좋은 주석
    - 구현에 대한 정보를 제공한다. 
    - 의도와 중요성을 설명한다. 
    - TODO : 앞으로 할 일. 지금은 해결하지 않지만 나중에 해야할 일을 미리 적어줄 때. 
    - FIXME : 문제가 있지만, 당장 수정할 필요는 없을 때. 가능하면 빨리 수정하는게 좋다.  

### 3. 주석보다 annotation 
    - annotation = 코드에 대한 메타 데이터
    - 코드의 실행 흐름에 간섭을 주기도 하고, 주석처럼 코드에 대한 정보를 줄 수 있다. 
        - @Deprecated : 컴파일러가 warning을 발생시킴. IDE에서 사용시 표시됨
        - @NotThreadSafe : Thread Safe하지 않음을 나타냄

### 4. JavaDoc
    - Java 코드에서 API문서를 HTML 형식으로 생성해주는 도구 
    /**
    * This is a Javadoc
    */
    
    
## 5장 형식 맞추기

### 1. 포맷팅이 중요한 이유
    - 가독성에 필수적이다

### 2. 클린코드 포맷팅 
    - 적절한 길이 유지 (~200라인, <500라인)
        - 200라인을 넘억나다면 클래스가 여러 일을 하고 있을 수 있다. SRP 위배 
    - 밀접한 개념은 서로 가까이 둔다 
        - 행 묶음은 완결된 생각 하나를 표현하기 때문에 개념은 빈 행으로 분리한다.
        - 변수는 사용되는 위치에서 최대한 가까이 선언한다. 

### 3. Java Class Declarations 
    - Class 내부 코드 순서
        1. static 변수 : public -> protected -> package -> private 순서 
        2. instance 변수 : public -> protected -> package -> private 순서
        3. 생성자 
        4. 메서드 : public 메서드에서 호출되는 private 메서드는 그 아래에 둔다. 가독성 위주로 그룹핑한다. 

### 4. Team Coding Convention
    - 팀의 코딩 스타일에 관한 약속
    - 참고
        - Google Java Style Guide : https://google.github.io/styleguide/javaguide.html
        - Naver Hackday Java Convention : https://naver.github.io/hackday-conventions-java/


## 6장 객체와 자료구조 

### 1. 자료구조 vs 객체
    - 자료구조(Data Structure) 
        - 데이터 그 자체 
        - 자료를 공개한다. 
        - 변수 사이에 조회 함수와 설정 함수로 변수를 다룬다고 객체가 되지 않는다. (getter, setter) 
        
    - 객체(Object)
        - 비즈니스 로직과 관련
        - 자료를 숨기고, 추상화한다. 자료를 다루는 함수만 공개한다.
        - 추상 인터페이스를 제공해 사용자가 구현을 모른 채 자료의 핵심을 조작할 수 있다.
        
    - 상황에 맞는 선택을 하면 된다.
        - 자료구조를 사용하는 절차적인 코드는 기본 자료구조를 변경하지 않으면서 새 함수를 추가하기 쉽다. 
        - 절차적인 코드는 새로운 자료구조를 추가하기 어렵다. 그러려면 모든 함수를 고쳐야 한다. 
        - 객체지향 코드는 기존 함수를 변경하지 않으면서 새 클래스를 추가하기 쉽다. 
        - 객체지향 코드는 새로운 함수를 추가하기 어렵다. 그러려면 모든 클래스를 고쳐야 한다. 

### 2. 객체 - 디미터 법칙
    - 클래스 C의 메서드 f는 다음과 같은 객체의 메서드만 호출해야 한다.
        - 클래스 C
        - 자신이 생성한 객체 
        - 자신의 인수로 넘어온 객체 
        - C 인스턴스 변수에 저장된 객체 
<img src="https://github.com/jihyun-s/CleanCode/blob/main/object.png" width="55%" height="55%"></img>

### 3. DTO 
    - Data Transfer Object = 자료구조 
    - 다른 계층 간 데이터를 교환할 때 사용
        - 로직없이 필드만 갖는다. 
        - 일반적으로 클래스명이 Dto(or DTO)로 끝난다. 
        - getter/setter를 갖기도 한다. 
        
    * Beans 
    Java Beans : 데이터 표현이 목적인 자바 객체 
        - 멤버 변수는 private 속성이다. 
        - getter와 setter를 가진다.

### 4. Active Record 
    - Database row를 객체에 맵핑하는 패턴 
        - 비즈니스 로직 메서드를 추가해 객체로 취급하는 건 바람직하지 않다. 
        - 비즈니스 로직을 담으면서 내부 자료를 숨기는 객체는 따로 생성한다. 
        - 하지만 객체가 많아지면 복잡하고, 가까운 곳에 관련 로직이 있는 것이 좋으므로 현업에서는 Entity에 간단한 메서드를 추가해 사용한다. 
    
    * Active Record
        - 객체가 row를 담을 뿐 아니라 database에 대한 접근을 포함한다. 
        - Person의 속성을 담을 뿐 아니라, 생성,수정도 객체 안에서 수행할 수 있다. 
    
    * Data Mapper 
        - row를 담는 객체와 database에 접근할 수 있는 객체가 분리되어 있다. 
        - Person은 값만 담고 있고, 생성, 수정 등 액션은 Person Mapper에서 담당한다. 
        
## 7장 우아하게 예외 처리하기 

### 1. 예외 처리 방식
    - 오류 코드를 리턴하지 말고, 예외를 던져라 (명확하고 처리흐름이 깔끔해진다.) 
        1. 오류가 발생한 부분에서 예외를 던진다. (별도의 처리가 필요한 예외라면 checked exception으로 던진다.) 
        2. checked exception에 대한 예외처리를 하지 않는다면 메서드 선언부에 throws를 명시해야 한다. 
        3. 예외를 처리할 수 있는 곳에서 catch하여 처리한다.

### 2. Unchecked Exception을 사용하라
    - Checked vs Unchecked Exception 
        - Exception을 상속하면 Checked Exception : 명시적인 예외처리가 필요하다. (ex. IOException, SQLException) 
        - RuntimeException을 상속하면 UncheckedException : 명시적인 예외처리가 필요하지 않다. 
        (ex. NullPointerException, IllegalArgumentException, IndexOutOfBoundException) 
        
    - Exception에 관한 규약 
        - Error 클래스를 상속해 하위 클래스를 만드는 일은 자제하자 
        - 사용자가 직접 구현하는 unchecked throwable은 모두 RuntimeException의 하위 클래스여야 한다 
        - Exception, RuntimeException, Error를 상속하지 않는 throwable은 절대로 사용하지 말자 
    
    - Checked Exception이 나쁜 이유
        1. 특정 메서드에서 checked exception을 throw하고 상위 메서드에서 그 exception을 catch한다면 
          모든 중간단계 메서드에 exception을 throws 해야 한다 
        2. OCP(개방 폐쇄 원칙) 위배 
          상위 레벨 메서드에서 하위 레벨 메서드의 디테일에 대해 알아야 하기 때문에 OCP 원칙에 위배된다. 
        3. 필요한 경우 checked exception을 사용해야 되지만 일반적인 경우 득보다 실이 많다. 

### 3. Exception 잘 쓰기 
    - 예외에 메시지 담기 
        - 오류가 발생한 원인과 위치를 찾기 쉽도록, 예외를 던질 때는 전후 상황을 충분히 덧붙인다. 
        - 실패한 연산 이름과 유형 등 정보를 담아 예외를 던진다. 
    
    - exception wrapper : 예외를 감싸는 클래스를 만든다. 
        - port.open() 시 발생하는 checked exception들을 감싸도록 port를 가지는 LocalPort 클래스를 만든다. 
        - port.open()이 던지는 checked exception들을 하나의 PortDeviceFailure exception으로 감싸서 던진다. 
        

### 4. 실무 예외 처리 패턴 
    - getOrElse : 예외 대신 기본값을 리턴한다
        1. null이 아닌 기본값 : 복수형의 데이터를 가져올 때는 데이터 없음을 의미하는 컬렉션을 리턴. (size 0) 
        2. 도메인에 맞는 기본값
        
    - getOrElseThrow : null 대신 예외를 던진다 (기본값이 없다면) 
        - 데이터를 제공하는 쪽에서 null 체크를 하여, 데이터가 없는 경우엔 예외를 던진다. 
        호출부에서 매번 null 체크를 할 필요 없이 안전하게 데이터를 사용할 수 있다. 
        
    - 파라미터의 null을 점검하라 
        - null을 리턴하는 것도 나쁘지만 null을 메서드로 넘기는 것은 더 나쁘다.
        - null을 메서드의 파라미터로 넣어야 하는 API를 사용하는 경우가 아니면 null을 메서드로 넘기지 마라.
        - null을 파라미터로 받지 못하게 한다. (unchecked exception, assert 사용 등) 

    - 자신의 예외를 정의한다. 
        - 에러 로그에서 stacktrace 해봤을 때 우리가 발생시킨 예외라는 것을 바로 인지할 수 있다. 
        - 다른 라이브러리에서 발생한 에러와 섞이지 않는다. 
        IllegalArgumentException을 던지는 것보다 우리 예외로 던지는게 어느 부분에서 에러가 났는지 파악하기에 용이하다.
        - 우리 시스템에서 발생한 에러의 종류를 나열할 수 있다. 


## 8장 경계 

### 1. 경계란
    - 우리가 만든 코드에 외부에서 들어온 코드를 병합해야 한다. 
    - 외부 코드는 외부에서 만든 코드인데, 외부 시스템과 호출하거나 단순히 외부에서 만들어진 코드일 수 있다. 
    - 우리 코드와 외부 코드를 깔끔하게 통합시키기 위해 경계를 잘 지어야 한다. 

### 2. 경계 짓기 (1) 우리 코드를 보호하기 
    - 캡슐화(Encapsulation) : 객체의 실제 구현을 외부로부터 감추는 방식 

### 3. 경계 짓기 (2) 외부 코드와 호환하기 
    - Adapter 패턴
        - 외부 코드를 호출할 때, 우리가 정의한 인터페이스대로 호출하기 위해 사용하는 패턴 

### 4. 외부 라이브러리 테스트하기 - Learning Test 
    - 학습 테스트는 이해도를 높인다. 
    - 외부 코드의 버전이 변경됐을 때, 우리 코드와 호환되는지 확인할 수 있다. 
    

## 9장 깨끗한 테스트 코드

### 1. 테스트 코드의 중요성 
    - 테스트 코드는 실수를 바로 잡아준다. 
    - 테스트 코드는 반드시 존재해야하며, 실제 코드 못지 않게 중요하다. 
    - 테스트 케이스는 변경이 쉽도록 한다. 코드에 유연성, 유지보수성, 재사용성을 제공하는 버팀목이 단위테스트다. 
    테스트 케이스가 있으면 변경이 두렵지 않다. 테스트 케이스가 없다면 모든 변경이 잠정적인 버그다. 
    - 지저분한 테스트 코드는 테스트를 안하니만 못하다. 
    - (책) <Effective Unit Test> 
    - 테스트는 자동화되어야 한다. 

### 2. 테스트의 종류
    - Test Pyramid (70% unit tests, 20% integration tests, 10% end-to-end tests) 
        - Unit Test : 프로그램 내부의 개별 컴포넌트의 동작을 테스트한다. 배포하기 전에 자동으로 실행되도록 많이 사용한다.
        - Integration Test : 프로그램 내부의 컴포넌트들을 합쳐서 동작을 테스트한다. 
          Unit Test는 각 컴포넌트를 고립시켜 테스트하기 때문에 컴포넌트의 interaction을 확인하는 interaction test가 필요하다. 
        - E2E Test : End to End Test. 실제 유저의 시나리오대로 네트워크를 통해 서버의 Endpoint를 호출해 테스트한다. 

### 3. Unit Test 작성 
    - 테스트 라이브러리를 사용하자. (JUnit5 + mockito를 많이 사용한다) 
    - Test Double : 테스트에서 원본 객체를 대신하는 객체 
        - Stub 
            - 원래의 구현을 최대한 단순한 것으로 대체한다. 
            - 테스트를 위해 프로그래밍된 항목에만 응답한다. 
        - Spy 
            - Stub의 역할을 하면서 호출에 대한 정보를 기록한다. 
            - 이메일 서비스에서 메시지가 몇 번 전송되었는지 확인할 때 
        - Mock 
            - 행위를 검증하기 위해 가짜 객체를 만들어 테스트하는 방법
            - 호출에 대한 동작을 프로그래밍 할 수 있다. 
            - Stub은 상태를 검증하고 Mock은 행위를 검증한다. 
    - given-when-then 패턴을 사용하자 
        - given : 테스트에 대한 pre-condition
        - when : 테스트 하고싶은 동작 호출
        - then : 테스트 결과 확인 

### 4. FIRST 원칙 
    - Fast : 더 빠르게 
        테스트는 빨리 돌아야 한다. 자주 돌려야 하기 때문이다. 
    - Independent : 독립적으로 
        각 테스트를 독립적으로 작성한다. 서로에게 의존하면 실패한 원인을 찾기 어려워진다.
    - Repeatable : 반복 가능하게 
        테스트는 어떤 환경에서도 반복 가능해야 한다. 실제 환경, QA 환경, 모든 환경에서 돌아가야 한다. 
    - Self-Validating : 자가 검증하는 
        테스트는 bool값으로 결과를 내야 한다. 
    - Timely : 적시에 
        테스트하려는 실제 코드를 구현하기(개발하기) 직전에 구현한다. 

## 10장 클래스 잘 설계하기 

### 1. 캡슐화되어야 한다
    - 캡슐화 : 객체의 실제 구현을 외부로부터 감추는 방식 
        - 클래스를 개발할 때 기본적으로 구현을 감추고, 외부 객체와 상호작용하는 부분만 노출한다. 
        - 외부의 잘못된 사용을 방지한다. 

### 2. 단일 책임 원칙 
    - 클래스는 작아야 한다. (클래스가 맡은 책임이 한 개인가) 
        - 함수와 마찬가지로 클래스도 작아야 한다. 
        - 함수는 라인 수로 크기를 측정했는데, 클래스는 맡은 책임의 수로 크기를 측정한다. 
        - 클래스 설명은 만일(if), 그리고(and), 하며(or), 하지만(but)을 사용하지 않고 25단어 내외로 가능해야 한다.
        
    - 단일 책임 원칙 (SRP) 
        - SRP 해야한다. 자잘한 단일 클래스가 많아지면 큰 그림을 이해하기 어렵다고 우려한다.
        하지만 작은 클래스가 많은 시스템이든 큰 클래스가 몇 개뿐인 시스템이든 돌아가는 부품은 그 수가 비슷하다. 
        - 작은 클래스는 각자 맡은 책임이 하나며, 변경할 이유가 하나며, 다른 작은 클래스와 협력해 시스템에 필요한 동작을 수행한다. 

### 3. 낮은 결합도, 높은 응집도 
    - 결합도(Coupling) : 다른 모듈 간의 의존도 
    - 응집도(Cohesion) : 모듈 내부의 기능 집중도 
    
    - 결합도가 높은 클래스의 문제점
        - 연관된 클래스가 변경되면 수정이 필요하다
        - 결합도가 높으면 연관된 클래스들을 모두 이해해야 한다. 
    - 응집도가 낮은 클래스의 문제점
        - 여러 기능이 있으므로 이해하기 어렵다 
        - 재사용하기 어렵다 

    - 결합도는 낮아야 한다. 
        - 시스템의 결합도를 낮추면 유연성과 재사용성도 더욱 높아진다. 
        - DIP : 클래스가 상세한 구현이 아니라 추상화에 의존해야 한다. 
        - 추상화를 이용하면 테스트 코드 짜기에 용이하다.   
    - 응집도는 높아야 한다. 
        - 클래스는 인스턴스 변수 수가 적어야 한다. 메서드는 인스턴스 변수를 하나 이상 사용해야 한다.
         메서드가 인스턴스 변수를 많이 사용할수록 응집도가 높다.
        - 응집도가 높다 = 클래스에 속한 메서드와 변수가 서로 의존하며 논리적인 단위로 묶인다. = 서로 관계있는 애들만 모여있다. 
        - 클래스가 응집도를 잃어간다면 함수를 쪼개야 한다. 
        
### 4. 변경하기 쉬워야 한다 

## 11장 관심사 분리 패턴들 

### 1. 관심사 분리
    - construction(생성)과 use(사용)은 아주 다르다
    - 소프트웨어 시스템은(App. 객체를 제작하고 의존성을 서로 '연결'하는) 준비 과정과 (준비 과정 이후에 이어지는) 런타임 로직을 분리해야 한다. 
    - 객체의 생성과 객체를 사용하는 부분을 분리한다. 
    
    - 시작에 대한 관심사 분리 
        - 객체의 생성은 시작 단계에서, 비즈니스 로직은 객체를 사용하는데 집중한다. 
        - main 함수에서 시스템에 필요한 객체를 생성한 후 Application에 넘긴다. 
        - Application은 그저 만들어진 객체를 사용한다. 
        - 모든 객체가 잘 생성되었다고 가정하고, 객체를 이용한 개발에 집중할 수 있다. 
      
    - 요청에 대한 관심사 분리 
        - Spring 프레임 워크를 통해 요청에 대한 관심사를 분리해 요청 처리에 대한 비즈니스 로직에 집중할 수 있다. 
        - Filter, Interception, AOP 
        - 서블릿 필터는 DispatchServlet 이전에 실행이 되는데 요청 내용을 변경하거나, 요청을 처리하기 전에 작업을 수행할 수 있다. 
        - Filter와 Interceptor는 Servlet 단위에서 실행된다. 반면 AOP는 메서드 앞에서 Proxy 패턴으로 실행된다. 
        - 인터셉터는 여러 개를 사용할 수 있고 로그인 처리, 권한체크, 프로그램 실행시간 계산작업, 로그확인 등의 업무처리에 활용된다. 
        - AOP는 메서드 앞에서 Proxy 패턴으로 실행된다. 주로 '로깅', '트랜잭션', '에러처리' 등 비즈니스 단의 메서드에서
        조금 더 세밀하게 조정하고 싶을 때 사용한다. AOP는 주소, 파라미터, annotaion 등 다양한 방법으로 대상을 지정할 수 있다. 

### 2. Dependency Injection (의존성 주입) 
    - 객체 의존성을 DI 컨테이너에 맡긴다. 
    - Setter 메서드 or 생성자 인수를 통해 의존성을 주입한다. 
    - DI 컨테이너는 요청이 들어올 때 필요한 객체의 인스턴스를 만든 후 의존성을 설정한다. 

### 3. Cross Cutting Concern (횡단 관심 분리) 
    - application 전반에서 가지는 공통적인 관심사를 분리한다. 
    - 비즈니스 로직 외에 Logging, Transaction 관리, Security 등 신경써야 할 관심사들이 많다. 
    - 관심사들은 많은 applciation 레이어에 퍼져있는데, 이 관심사들을 분리해 처리하는 것이 효율적이다. 
    
    
## 12장 창발적 설계로 깔끔한 코드 구현하기

### 0. 창발적 설계란
    - 창발성(Emergence) 
        - 하위 계층에는 없는 특성이나 행동이 상위 계층(전체 구조)에서 자발적으로 돌연히 출연하는 현상
        - 각각의 개미는 집을 지을 능력이 없지만 작은 개미들의 상호작용을 통해 집이라는 결과물이 나오는 것처럼
        작은 요소들의 상호작용의 반복이 전체구조에 영향을 미친다. 
        
    - 창발적 설계 : 단순한 4가지를 반복하다보면 전체적으로 깨끗한 코드가 만들어진다. 
        
### 1. 모든 테스트를 실행한다
    - 모든 테스트 케이스를 항상 통과하는 시스템은 '테스트가 가능한 시스템'이다. 테스트가 불가능한 시스템은 검증도 불가능하다.
    - 테스트가 가능한 시스템을 만들려고 애쓰면 설계 품질이 높아진다. 크기가 작고 목적 하나만 수행하는 클래스가 나온다. 
    - 결합도가 높으면 테스트 케이스를 작성하기 어렵기 때문에 결합도를 낮추는 설계를 하게 된다. 
    - '모든 테스트를 실행한다'는 규칙을 따르면 시스템은 낮은 결합도와 높은 응집력이라는 목표를 저절로 달성할 수 있다. 
    
### 2. 중복을 없앤다 
    - 기존의 코드를 최대한 재활용한다.
    - 중복된 코드를 별도의 메서드로 분리한다. 
    - Template Method 패턴 
        - 알고리즘의 구조를 상위 클래스의 메서드에서 정의하고, 하위 클래스에서 자신에 맞게 세부 알고리즘을 정의한다.
        - 구현하려는 알고리즘에 일정한 단계가 있고, 세부 단계마다 조금씩 구현 내용이 다를 때 사용한다. 
        - 알고리즘의 여러 단계를 각 메서드로 선언하고, 그 알고리즘을 수행할 템플릿 메서드를 만든다. 
        - 하위 클래스에서는 나눠진 메서드(단계)를 구현한다. 

### 3. 의도를 표현한다 
    1) 좋은 이름을 선택한다. 
    2) 함수와 클래스 크기를 가능한 줄인다. (작은 클래스와 작은 함수는 이름 짓기도 쉽다.)
    3) 표준 명칭을 사용한다. 다른 개발자가 보고 바로 이해할 수 있도록 
      디자인 패턴을 사용했다면 그 이름을 클래스에 넣어준다. 
    4) 단위 테스트 케이스를 꼼꼼하게 작성한다. 
    5) 다른 사람을 위해 조금이라도 더 읽기 쉽게 만드려고 노력한다. 

### 4. 실용적 관점에서 타협한다 (클래스와 메서드 수를 최소로 줄인다)
    - 여러가지 규칙에 극단적으로 심취해 클래스와 메서드를 무수하게 만들지 말라. 
    - 결국 좋은 코드를 만드는 이유는 생산성을 올리기 위한 것이다.
    - 실용적인 관점에서 타협해야 한다. 
    - DIP (의존성 역전 원칙) 
        - 상위 모델은 하위 모델에 의존하면 안된다. 둘 다 추상화에 의존해야 한다. 
          추상화는 세부사항에 의존해서는 안 된다. 세부사항은 추상화에 따라 달라진다.
        - 하위 모델의 변경이 상위 모듈의 변경을 요구하는 위계관계를 끊는다. 
        - 실제 사용관계는 그대로지만, 추상화를 매개로 메시지를 주고 받으면서 관계를 느슨하게 만든다. 

## 13장 

###
###
###
###
