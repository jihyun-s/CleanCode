# Clean Code

## 1. 나쁜 코드
    - 성능이 나쁜 코드 : 불필요한 연산이 들어가서 개선의 여지가 있는 코드
    - 의미가 모호한 코드 : 이해하기 어려운 코드. 네이밍과 그 내용이 다른 코드 
    - 중복된 코드 : 비슷한 내용인데 중복되는 코드 

    (-) 깨진 유리창처럼 계속 나쁜 코드가 만들어지도록 한다.
    (-) 생산성 저하 (기술부채)
    (-) 새로운 시스템을 만들어야 한다. (현시스템 유지보수 어렵기 때문)


## 2. 클린 코드
    - 성능이 좋은 코드
    - 의미가 명확한 코드 = 가독성이 좋은 코드
    - 중복이 제거된 코드


## 3. 의미 있는 이름 짓기 
    - 루프 속 i j k 사용하지 않기 (advaned for문으로 대체, lamda 사용, 맥락에 맞는 이름 사용) 
    - 통일성 있는 단어 사용하기 
    - 변수명에 타입 넣지 않기 
    
    
## 4. Google Java Naming Guide
    - Package Naming Guide : All lover case, no underscores
    - Class Naming Guide : UppderCamelCase (대문자로 시작) 
        - 클래스는 명사, 명사구
        - 인터페이스는 명사, 명사구, (형용사) 
        - 테스트 클래스는 Test로 끝나기 
    - Method Naming Guide : LowerCamelCase (소문자로 시작) 
        - 메서드는 동사, 동사구 
        - jUnit 테스트에 underscore 사기도 함 
