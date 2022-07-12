---
layout: project
title: 'whereisuos'
caption: A mobile application that provide information on University of Seoul campus.
description: >
  서울시립대학교 교내 정보를 제공해주고 건물 사진을 찍으면 건물에 대한 정보를 제공해주는 모바일 어플리케이션
date: '2022.03 ~ 2022.06'
image: 
  path: /assets/img/projects/whereisuos.png
  srcset: 
    1920w: /assets/img/projects/whereisuos.png
    960w:  /assets/img/projects/whereisuos.png
    480w:  /assets/img/projects/whereisuos.png
links:
  - title: Link
    url: ''
accent_color: '#4fb1ba'
accent_image:
  background: '#193747'
theme_color: '#193747'
sitemap: false
---

# 어디시립

## 참여자

| [<img src="https://avatars.githubusercontent.com/u/71018111?v=4" width="100">](https://github.com/Pilse) | [<img src="https://avatars.githubusercontent.com/u/62492860?v=4" width="100">](https://github.com/qf9ar8nv) | [<img src="https://avatars.githubusercontent.com/u/66901361?v=4" width="100">](https://github.com/naekang) | [<img src="https://avatars.githubusercontent.com/u/67647794?v=4" width="100">](https://github.com/UOSCS) |
| :-----------------------------------: | :---------------------------------------: | :-------------------------------------: | :-------------------------------------: | 
|[FE] Pilse |[BE] qf9ar8nv |[BE] naekang | [DevOps] UOSCS |

## 프로젝트 시작 배경
학교 졸업 프로젝트로 시작한 프로젝트이다.

## 어디시립의 주요 기능
- 건물 사진을 찍으면 건물과 건물 내부 시설에 대한 정보를 제공
- 학교 일반공지, 시설공지, 학과공지를 한번에 볼 수 있는 환경 제공
- 원하는 공지사항 구독시 구독한 공지사항에 대한 알림만 제공

## 기술 스택
- Python FastAPI, Docker, MySQL

## 담당 기능
- Yolov5 모델을 이용한 건물 사진 학습
- 찍은 사진에 대해 학습된 모델을 이용하여 결과값 반환 및 S3에 사진 업로드
- 

## 프로젝트 후기
- 