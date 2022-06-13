---
layout: post
title: 프로세스와 스레드의 차이
image: /assets/img/blog/os/process&thread.jpeg
categories: [computer-science, os]
tags: [computer-science, os]
accent_image: 
  background: url('/assets/img/blog/jj-ying.jpg') center/cover
  overlay: false
accent_color: '#ccc'
theme_color: '#ccc'
description: >
  면접 단골 질문으로 나오는 운영체제의 프로세스와 스레드의 차이에 대해 알아보자.
invert_sidebar: true
---

# [운영체제] 프로세스와 스레드의 차이

프로세스와 스레드의 차이에 대해 알아보자.

* toc
{:toc}


## Process (프로세스)
> 프로그램이 메모리 위에 적재되어 운영체제로부터 자원을 할당받는 주체

- 각 프로세스는 별도의 주소 공간에서 실행되며 다른 프로세스의 변수나 자료구조에 접근이 불가능하다.
- 기본적으로 프로세스는 최소 1개의 스레드를 갖는다.
- 여러 프로세스가 실행될 수 있다. = **멀티태스킹**


## Thread (스레드)
> 프로세스 내에서 실행되는 여러 흐름의 단위

- 스레드는 프로세스 내에서 Stack만 할당받고 Code, Data, Heap 영역은 공유한다.
- 프로세스는 다른 프로세스의 메모리에 직접 접근할 수 없다.
- 하나의 프로세스 내에 여러 스레드가 존재할 수 있다. = **멀티스레드**



## Multi Process (멀티 프로세스)
> 하나의 응용 프로그램을 여러 프로세스로 구성하여 각 프로세스가 하나의 태스크를 처리하도록 하는 것

- 프로세스마다 처리하는 테스크가 다르기 떄문에 하나의 프로세스에 문제가 발생해도 다른 프로세스는 영향을 받지 않는다.
- Context Switching 과정에서 오버헤드가 발생할 수 있다.
  - Context Switching: CPU가 다른 프로세스를 수행하도록 새로운 프로세스의 상태 또는 Context를 교체하는 작업



## Multi Thread (멀티 스레드)
> 하나의 응용 프로그램을 여러 스레드로 구성하고 각 스레드로 하여금 하나의 작업을 처리하도록 하는 것

- 프로세스를 생성하는 과정에서 자원을 할당하는 시스템 콜을 줄임으로써 자원을 효율적으로 관리할 수 있다.
- 시스템 자원 소모가 줄어들고 스레드간 작업량이 작아 Context Switching이 빨라 시스템 처리량이 증가한다.
- 다른 프로세스에서 스레드를 제어할 수 없다.
- 하나의 스레드에 문제가 생기면 전체 프로세스가 영향을 받는다.
- 스레드 간 자원 공유는 전역변수를 사용하기 때문에 충돌이 발생할 수 있다. = **동기화 문제**
