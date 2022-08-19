---
title: "Technical interview questions for software engineer"
excerpt: "Questions related Java"

categories:
  - Backend
tags:
  - Backend
  - technical interview question
  - technical interview
  - software engineer
  - java 
  - spring
---


### Index
- [Index](#index)
- [Java](#java)
- [Spring](#spring)

---
### Java

1. <span style="color: black; background-color: #fff5b1;"> **Please explain about HashMap and how it works.** 2~3min</span>
    * definition
      * HashMap is Java Collections Framework API and also implemented Map interface.
      * Basically it is key value map. And value is saved on bucket.
      * Compare with list, HashMap performance is faster as O(1) for searching.
      * We need to provide an implementation for **equals()** and **hashCode()** method to work properly.
    * hashCode
      * HashMap uses **hashCode method** to determine the bucket which the value will be stored.
      * pros : whatever key types(Integer, String, Object), hashCode provides standard results.
      * cons : hashCode return type is int. If number of keys is more than int range, collision occur
    * collision
      * collision happens when differen keys have same **hashCode** result
      * HashMap uses 'separate chaining' structure as linked list to resolve collision.
  <br>
2. <span style="color: black; background-color: #fff5b1;"> **Please explain why equals and hashCode method override is required.**</span>
   * It is necessary to do override because **equals method** return false when same value but different object case. Same for **hashCode method**.
  <br>
3. <span style="color: black; background-color: #fff5b1;"> **Please explain what is difference between '=='(equality operator) and 'equals method'**</span>
   * '=='(equality operator) is only **check referencing same memory address**.
   * But we can override 'equals method' that checking referencing same memory address, on top of that **checking internal value if referring different memory address case.**
   * And also when we override 'equals method', we need to override hashCode as well for same reason. Because hashCode generates different value each by memory address.
  <br>
4. <span style="color: black; background-color: #fff5b1;"> **TBD**</span>



---
### Spring

1. <span style="color: black; background-color: #fff5b1;"> **Please explain about Dependency injection.** 2~3min</span>
     * 