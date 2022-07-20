---
layout: post
title: String vs StringBuffer vs StringBuilder
image: /assets/img/blog/jvm/java.png
categories: [computer-science, java]
tags: [computer-science, java]
accent_image: 
  background: url('/assets/img/blog/jj-ying.jpg') center/cover
  overlay: false
accent_color: '#ccc'
theme_color: '#ccc'
description: >
  String, StringBuffer, StringBuilder에 대해 알아보자.
invert_sidebar: true
---

# [Java] String vs StringBuffer vs StringBuilder

String, StringBuffer, StringBuilder에 대해 알아보자.

* toc
{:toc}


## 자바에서 문자열을 다루는 방법
> 상황에 맞는 방법을 사용해야 한다.

1. String
2. StringBuffer
3. StringBuilder


## String
- 불변(immutable)의 속성
```java
String str = "zero"; // == String str = new String("zero");
str += "base"; // zerobase
```
- 위의 코드에서 기존 String 클래스의 참조변수인 `str`이 가리키는 곳에 zero 저장
- `str`에 base를 더하면서 새로운 메모리 영역을 가리키게 되고 기존의 메모리 영역은 **GC**(Garbage Collector)에 의해 사라짐
- 따라서, 문자열이 자주 변하는 경우 Heap 메모리에 많은 Garbage가 생성되며 GC가 많이 발생하여 성능이 저하된다.

## StringBuffer & StringBuilder
- String과는 달리 mutable한 속성을 가진다.
- StringBuffer와 StringBuilder의 차이는 동기화의 유무이다. (`synchronized` 키워드)

![Full-width image](/assets/img/blog/jvm/StringBuffer.png){:.lead width="400" height="100"}
StringBuffer
{:.figure}

![Full-width image](/assets/img/blog/jvm/StringBuilder.png){:.lead width="400" height="100"}
StringBuilder
{:.figure}

- 따라서 멀티쓰레드 환경에서는 `StringBuffer`를 사용해야하고 단일쓰레드이거나 동기화를 고려하지 않는다면 성능이 좋은 `StringBuilder`를 사용하는 것이 좋다.

## 코드로 확인해보기
- "a"를 1,000,000번 추가하는 연산을 해보자.

#### String

```java
import java.util.concurrent.TimeUnit;

public class String_test {
    public static void main(String[] args) {
        long startTime = System.currentTimeMillis();

        String str = "a";

        for (int i = 0; i < 1_000_000; i++) {
            str += "a";
        }

        long endTime = System.currentTimeMillis();

        long totalTime = endTime - startTime;

        System.out.println("시간: " + TimeUnit.MILLISECONDS.toMillis(totalTime) + "밀리초");

        Runtime.getRuntime().gc();

        long usedMemory = Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory();
        
        System.out.print("메모리 사용량: " + usedMemory + " bytes");
    }
}
```

```
시간: 22177밀리초
메모리 사용량: 2507832 bytes
```

#### StringBuilder

```java
import java.util.concurrent.TimeUnit;

public class String_test {
    public static void main(String[] args) {
        long startTime = System.currentTimeMillis();

        StringBuilder sb = new StringBuilder("a");

        sb.append("a".repeat(10_000_000));

        long endTime = System.currentTimeMillis();

        long totalTime = endTime - startTime;

        System.out.println("시간: " + TimeUnit.MILLISECONDS.toMillis(totalTime) + "밀리초");

        Runtime.getRuntime().gc();

        long usedMemory = Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory();
        
        System.out.print("메모리 사용량: " + usedMemory + " bytes");
    }
}
```

```
시간: 3밀리초
메모리 사용량: 2023664 bytes
```