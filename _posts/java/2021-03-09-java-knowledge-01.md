---
title: "Java Environment Terms"
excerpt: "Basic knowledge"

categories:
  - Java
tags:
  - java
  - 자바
---

## java 기본 용어

#### JVM : Java Virtual Machine
자바 가상 머신은 자바 바이트코드를 실행할 수 있는 주체이다. 
일반적으로 인터프리터나 JIT 컴파일 방식으로 다른 컴퓨터 위에서 바이트코드를 실행할 수 있도록 구현되나 jop 자바 프로세서처럼 하드웨어와 소프트웨어를 혼합해 구현하는 경우도 있다.

Java로 개발한 프로그램을 컴파일하여 만들어지는 바이트코드를 실행시키기 위한 가상머신. JRE(Java Runtime Environment)에 포함되어 있으며, Java 컴파일러가 프론트엔드를 담당한다면 Java 가상 머신은 코드 최적화와 백엔드를 담당한다. 
Java와 함께 썬 마이크로시스템즈에서 개발되었으며 썬이 오라클에 인수된 후 현재는 오라클이 Java 명칭을 비롯하여 모든 권한을 행사하고 있다. 
Java 소스 코드는 javac 컴파일러를 거쳐 바이트코드로 변환되며, 이 바이트코드는 JRE에 들어있는 java classloader에 의해 JVM으로 적재되고 JVM은 적재된 바이트코드를 JIT 컴파일 방식으로 실행한다.
<br>

#### JRE : Java Runtime Environment

#### JDK : Java Development Kit
자바 개발 키트는 자바 SE, 자바 EE, 또는 자바 ME 플랫폼 중 하나를 구현한 것으로 솔라리스, 리눅스, 맥 OS X, 또는 윈도 자바 개발자를 대상으로 오라클에 의해 바이너리 제품으로 제공된다. 
자바 플랫폼의 등장 이래 지금까지 가장 널리 사용되는 소프트웨어 개발 키트다.

썬 마이크로시스템즈에서 개발한 Java 환경에서 돌아가는 프로그램을 개발하는 데 필요한 툴들을 모아놓은 소프트웨어 패키지이다. 
JRE(Java Runtime Environment)와 Java 바이트코드 컴파일러, Java 디버거 등을 포함하는 개발 도구들로 이루어져 있다. IBM에서 자체적으로 변형한 IBM JDK와 오픈 소스 버전인 OpenJDK도 있다.


#### JAVA SE : Java Platform, Standard Edition
#### JAVA EE : Java Platform, Enterprise Edition

출처 : 위키피디아, 나무위키