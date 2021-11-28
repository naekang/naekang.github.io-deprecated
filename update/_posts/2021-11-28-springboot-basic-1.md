---
layout: post
title: 스프링부트 프로젝트 생성하기
category: [computer-science, springboot-basic]
tags: [computer-science, springboot-basic]
image: /assets/img/blog/springboot-main.png
accent_image: 
  background: url('/assets/img/blog/jj-ying.jpg') center/cover
  overlay: false
accent_color: '#ccc'
theme_color: '#ccc'
description: >
  자바 ORM 표준 JPA 프로그래밍
invert_sidebar: true
---

# 스프링부트 프로젝트 생성하기

- 스프링부트를 이용하여 프로젝트를 생성하는 2가지 방법에 대해 알아본다.

* toc
{:toc}

## 프로젝트 개발환경
- MacBook Pro 16" 2019
- OS: macOS Monterey 12.0.1
- Java Version: 11
- IDE: IntelliJ IDEA Ultimate 2021.2.3

## Spring initializr 홈페이지를 통해 프로젝트 생성하기
### 1. [Spring Initializr](https://start.spring.io/) 접속
### 2. Project에서 빌드 관리 도구 선택하기
  - **빌드 관리 도구**
    - 프로젝트 내부의 Java 코드와 각종 xml, properties, jar 파일들을 JVM이나 WAS가 인식할 수 있도록 패키징 해주는 빌드 과정 == 빌드 자동화 도구
    - 프로젝트 생성, 테스트 빌드, 배포 등의 작업을 위한 전용 프로그램
    - 필요한 라이브러리들을 종류와 버전, 종속성 정보를 명시함으로써 자동으로 다운로드 해주고 간편히 관리해주는 도구
  - **Maven**
    - Java용 프로젝트 관리도구로 Apache의 Ant 대안으로 만들어짐
    - `pom.xml` 파일에 명시
    - Maven은 외부저장소에서 필요한 라이브러리와 플러그인들을 다운로드 한 후, 로컬시스템의 캐시에 모두 저장

    ~~~xml
    <!-- https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-data-jpa -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
        <version>2.2.4.RELEASE</version>
    </dependency>
    ~~~

  - **Gradle**
    - Apache Maven과 Apache Ant에서 볼 수 있는 개념들을 사용하는 대안으로 나온 프로젝트 빌드 관리 툴
    - Groovy언어를 사용한 Domain-specific-language 사용
    - multi-project 빌드를 도울 수 있도록 디자인

    ~~~groovy
    dependencies { 
      // This dependency is found on compile classpath of this component and consumers. 
      compile 'com.google.guava:guava:22.0' 

      // Use JUnit test framework 
      testCompile 'junit:junit:4.12' 
    }
    ~~~

### 3. language 선택 - **Java**, Kotlin, Groovy

### 4. Spring Boot 버전 선택
- `SNAPSHOT`: 아직 개발단계임
- `GA`: 테스트가 완료된 정식 릴리즈 버전으로 안정적으로 운영되어야 하는 프로젝트에서 사용
- `RC`: 베타 버전, 기능은 픽스되었으나 안정성은 보장할 수 없음
- `M`: 테스트 버전, 기능이 픽스되지 않아 구현될때마다 테스트 버전이 릴리즈 될 수 있음
- **Project Metadata**
  - `Group`: 프로젝트를 정의하는 고유한 식별자 정보 / 기업의 도메인 명
    - 일반적으로 Java의 패키지 네이밍을 따름
  - `Artifact`: jar 파일에서 버전 정보를 뺀 이름으로 소문자를 사용 / 빌드 결과물 이름
  - `Name`: 프로젝트 이름
  - `Description`: 프로젝트에 대한 설명
  - `Package name`: 패키지 이름
  - `Packaging`: 배포 형태 선택
    - `JAR (Java Archive)`
      - Java 애플리케이션이 동작할 수 있도록 자바 프로젝트를 압축한 파일
      - Class (Java리소스, 속성 파일), 라이브러리 파일 포함
      - JRE(Java Runtime Environment)만 있어도 실행 가능(`java -jar 프로젝트명.jar`)
    - `WAR (Web Application Archive)`
      - Servlet / JSP 컨테이너에 배치할 수 있는 웹 애플리케이션 압축파일 포맷
      - 웹 관련 자원 포함 (JSP, Servlet, JAR, Class, XML, HTML, Javascript)
      - 사전 정의된 구조 사용 (WEB-INF, META-INF)
      - 별도의 웹서버 or 웹 컨테치너(WAS) 필요
      - 즉, JAR파일의 일종으로 웹 애플리케이션 전체를 패키징하기 위한 JAR 파일
  - `Java`: 자바 버전 선택 (8, **11**, 17)
- **Dependencies**
  - ADD... 버튼 누르기
  - 필요한 Dependency 검색 후 추가하기 (ex. Spring Web)

### 5. 밑에 있는 3개의 버튼 중 **GENERATE** 버튼 누르기

### 6. 다운로드 된 zip 파일을 압축 해제하고 IntelliJ에서 해당 폴더 열기

## IntelliJ 내부에서 프로젝트 생성하기

### 1. 메뉴바 -> 파일 -> 새로 만들기 -> 프로젝트
![데이터베이스 방언](/assets/img/blog/springboot-basic-1-1.png){:.border.lead width="480" height="480" loading="lazy"}

### 2. 새 프로젝트에서 Spring Initializr을 누르고 웹페이지와 같은 방법으로 생성
![데이터베이스 방언](/assets/img/blog/springboot-basic-1-2.png){:.border.lead width="480" height="480" loading="lazy"}

### 3. 버전 및 Dependency를 생성한 후 완료
![데이터베이스 방언](/assets/img/blog/springboot-basic-1-3.png){:.border.lead width="480" height="480" loading="lazy"}

### 4. 프로젝트 설정에 들어가서 환경 설정 변경하기
- 단축키: cmd + , (Mac)
- 빌드 및 실행 모두 IntelliJ로 변경
- Gradle JVM을 본인 버전에 맞게 변경
![데이터베이스 방언](/assets/img/blog/springboot-basic-1-4.png){:.border.lead width="480" height="480" loading="lazy"}

### 5. 설정 변경이 완료되었으면 src - main - java 패키지 가장 하위에 있는 Application에 들어가 실행하기
![데이터베이스 방언](/assets/img/blog/springboot-basic-1-5.png){:.border.lead width="480" height="480" loading="lazy"}

### 6. 실행이 정상적으로 될 경우 다음과 같은 화면이 나오게 됨
![데이터베이스 방언](/assets/img/blog/springboot-basic-1-6.png){:.border.lead width="480" height="480" loading="lazy"}

### 7. localhost:8080에 접속하였을 때 다음과 같은 화면이 나온다면 정상적으로 완료된 것임
![데이터베이스 방언](/assets/img/blog/springboot-basic-1-7.png){:.border.lead width="480" height="480" loading="lazy"}