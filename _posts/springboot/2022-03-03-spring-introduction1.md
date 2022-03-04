---
title: "스프링 thymleaf 동작 구조"
excerpt: "스프링 입문thymleaf view 동작 환경"

categories:
  - Spring introduction
tags:
  - spring
  - 스프링
  - thymleaf
  - 타임리프
---

김영한님의 스프링 입문 강의의 정리내용입니다.

# 기본 세팅
maven, gradle 어느쪽이든 무방합니다.

# view 환경설정

### welcome 페이지 만들기
```bash
resources/static/index.html
```

```html
<!DOCTYPE HTML>
<html>
  <head>
    <title>Hello</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  </head>
  <body>
    Hello
    <a href="/t1">go to t1</a>
  </body>
</html>
```

`static/index.html` 위치는 welcome page 기능을 합니다.

### controller 만들기
```java
@Controller
public class HelloController {
  @GetMapping("t1")
  public String hello(Model model) {
    model.addAttribute("data", "attributeValue");
    return "template1";
  }
}
```

```bash
resources/templates/template1.html
```
```java
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
  <head>
    <title>Hello</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  </head>
  <body>
    <p th:text="'안녕하세요. ' + ${data}" >안녕하세요.</p>
  </body>
</html>
```
# viewResolver 동작 환경
![spring1](/assets/images/spring_introduction1.png)

<http://localhost:8080/t1> 을 실행하면 아래와 같은 결과를 볼 수 있습니다.
![spring2](/assets/images/spring_introduction2.png)

* 컨트롤러가 `반환한 값(template1)`으로 viewResolver가 `해당 파일( template1.html)`을 찾습니다.
* 스프링 부트 템플릿엔진 기본 viewName 매핑이라고 합니다.
* `resources:templates/` + **{ViewName}** + `.html`
