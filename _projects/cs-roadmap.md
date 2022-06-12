---
layout: project
title: 'CS-Roadmap'
caption: A Community site to share a roadmap for computer science students.
description: >
  컴퓨터과학부 학생들이 각자 공부하는 것을 로드맵으로 작성하고, 공유할 수 있는 커뮤니티 사이트
date: '2021.07 ~ 2022.02'
image: 
  path: /assets/img/projects/csroadmap.png
  srcset: 
    1920w: /assets/img/projects/csroadmap.png
    960w:  /assets/img/projects/csroadmap@0,5x.png
    480w:  /assets/img/projects/csroadmap@0,25x.png
links:
  - title: Link
    url: https://cs-roadmap.com/
accent_color: '#4fb1ba'
accent_image:
  background: '#193747'
theme_color: '#193747'
sitemap: false
---

# CS-Roadmap

## 참여자

| [<img src="https://avatars.githubusercontent.com/u/71018111?v=4" width="100">](https://github.com/Pilse)| [<img src="https://avatars.githubusercontent.com/u/76692479?v=4" width="100">](https://github.com/ki7348) | [<img src="https://avatars.githubusercontent.com/u/70210412?v=4" width="100">](https://github.com/Dongdong351) | [<img src="https://avatars.githubusercontent.com/u/67647794?v=4" width="100">](https://github.com/UOSCS) | [<img src="https://avatars.githubusercontent.com/u/66901361?v=4" width="100">](https://github.com/naekang) |
| :-----------------------------------: | :---------------------------------------: | :-------------------------------------: | :-------------------------------------: | :-------------------------------------: | :-------------------------------------: | :-------------------------------------: |
|[FE] Pilse|[FE] ki7348|[FE] Dongdong351|[BE] UOSCS|[BE] naekang|

## 프로젝트 시작 배경
개발자로 성장하기 위해 어떤 공부를 해야할지 몰라하는 동기들의 고민을 듣고 이런 고민을 해결하고 해결법을 널리 알리기 위한 목적으로 시작하였다.

## CS-Roadmap의 주요 기능
- 자신만의 로드맵 작성
- 작성한 로드맵 공유 및 게시글에 첨부하여 토론 가능
- 깃허브 연동을 통해 자주 사용하는 언어 확인 가능

## 기술 스택
- Java, Spring Boot, Mysql, Redis, Docker

## 담당 기능
- 회원 가입 시 이메일 인증 및 회원 탈퇴 기능 구현
  - 이메일 인증 시 인증코드를 데이터베이스에 저장하는 것 보다 만료 시간을 설정하고 데이터베이스에 접근을 최소화할 수 있는 Redis를 사용하여 구현
- 로드맵 작성 및 수정 기능 담당
- 게시글에 로드맵 첨부, 저장 및 이어 만들기 기능 구현

## 프로젝트 후기
- Spring Boot를 활용하여 만든 첫 프로젝트였다. 백엔드 담당 팀원과 기술적인 격차가 있었으나 서로 도움이 되도록 노력했고 잘 마무리할 수 있었다.
- 처음엔 기능을 위주로 코드를 짜다보니 알 수 없는 에러들을 많이 만나게 되었고 이로 인해 디버깅과 에러 처리의 중요성에 대해 알게되었다.
- TDD에 대해서 들어봤으나 막상 프로젝트할 때에는 적용을 하지 못하였다. 이번 프로젝트를 통해 테스트 코드를 짜고 이 테스트 코드를 통과할 수 있는 로직을 짜는 TDD에 대해 알게 되었고 차후 테스트 코드 작성까지 진행할 예정이다.