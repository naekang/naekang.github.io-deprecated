---
layout: post
title: Overriding vs Overloading
image: /assets/img/blog/jvm/java.png
categories: [computer-science, java]
tags: [computer-science, java]
accent_image: 
  background: url('/assets/img/blog/jj-ying.jpg') center/cover
  overlay: false
accent_color: '#ccc'
theme_color: '#ccc'
description: >
  오버로딩과 오버라이딩의 차이점에 대해 알아보자.
invert_sidebar: true
---

# [Java] Overrding vs Overloading

Overriding과 Overloading에 대해 알아보자.

* toc
{:toc}


## 다형성(polymorphism)이란?
> 부모-자식 상속 관계에 있는 클래스에서 상위 클래스가 동일한 메시지로 하위 클래스를 다르게 동작시키는 객체 지향 원리

1. 오버로딩(Overloading)
    - 메서드 이름은 같으나 매개변수 유형이나 개수가 다름
    - 기존에 없던 새로운 메서드 생성
2. 오버라이딩(Overriding)
    - 상위 클래스의 메서드를 하위 클래스가 재정의
    - 상속 받은 메서드의 내용만 변경


## 오버로딩(Overloading)
- 자바의 한 클래스 내에서 같은 이름의 메서드를 여러개 정의하는 것
- 매개변수의 타입이나 개수가 달라야함

```java
public class OverloadingTest {

    void test() {
        System.out.println("매개변수 없음");
    }

    void test(int x, int y) {
        System.out.println("매개변수1: " + x + ", 매개변수2: " + y);
    }

    void test(double d) {
        System.out.println("매개변수1: " + d);
    }
}

public class OverloadingMain {
    public static void main(String[] args) {
        OverloadingTest ot = new OverloadingTest();

        // test() 호출
        ob.test();

        // test(int x, int y) 호출
        ob.test(10, 15);

        // test(double d) 호출
        ob.test(1.0);
    }
}
```

## 오버라이딩(Overriding)
- 상속 관계에 있는 클래스 간 같은 이름의 메서드를 재정의하는 것
- 자식 클래스가 부모 클래스에 선언된 것과 같은 메서드를 같은 경우 = 메서드 오버라이딩

```java
public class Cat {

    public void selfInfo(String name, String age) {
        System.out.println("이름: " + name + ", 나이: " + age);
    }
}
```

```java
public class Haul extends Cat {

    public String kind;

    @Override
    public void selfInfo(String name, String age) {
        System.out.println("이름: " + name + ", 나이: " + age + ", 품종: " + this.kind);
    }

}
```