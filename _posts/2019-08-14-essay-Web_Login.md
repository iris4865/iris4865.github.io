---
layout: post
title:  "JWT(Json Web Token)"
subtitle:   "Python에서 JWT사용하기"
categories: essay
tags: Python, Flask, JWT
---

# JWT란?
JWT란 Json Web Token의 약자로 클라이언트가 로그인인증정보를 직접 관리하는 Claim Token기반 인증방법이다.
Token을 받은 후 클라이언트에서는 서버에 요청을 할 때 마다 Token을 Header에 포함해서 전달하면 서버는 해당 Token을 검사하여 작업을 처리한다.


## 다른 웹 로그인 방식
### Cookie
쿠키에 사용자의 모든정보를 저장한다.  
서버에 요청할 떄 마다 쿠키의 모든정보를 전달하여야 한다.  

### Session
서버에서 해당 유저의 Token을 발급하고 따로 저장한다.  
클라이언트는 Cookie에 모든 정보를 저장하지 않고 무작위 문자열로 이루어진 Token만 저장한다.  
서버에 요청할 때 마다 Cookie쿠키에 저장된 Token을 포함하여 전달한다.  
서버는 저장한 Token와 전달 된 Token을 비교하여 로그인 상태를 검증한다.  
서버 기반 인증은 서버에 정보를 저장하고 있기 때문에 확장하기가 어렵다.  
A서버의 메모리에 인증되있으면 B서버의 메모리에는 인증이 안되어 있기 때문이다.  
이를 해결하기 위해서 A, B서버가 같은 DB에 같은 정보를 공유하는 방식이 있다.

### Claim기반 로그인
Session DB를 이용하면 확장성은 해결되지만 DB과부하는 피할 수 없다.  
서버과부하를 피하는 방법은 클라이언트가 인증정보를 가지고 있는 것이다.  
Claim Token이란 로그인한 사용자의 정보가 들어있는 Token을 뜻한다. 대표적으로 JWT가 있다.


## Flask에서 JWT적용하기
JWT는 Access Token만 사용하는 방법과 Access Token, Refresh Token을 사용하는 방법이 있다.  
아래는 Flask-JWT-Extended를 이용한 코드다.  

1. 라이브러리 설치
  - Flask==1.1.1
  - Flask-Bcrypt==0.7.1
  - Flask-JWT-Extended==3.21.0

2. Flask 초기화

```python
from flask import Flask
from flask_jwt_extended import JWTManager
from flask_bcrypt import Bcrypt

app = Flask(__name__)

jwt = JWTManager(app)
flask_bcrypt = Bcrypt(app)
```

3. 로그인 함수

```python
@app.route('/login', methods=['POST'])
def login():
    data = request.get_json()
    if user.validate(data): # 데이터 검사
        test_user = get_user(data['id']) # DB에서 ID가 일치하는 유저 검색
        if test_user and flask_bcrypt.check_password_hash(test_user['password'], data['password']):
            del data['password']
            access_token = create_access_token(identity=data)
            refresh_token = create_refresh_token(identity=data)
            data['access_token'] = access_token
            data['refresh_token'] = refresh_token
            save_token(refresh_token) # Refresh Token 저장
            return jsonify({'return': True, 'data': data}), 200
        else:
            return jsonify({'return': False, 'message': 'invalid username or password'}), 401
    else:
        return jsonify({'return': False, 'message': 'Bad request parameters'}), 400
```

4. Token인증을 이용한 로직함수
@jwt_required를 사용하여 Token유효성을 검사한다.

```python
from flask_jwt_extended import jwt_required, get_jwt_identity

@app.route('/test_token')
@jwt_required
def test_token():
    current_user = get_jwt_identity() # 유저의 ID출력
    # 사용자 로직
    return jsonify({'return': True}), 200
```

5. Token Refresh함수
Access Token과 Refresh Token을 갱신하는 함수이다.

```python
@app.route('/refresh', methods=['POST'])
@jwt_refresh_token_required
def refresh(*args, **kwargs):
    current_user = get_jwt_identity()
    if is_expire(current_user['id']): #만료시간 확인
        refresh_token = create_refresh_token(identity=current_user) # 갱신
        save_token(refresh_token) # Refresh Token 저장
        data = {
            'access_token': create_access_token(identity=get_jwt_identity()),
            'refresh_token': refresh_token
        }
    else:
        data = {
            'access_token': create_access_token(identity=get_jwt_identity())
        }
    return jsonify({'return': True, 'data': data}), 200
```

6. 인증실패 
JWT의 무결성이 깨지면 해당 함수를 호출한다.

```python
@jwt.unauthorized_loader
def unauthorized_response(callback):
    return jsonify({
        'return': False,
        'message': 'Missing Authorization Header'
    }), 401
```

## 후기
라이브러리가 상당히 잘 만들어져 있어 구현보다 JWT, Oauth, 웹보안등 기본 개념을 이해하는데 시간이 더 오래 걸렸다.  
단일 서버라면 그냥 Session방식으로 해도 됐을것 같은데 MSA를 하고 싶은 욕심에 JWT까지 찾아보게 되었다.  
테스트 중에 서비스를 내렸다 올려도 Token으로 인증상태를 유지할 수 있어 MSA에 적합한 방식으로 보인다.  

## 다음에 할 일
- JWE(Json Web Encryption)
- 타 서비스와 로그인 서비스의 연동
- Nginx사용법과 대체 프로그램 Envoy 학습