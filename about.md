---
layout: about
title: About
menu: true
order: 10
---

# 김문성(Kim munseong)
매일 새로운 것을 배우고 성장하려고 합니다.

## Contact
- Mail: iris4865@gmail.com
- Github: [github.com/iris4865](https://github.com/iris4865)


## How to Develop
설계를 기준으로 데이터를 맞추는 것이 아닌 데이터를 기준으로 설계합니다.  
완벽한 코드가 아닌 고객과의 충분한 소통으로 가치있는 코드를 개발합니다.  
WET코드보다 DRY코드를 좋아합니다.
- WET: Write Everything Twice
- DRY: Don't Repeat Yourself


## Skills
- **Language**: C#, Scala, Python
- **Framework/Library**: Akka.NET, Flask
- **Database**: Mysql, OracleDB, Cassandra
- **Tool / DevOps**: Github, Docker
- **Environment**: Linux, Windows


## Experience
- [Revol](https://revol.io/home)(2019. 09 ~ 2020. 03)
  - 주니어 개발자(Scala, Python)
- [Mirero System](http://www.mirero.co.kr/)(2017. 08 ~ 2019. 03)
  - 소프트웨어 개발자(C#, WPF)


## Projects
### Company
---
#### Revol
##### 주식매매 알고리즘 개발 및 유지보수
- 설명: 도쿄증권거래소에서 퀀트 트레이딩 알고리즘 개발, 운영 및 유지보수
- 기간: 2019. 12 ~ 2020. 03
- 개발 언어: Scala, Python
- 역할
  - 기존 트레이딩 알고리즘에서 책임자분의 요구사항에 맞춰 유지보수
  - 새로운 트레이딩 알고리즘 개발
  - Python을 이용하여 백테스트와 결과 데이터 README.md파일 작성 자동화

##### 증권 옵션 증거금 계산 API
- 설명: 옵션매매에 필요한 증거금 API 개발
- 기간: 2019. 11 ~ 2019. 11
- 인원: 1명
- 개발 언어: Scala
- 추가 설명
  - KRX 거래소에서 만든 PC COMS를 참고하여 개발
  - 증거금 계산 시 필요한 파라미터를 가져오는 Crawler 개발

##### 파일기반 DB 라이브러리
- 설명: 트레이딩 중에 Database연결이 끊기는 경우 거래내역을 보관하기 위한 라이브러리
- 기간: 2019. 10 ~ 2019. 10
- 인원: 1명
- 개발 언어: Scala
- 추가 설명
  - Table을 폴더로 하고 Primary Key는 파일명, Data는 파일 내부에 저장한다.

---
#### MireroSystem
##### MLS(미래로 딥러닝 솔루션)
- 설명: 이미지를 하나의 클라이언트에서 분류, 학습, 판정하는 솔루션
- 기간: 2018. 10 ~ 2019. 03
- 인원: 11명
- 역할: 클리이언트 딥러닝 학습UI 설계, 학습 서비스 설계 및 신규개발, 학습 서비스(C#)에서 딥러닝 프레임워크(Python) 호출 및 실행, 여러개의 학습 프레임워크 Interface 개발
- 개발 언어: C#, WPF, Python
- 주요 라이브리러: [Akka.net](https://github.com/akkadotnet/akka.net), [PythonNET](https://github.com/pythonnet/pythonnet), [Dapper](https://github.com/StackExchange/Dapper), [OpenCvSharp](https://github.com/shimat/opencvsharp)
- 학습 프레임워크: NvCaffe, DigitsCaffe, Tensorflow, Keras, PyTorch
- 배운점
  - 여러개의 DeepLearning Framework를 단일 인터페이스를 통합하여 난이도를 낮추고 개발속도를 향상시켰다.

##### Inference Service
- 설명: 이미지를 딥러닝 판정(Inference)하는 이미지 분석 서비스
- 기간: 2018. 01 ~ 2019. 09
- 인원: 2명
- 역할: 판정 서비스(C#)에서 딥러닝 프레임워크(Python)의 호출 및 실행
- 개발 언어: C#, WPF, Python
- 주요 라이브리러: [Akka.net](https://github.com/akkadotnet/akka.net), [PythonNET](https://github.com/pythonnet/pythonnet), [Dapper](https://github.com/StackExchange/Dapper), [OpenCvSharp](https://github.com/shimat/opencvsharp)
- 판정 프레임워크: NvCaffe, DigitsCaffe, Tensorflow
- 배운점
  - 강타입에서 약타입의 언어를 호출하기가 어려웠다.
  - 개발속도를 향상시키기 위하여 Python Framework를 API서비스(Flask)로 개발하는 제안을 했다.


### Personal
---
#### Todolist
- 기간: 2019. 05 ~ 2019. 06
- 개발 언어: Javascript, Python
- 주요 라이브러리: [Vue.js](https://github.com/vuejs/vue), [BootstrapVue](https://github.com/bootstrap-vue/bootstrap-vue), [Flask](https://github.com/pallets/flask/), [Flask-SQLAlchemy](https://github.com/pallets/flask-sqlalchemy/)
- 학습
  - Front-End와 Back-End의 차이와 개발방법
  - nginx - vue - flask연결
  - HTML을 템플릿화하여 HTML 코드 재사용방법
  - Docker를 이용하여 Heroku에 배포
  - Github과 Docker Hub를 이용한 컨테이너자동빌드 구축
- Github
  - Docker: https://github.com/iris4865/todolist-dockerfile
  - Vue: https://github.com/iris4865/todolist-vue
  - Flask: https://github.com/iris4865/todolist-flask
- Docker Hub
  - https://hub.docker.com/r/iris4865/programmers-todo


## Education
- 강릉원주대학교 컴퓨터공학과 졸업(2011.03 ~ 2018.02)
  - 공군 (2014.05 ~ 2016.05)