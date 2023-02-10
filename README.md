# 웹소켓(WebSocket)이란 ?

Transport protocol의 일종으로 쉽게 이야기하면 웹버전의 TCP 또는 Socket이라고 이해하면 된다.
WebSocket은 서버와 클라이언트 간에 Socket Connection을 유지해서 언제든 양방향 통신 또는 데이터 전송이 가능하도록 하는 기술이다.
Real-time-web-application구현을 위해 널리 사용되어지고 있다.
(SNS 어플리케이션, LoL같은 멀티플레이어 게임, 구글 Doc, 증권 거래, 화상 채팅 등)

## 사용 이유

웹 어플리케이션에서 기존의 서버와 클라이언트 간의 통신은 대부분 HTTP를 통해 이루어 졌으며 HTTP는 Request/response기반의 Stateless protocol이다.
즉, 서버와 클라이언트 간의 Socket Connection같은 영구적인 연결이 되어 있지 않고 클라이언트 쪽에서 필요할 때 Request를 할 때만 서버가 Response를 하는 방식으로 통신이 진행되는 한방향 통신이다.
이럴 경우 서버쪽 데이터가 업데이트 되더라도 클라이언트 쪽에는 화면을 새로고침(Refresh)하지 않는한 변경된 데이터가 업데이트 되지 않는 문제가 발생한다. 이 문제의 경우 Long polling 또는Ajax를 사용해도 어느정도 해결이 가능하지만 데이터의 빠른 업데이트가 아주 중요한 요소 중에 하나인 어플리케이션에서는 실시간 업데이트가 아주 중요하기 때문에 Web Socket이 아주 중요한 기술로 사용되고 있다.
Web Socket은 Stateful protocol이기 때문에 클라이언트와 한 번 연결이 되면 계속 같은 라인을 사용해서 통신하기 때문에 HTTP 사용시 필요 없이 발생되는 HTTP와 TCP연결 트래픽을 피할 수 있다.
또한 Web Socket은 HTTP와 같은 포트(80)을 사용하기에 기업용 어플리케이션에 적용할 때 방화벽은 재설정 하지 않아도 되는 장점이 있다.

## 작동 원리

서버와 클라이언트 간에 WebSocket연결은 HTTP 프로토콜을 통해 이루어진다.
만약 연결이 정상적으로 이루어 진다면 서버와 클라이언트 간에 Web Socket연결이 이루어지고 일정 시간이 지나면 HTTP 연결은 자동으로 끊어진다.

WebSocket을 사용하면 전송되는 데이터를 암호화할 수 있다.
이를 위해 추가 기능이 WSS 프로토콜을 통해 사용되며, 
송신측에서는 데이터를 인코딩하고 수신측에서는 디코딩한다.
모든 중개자의 경우 정보가 암호화된 상태로 유지한다.
암호화가 없으면 데이터가 위협의 대상이 된다..

## HTTP 통신 방법과 WebSocket의 차이점

결정적인 차이는 프로토콜이다.
WebSocket 프로토콜은 접속 확립에 HTTP를 사용하지만, 그 후 통신은 Web Socket 독자의 프로토콜로 이루어진다. 또한, header가 상당히 작아 overhead가 적은 특성이 있다. 장시간 접속을 전제로 하기 때문에, 접속한 상태라면 클라이언트나 서버로부터 데이터 송신이 가능하다. 그리고 하나의 커넥션으로 데이터를 송수신 할 수 있다.

## 파일 사용법
1. python 파일과 html 파일에서 0.0.0.0:0000 부분에 자신의 ip와 포터번호를 적어준다.
2. python 파일을 실행시키고 서버를 열어준다.
3. html 파일을 열고(visual studio code의 live server) 통신이 잘 되었는지 connected가 뜨는지 확인한다.
4. 메세지를 전송하여 통신을 확인한다.
