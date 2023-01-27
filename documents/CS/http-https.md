# 💻 HTTP, HTTPS
<br />

## 👨🏻‍💻 HTTP(Hyper Text Transfer Protocol)
- HTTP는 `서버/클라이언트 모델`을 따라 `인터넷`에서 데이터를 주고 받기 위한 프로토콜이다.
- 즉, HTTP는 인터넷에서 Hyper Text를 교환하기 위한 통신 규약으로, `80번 포트`를 사용하고 있다. 따라서 HTTP 서버가 80번 포트에서 요청을 기다리고 있으며, 클라이언트는 80번 포트로 요청을 보내게 된다.
- HTTP는 1989년 팀 버너스 리(Tim Berners Lee)에 의해 처음 설계되었으며, `WWW(World-Wide-Web)기반`에서 세계적인 정보를 공유하는데 큰 역할을 하고 있다.

<br />

## 👨🏻‍💻 HTTP 동작
- 클라이언트 즉, 사용자가 브라우저를 통해서 어떠한 서비스를 URL을 통하거나 다른 것을 통해서 `요청(Request)`을 하면 서버에서는 해당 요청사항에 맞는 결과를 찾아서 사용자에게 `응답(Response)`하는 형태로 동작한다.
- 요청: Client -> Server
- 응답: Server -> Client

<br />

## 👨🏻‍💻 HTTP 특징
- HTTP 메시지는 HTTP 서버와 HTTP 클라이언트에 의해 해석이 된다.
- `TCP/IP`를 이용하는 `응용 프로토콜`이다. (컴퓨터와 컴퓨터 간에 데이터를 전송할 수 있도록 하는 장치로 인터넷이라는 거대한 통신망을 통해 원하는 정보(데이터)를 주고 받는 기능을 이용하는 응용 프로토콜)
- HTTP는 연결 상태를 유지하지 않는 `비연결성 프로토콜`이다.
- HTTP는 연결을 유지하지 않는 프로토콜이기 때문에 `요청/응답 방식으로 동작`한다.

![http](https://user-images.githubusercontent.com/64779472/120214806-ebe8e800-c26f-11eb-9a40-4b161329ac12.PNG)

<br />

## 👨🏻‍💻 HTTP 흐름
1. TCP 연결을 연다: TCP 연결은 요청을 보내거나 응답을 받는데 사용된다. 클라이언트는 새 연결을 열거나, 기존 연결을 재사용하거나, 서버에 대한 여러 TCP 연결을 열 수 있다.
2. HTTP 메시지를 전송한다: HTTP 메시지(HTTP/2 이전)는 사람이 읽을 수 있다. HTTP/2에서는 메시지가 프레임 속으로 캡슐화되어, 직접 읽는게 불가능하다.
```
  GET / HTTP/1.1
  Host: developer.mozilla.org
  Accept-Language: fr
```
3. 서버에 의해 전송된 응답을 읽어들인다.
```
  HTTP/1.1 200 OK
  Date: Sat, 09 Oct 2010 14:28:02 GMT
  Server: Apache
  Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
  ETag: "51142bc1-7449-479b075b2891b"
  Accept-Ranges: bytes
  Content-Length: 29769
  Content-Type: text/html

  <!DOCTYPE html... (here comes the 29769 bytes of the requested web page)
```
4. 연결을 닫거나 다른 요청들을 위해 재사용한다.

<br />

## 👨🏻‍💻 HTTP 메시지
- HTTP/1.1와 초기 HTTP 메시지는 사람이 읽을 수 있었다. 
- HTTP/2에서, 이 메시지들은 새로운 이진 구조인 프레임안에서 `임베드`되어, `헤더의 압축`과 `다중화`와 같은 최적화를 가능하게 한다.
- 본래의 HTTP 메시지의 일부분만이 이 버전의 HTTP(HTTP/2) 내에서 전송된다고 할지라도, 각 메시지의 의미들을 변화하지 않으며 클라이언트는 본래의 HTTP/1.1 요청을 재구성한다.
- 따라서 HTTP/1.1 포맷 내에서 HTTP/2를 이해하는 것은 여전히 유효하다.
- HTTP 메시지의 두 가지 타입인 요청(Request)와 응답(Response)은 각자의 특성있는 형식을 갖고 있다.

<br />

### 🏃 요청(Request)
![http-request](https://user-images.githubusercontent.com/64779472/120215991-66fece00-c271-11eb-9078-718d3b45ad3c.PNG)
- HTTP 메서드: 보통 클라이언트가 수행하고자 하는 동작을 정의한다. (GET, POST 같은 동사나 OPTIONS나 HEAD와 같은 명사) 일반적으로, 클라이언트는 리소스를 가져오거나(GET) HTML 폼의 데이터를 전송(POST)한다.
- HTTP Path: 가져오려는 리소스의 경로이다. 예를 들면 `프로토콜`(http://), `도메인`(developer.mozilla.org), 또는 `TCP포트`(80)인 요소들을 제거한 리소스의 URL이다.
- Version of the Protocol: HTTP 프로토콜의 버전
- Headers: 서버에 대한 추가 정보를 전달하는 선택적 헤더들
- `POST`와 같은 몇 가지 메서드를 위한, 전송된 리소스를 포함하는 응답의 본문과 유사한 본문

<br />

### 🏃 응답(Response)
![http-response](https://user-images.githubusercontent.com/64779472/120216531-1b98ef80-c272-11eb-9319-1f5a66642418.PNG)
- Version of the Protocol: HTTP 프로토콜의 버전.
- Status code: 요청의 성공 여부와, 그 이유를 나타내는 `상태 코드`.
- Status Message: 아무런 영향력이 없는, 상태 코드의 짧은 설명을 나타내는 `상태 메시지`.
- Headers: 요청 헤더와 비슷한, HTTP 헤더들.
- 선택 사항으로, 가져온 리소스가 포함되는 본문.

<br />

### 🏃 상태 코드
- (100 ~ 199): 정보 응답
- (200 ~ 299): 성공적인 응답
- (300 ~ 399): 리디렉션
- (400 ~ 499): 클라이언트 오류
- (500 ~ 599): 서버 오류

<br />

## 👨🏻‍💻 HTTP 기반 API
- HTTP 기반으로 가장 일반즉어로 사용되는 API는 `User Agent`와 서버간에 데이터를 교환하는데 사용할 수 있는 `XMLHttpRequest API`입니다.
- 최신에는 XMLHttpRequest보다 `Fetch API`가 등장했습니다. Fetch는 XMLHttpRequest보다 훨씬 강력하고 유연한 기능을 제공합니다.

<br />

## 👨🏻‍💻 HTTPS(Hyper Text Transfer Protocol Secure)
- HTTPS는 HTTP에 데이터 암호화가 추가된 프로토콜입니다. HTTPS는 HTTP와 다르게 `433번` 포트를 사용하며, 네트워크 상에서 중간에 제 3자가 정보를 볼 수 없도록 `공개키/개인키 암호화`를 지원하고 있습니다.

<br />

## 👨🏻‍💻 HTTPS에서 공개키/개인키 암호화
- HTTPS는 공개키/개인키 암호화 방식을 이용해 데이터를 암호화합니다. 공개키와 개인키는 서로를 위한 한 쌍의 키입니다.
- 공개키: 모두에게 공개 가능한 키
- 개인키: 나만 알고 있어야 하는 키

<br />

### 🏃 공개키와 개인키로 암호화를 통한 얻을 수 있는 효과
- 공개키 암호화: 공개키로 암호화를 하면 개인키로만 복호화 할 수 있다. -> 개인키는 나만 갖고 있으므로, 나만 볼 수 있다.
- 개인키 암호화: 개인키로 암호화하면 공개키로만 복호화할 수 있다. -> 공개키는 모두에게 공개되어 있으므로, 내가 인증한 정보임을 알려 신뢰성을 보장할 수 있다.

<br />

![공개키](https://user-images.githubusercontent.com/64779472/120217209-01abdc80-c273-11eb-9215-4db9ef5a2ce1.PNG)

<br />

## 👨🏻‍💻 HTTPS 동작 과정
- HTTPS는 `SSL`과 같은 프로토콜을 사용하여 `공개키/개인키 기반`으로 데이터를 `암호화`한다.
- 데이터는 암호화되어 전송되기 때문에 임의의 사용자가 데이터를 조회하여도 원본의 데이터를 보는 것은 불가능하다.
- 그렇다면 서버는 클라이언트가 요청을 보낼 때 암호화를 하기 위한 공개키를 생성하여야 하는데, 일반적으로는 `인증된 기관(CA, Certificate Authority)`에 공개키를 전송하여 인증서를 발급 받는다.

<br />

![ca](https://user-images.githubusercontent.com/64779472/120217669-ab8b6900-c273-11eb-9426-d5554dbc96a7.PNG)

<br />

```
  1. A기업은 HTTP 기반의 애플리케이션에 HTTPS를 적용하기 위해 공개키/개인키를 발급함
  2. CA(Certificate Authority)기업에게 돈을 지불하고, 공개키를 저장하는 인증서의 발급을 요청함
  3. CA 기업은 CA기업의 이름, 서버의 공개키, 서버의 정보 등을 기반으로 인증서를 생성하고, CA 기업의 개인키로 암호화하여 A기업에게 이를 제공함
  4. A기업은 클라이언트에게 암호화된 인증서를 제공함
  5. 브라우저는 CA기업의 공개키를 미리 다운받아 갖고 있어, 암호화된 인증서를 복호화함
  6. 암호화된 인증서를 복호화하여 얻은 A기업의 공개키로 데이터를 암호화하여 요청을 전송함
```

- 암호화된 인증서는 CA의 개인키로 암호화되었기 때문에, `신뢰성`을 확보할 수 있고, 클라이언트는 A 기업의 공개키로 데이터를 암호화하였기 때문에 A기업만 복호화하여 원본의 데이터를 얻을 수 있다.
- HTTPS는 이러한 공개키/개인키 기반의 대칭키 암호화 방식을 활용하여 `안전성`을 확보한다.

<br />

## 👨🏻‍💻 HTTP와 HTTPS
- HTTP는 암호화가 추가되지 않았기 때문에 `보안에 취약`하다. 반면에 HTTPS는 안전하게 데이터를 주고받을 수 있다.
- HTTPS를 이용하면 암호화/복호화 과정이 필요하기 때문에 `HTTP보다 속도가 느리다.`(오늘날에는 거의 차이를 못느낀다.)
- HTTPS는 인증서를 발급하고 유지하기 위한 추가 `비용`이 발생한다.

### 🏃 언제 HTTP 사용? 언제 HTTPS 사용?
- 개인 정보와 같은 민감한 데이터를 주고 받아야 한다면 HTTPS를 이용해야 하지만, 단순한 정보 조회 등만을 처리하고 있다면 HTTP를 사용해도 괜찮다.

<br />

## 참고
https://mangkyu.tistory.com/98 <br />
https://post.naver.com/viewer/postView.nhn?volumeNo=16561296&memberNo=1834 <br />
https://velog.io/@surim014/HTTP%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80 <br />
https://developer.mozilla.org/ko/docs/Web/HTTP/Overview <br />



