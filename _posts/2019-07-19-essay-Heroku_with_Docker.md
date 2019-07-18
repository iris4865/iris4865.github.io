---
layout: post
title:  "도커(Docker) 배포 - 헤로쿠(Heroku)"
subtitle:   "Docker를 이용하여 배포하는 방법"
categories: essay
tags: Docker, Heroku
---

# Heroku란?
Heroku는 AWS위에서 만들어진 Cloud Service다.  
AWS, GCP, Azure와 차이는 Heroku는 PaaS(Platform as a Service)만 지원한다는 점이다.

## Docker Image를 Heroku 배포하는 방법
### 1. Heroku 가입 및 설치
1. Heroku에 가입한다.
  - 이메일인증만 하면된다.
2. Create a new app을 선택하여 신규 앱을 생성한다.
3. 생성한 app에서 Deploy탭으로 이동하면 Heroku CLI를 다운받을 수 있다.
  - 다운로드 링크: [Heroku CLI](https://devcenter.heroku.com/articles/heroku-command-line)
4. 다운받은 Heroku CLI를 설치한다.

### 3. Heroku에 Docker Image 배포
1. Docker Image의 tag변경
  - docker tag \<image> registry.heroku.com/\<app>/\<process-type>
    - \<image>: Docker Image 이름
    - \<app>: Create a new app에서 생성한 App name
    - \<process-type>: 프로세스 유형 선택
      - web(유일하게 외부에서 HTTP를 수신), worker, urgentworker, clock
      - [Procfile format](https://devcenter.heroku.com/articles/procfile#procfile-format)
2. Heroku CLI 접속
  - heroku login
3. Container 접속
  - heroku container:login
4. Docker Image 업로드
  - docker push registry.heroku.com/\<app>/\<process-type>
5. 배포
  - heroku container:release --app \<app> \<process-type>
6. 웹 사이트에서 확인(Open app)

## 후기
처음으로 Cloud에 배포를 해봤다.  
Toy Project를 배포한거라 확실치는 않지만 서버를 관리할 필요가 없다는건 확실해보였다.  
기존에 만든 Docker Image를 그대로 이용하여 새로 빌드할 필요가 없었다.  
  
다음에 할 일  
  - AWS 배포
  - CI/CD를 통한 배포 자동화

CI/CD서버도 Docker를 통해 Cloud에 올리면 좋을 것 같다.