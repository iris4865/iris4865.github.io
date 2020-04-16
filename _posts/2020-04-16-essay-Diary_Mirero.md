---
layout: post
title:  "회사 리뷰 - mirero"
subtitle:   "첫 회사"
categories: essay
tags: Diary mirero
---

### 열심히 다니려고 했다.
첫 회사라 나름 열심히 다니려고 했다. 회사와 직원은 서로 상생관계라고 생각했다.  
그리고 신입이든 아니든 처음에 들어가면 회사 업무에 빨리 적응하여 1인분을 해야 한다고 생각했다.  
그 생각을 행동으로 옮기는 나만의 방법은 처음 1~2주 정도는 야근을 하더라도 실제 업무를 다른 사람들과 비슷한 일정을 끝내는 것을 목표로 하였다.  
실제로 업무속도를 따라잡아 가면서 야근도 점점 줄어들었다.

### 이미지 분석 솔루션 유지보수
해당 솔루션은 삼성전자에서 회로를 새긴 반도체를 찍은 사진으로 제품이 정상인지 아닌지 분류하는 솔루션이다.  
구조는 크게 클라이언트와 서비스로 나뉘어 있다. 서비스는 삼성전자에서 들어오는 데이터를 분류, 가공하며 직원이 클라이언트에서 가공된 데이터와 사진으로 불량을 확인한다.  
- Language: C#
- OS: Windows
- GUI: WPF, DevExpress
- library: Akka.NET, HappyPath(이름은 확실하지 않다)  
인상적인건 중간에 가공하는 이미지들을 확인하기위해 FTP를 기반으로 만들어져 있었다.
HappyPath는 사내 라이브러리인데 옛날에는 원리를 몰랐지만 지금 생각해보면 Tuple(java라면 Pair)을 직접만들고 Method Chaining을 이용하여 로직을 만들기 쉽게 하는 라이브러리이다.  
초창기 C#일 때 필요해서 만든거라 내장된 Tuple과 Stream API를 이용하면 대체가 가능해 보인다.


### 팀바팀, 부바부, 사바사...
처음에 상사는 같이 야근하는 것을 보고 대견하다고 생각했던 것 같았다. 거기까지였으면 좋았다. 알고보니 야근을 가장 많이 하시는 분이였다.  
업무에 적응이 될 때쯤 야근이 줄어드는가 싶더니 업무가 많아지기 시작했다. 착각일수도 있지만 분명 남들보다 일을 더 많이 한다고 생각이 들었다.  
비슷한 시기에 들어온 동기들이 그 팀은 항상 야근하는 팀이라고 불리고 있다고 알려줬다. 그래도 열심히 하면 연봉이라도 오르겠지 라는 마음에 계속 열심히 했다.


### Inference Service
사람이 분류한 사진을 이용하여 딥러닝한 모델을 이용하여 Inference하는 서비스를 신규 개발하였다.  
하나의 서비스에서 NvCaffe, DigitCaffe, TensorFlow의 model을 가지고 Interence하는 서비스이다.  
같은 이론으로 만든 Network라도 어떻게 구현했는가에 따라 Accuracy가 미세하게 달라지기 때문에 최대한의 Accuracy를 끌어올리려고 여러 Deep Learning Framework를 적용했다.  
- Language: C#, Python
- OS: Linux/Ubuntu
- library: Akka.NET(Remote), Dapper, Python.NET, OpenCvSharp


### mi래로의 아침 ㅎㅎ...
Deep Learning Framework를 가지고 inference를 하는건 간단해보여 금방 개발할 수 있다고 생각했다. 하지만 계속 버그가 발생해서 일정이 늦춰지기 시작했다.  
가장 큰 문제는 C#에서 Python.NET을 사용하는게 가장 큰 문제였다. 타입에 맞춰서 변환하는 것도 계속 버그가 발생했지만 라이브러리 자체에 버그가 있어 프로그램이 멈춰버렸다.  
해결한 방법은 해당 Github repository에서 같은 issue가 있었고 pull request했지만 merge를 하지 않는 상태여서 해당 문제를 해결한 branch를 가지고 재컴파일하여 테스트해보니 문제 없어 그대로 사용하였다.  
Akka.NET에서는 네트워크 연결에서 [메모리 누수문제](https://github.com/akkadotnet/akka.net/issues/3430)가 발생하여 Akka.NET팀에게 문의 끝에 일주일 내로 패치된 버전을 받아 해결할 수 있었다.  
하지만 Python.NET이 너무 불안정했다. 심지어 Stable 버전도 아니고 참여 인원이 적어 개발속도도 느렸다. 대안으로 그냥 Python으로 서비스하면 문제가 없다고 생각하여 Flask를 제안했다.
문제 해결보다 원인 파악하는게 가장 오래걸렸다. 매일 아침마다 너가 짠 코드인데 원인을 왜 모르냐고 혼났다. 덕분에 동기들에게 mi래로의 아침이라고 별명이 생겼다..


### 처음으로 진지하게 퇴사를 고민하다.
Inference Service를 개발하던 중 예비군 소집이 있었다. 미리 소집일 전날에 연차 1일을 신청하고 모든 라인 결제를 받고서 친구들과 술을 마시고 있었다.  
잠깐 핸드폰을 봤는데 부재중 전화가 있어서 전화했더니 버그가 났는데 해결을 못하겠다고 휴가취소하고 내일 출근하라고 했다.  
술기운도 무시는 못하지만 평소에 시나브로 의욕이 줄어들고 있었는데 휴가취소로 인하여 기폭제가 되었다.
- 정시퇴근 보다 많은 야근
- 아침마다 듣는 호통소리
- 휴가 취소 통보
- 코드리뷰를 안하고 있었다는 사실 인지


### 코드 리뷰는 협업의 기초
평소에 코드리뷰를 안해주고는 있었지만 따로 시간을 내서 리뷰하고 있었을 거라 생각하고 있었다.  
협업을 하기 위해서는 서로가 같은 곳을 바라봐야 하는데 코드리뷰는 개발자간의 협업의 기초 중 하나라고 생각했기 때문이다.  
코드리뷰를 해준다고 생각했을 때에는 공격적으로 개발을 했는데 코드리뷰가 없다는 사실을 직시하면서 try catch나 if문을 이용한 수비적인 코드로 바뀌기 시작했다.  
어떻게 보면 전화위복이 된건지는 모르곘다.


### MLS
Deep Learning을 이용하여 Model을 Trainig하고 이미지를 inference하여 자동분류하는 솔루션이다.  
클라이언트에서 Traning을 위한 Image Data, Network와 Parameter들을 따로 등록하여 각각의 조합을 거쳐 Accuracy가 갱신될 때마다 Inference service에 Model을 교체를 반복한다.
저번에 Python.NET을 제거하고 대안으로 Flask를 제안하여 직속상사까지는 합의가 되었지만 모든 프로그램은 C#을 사용해야 한다는 기술팀장의 반대로 무산되었다.  
- Language: C#, Python
- OS: Windows, Linux/Ubuntu
- GUI: WPF, DevExpress
- library: Akka.NET(Cluster), Dapper, Python.NET, OpenCvSharp  
MLS에서는 Keras, PyTorch를 추가하였다. 또한 Akka.NET의 Cluster로 Load Balancing을 적용하여 throughput을 향상시켰다. (Round Robin)  
더 뛰어난 Model이 나올 때마다 교체를 해야하는데 처음 의도는 Model을 Akka.NET을 이용한 Memcached Inference Service였다.  
하지만 Akka.NET의 통신구조는 두 Actor System간의 채널이 하나만 존재한다. 이게 문제가 되는게 큰 Message를 전송하는 경우 다른 Message를 통신할 수 없다.  
다른 Message중 서로간의 통신이 유지되는지 확인하는 Gossip Message(Remote면 Heartbeat)를 받지 못해 서로 연결이 끊기는 아이러니한 상황에 처할 수 있다.  
Akka.NET을 위주로 해결하기 위한 방법으로는 Aggregator Actor를 만들어 Message를 분할시켜 보내는 방식으로 하면 해결할 수 있다.  
다만 이 방법은 따로 추가 개발을 해야하기 때문에 Memcached는 아니지만 대안인 DB, FTP, NAS중에서 NAS를 선택하여 문제를 해결하였다.


### 퇴사를 결심하다.
작성중..