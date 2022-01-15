---
title: "JUnit5"
excerpt: "자바 스터디 04"

categories:
  - Java Study
tags:
  - java
  - 자바 스터디
---

### 0. JUnit 5 학습

#### 구성
JUnit 5 은 세 컴포넌트로 구성되어 있습니다.
1. JUnit Platform
2. JUnit Jupiter
3. JUnit Vintage

#### JUnit Platform
JVM위에서 테스트 프레임워크 실행하기 위한 기본 모듈입니다.
테스트 프레임워크를 개발하기 위한 테스트엔진 API를 정의합니다.

#### Junit Jupiter
테스트와 extension을 쓰기위한 모델입니다. 
(programming model과 extionsion model의 조합)

#### Junit Vintage
테스트엔진이 junit3,4 테스트를 실행하기 할 수 있도록 도와줍니다.

#### 샘플 코드
@Test 어노테이션을 통해 손쉽게 junit을 구현할 수 있습니다.
```java
...
class MyFirstJUnitJupiterTests {

    private final Calculator calculator = new Calculator();

    @Test
    void addition() {
        assertEquals(2, calculator.add(1, 1));
    }
}
```

#### 어노테이션 종류
|어노테이션|설명|
|---|---|
|@Test |해당 메서드가 테스트 메서드임을 나타냅니다.|
|@BeforeAll |해당 메서드가 모든 @Test, @RepeatedTest, @ParameterizedTest, and @TestFactory 보다 먼저 실행됩니다.|
|@AfterAll |해당 메서드가 모든 @Test, @RepeatedTest, @ParameterizedTest, and @TestFactory 메서드가 샐힝된 후 실행됩니다.|
|@DisplayName|커스텀 display name을 만듭니다.|

출처 : https://junit.org/junit5/docs/current/user-guide/ 