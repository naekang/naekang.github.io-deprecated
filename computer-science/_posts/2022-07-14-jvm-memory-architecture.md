---
layout: post
title: JVM 메모리 구조란?
image: /assets/img/blog/jvm/java.png
categories: [computer-science, java]
tags: [computer-science, java]
accent_image: 
  background: url('/assets/img/blog/jj-ying.jpg') center/cover
  overlay: false
accent_color: '#ccc'
theme_color: '#ccc'
description: >
  JVM 메모리 구조에 대해 알아보자.
invert_sidebar: true
---

# [Java] JVM의 메모리 구조

JVM의 메모리 구조에 대해 알아보자.

* toc
{:toc}


## JVM(Java Virtual Machine) 이란?
![Full-width image](/assets/img/blog/jvm/jvmos.png){:.lead width="800" height="100"}
General Application VS Java Application
{:.figure}
- 자바 가상 머신
- 시스템 메모리 관리
- 자바 기반 애플리케이션을 위해 이식 가능한 환경 제공


## JVM의 메모리 구조
- 응용프로그램이 시작하면, JVM은 시스템으로부터 메모리를 할당받고 JVM은 용도에 따라 메모리를 3개의 영역으로 나누어 관리

![Full-width image](/assets/img/blog/jvm/jvmarea.png){:.lead width="800" height="100"}
JVM Runtime Area
{:.figure}

1. 메서드 영역(method area)
  - 프로그램 실행 중 사용된 클래스의 클래스파일(*.class)을 읽어 분석하고 클래스 데이터 저장
  - 클래스 변수(class variable)도 함께 생성

2. 힙(heap)
  - 인스턴스가 생성되는 공간 = 인스턴스 변수(instance variable)들이 생성되는 공간

3. 호출 스택(call stack)
  - 메서드 작업에 필요한 메모리 공간 제공
  - 메서드가 작업을 수행하는 동안 지역변수 (매개변수 포함)들과 연산의 중간결과 등 저장
  - 메서드 작업 종료 시 할당되었던 메모리공간은 반환되어 비워짐
  - 호출스택의 가장 위에 있는 메서드가 현재 실행중인 메서드이다.


## 코드로 알아보기
```java
class CallStackTest {
    public static void main(String[] args) {
        firstMethod();
    }

    static void firstMethod() {
        secondMethod();
    }

    static void secondMethod() {
        System.out.prinln("secondMethod()");
    }
}
```

```
// 실행결과
secondMethod()
```

1. JVM에 의해 main메서드가 호출되어 호출스택에 main메서드를 위한 메모리공간이 할당되고 main메서드의 코드가 수행되기 시작한다.
2. main메서드에서 firstMethod()를 호출 -> 이때 main 메서드는 아직 끝난상태가 아니기때문에 호출스택에 대기상태로 남아있다.
3. firstMethod()에서 secondMethod() 호출 -> 호출 스택에 main 메서드와 firstMethod()는 대기 상태로 남아있다.
4. secondMethod()에서 println()을 호출
5. println()이 완료 된 후로부터 println() -> secondMethod() -> firstMethod() -> main메서드 순으로 호출 스택에서 비워지게 된다.