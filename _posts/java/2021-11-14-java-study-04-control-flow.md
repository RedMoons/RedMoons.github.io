---
title: "선택문 및 반복문"
excerpt: "자바 스터디 04"

categories:
  - Java Study
tags:
  - java
  - 자바 스터디
---

### 선택문 & 반복문
1. if
2. switch/case
3. for
4. while


#### if문 & for문 예제
```java
    for (int i=0; i<2; i++) {
        if (i%2 == 1) {
            System.out.println(i+ " : odd");
        }else {
            System.out.println(i+ " : even");
        }
    }
```

#### switch문 예제
```java
int num = 11;
switch (num%10) {
    case 1:
        System.out.println("case 1");
        break;
    case 2:
        System.out.println("case 2");
        break;
    default:
        System.out.println("default");
        break;
}
```

#### while문 예제
```java
int i = 5;
while (0<i) {
    System.out.println(i+" is bigger than 0");
    i -= 1;
}
```