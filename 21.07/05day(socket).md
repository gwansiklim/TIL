# 오늘 배운 것
___

* socket

## socket이란?
___

네트워크상에서 동작하는 프로그램 간 통신의 종착점(Endpoint)입니다. 즉, 프로그램이 네트워크에서 데이터를 통신할 수 있도록 연결해주는 연결부라고 할 수 있다.

## socket의 역할
___

현실로 비유하자면 마치 벽에 있는 콘센트 구멍과 비슷하다. 우리가 전기를 사용하기 위해 반드시 거쳐야 하는 연결부에 해당한다. 그럼 네트워크에서의 소켓은 무엇일까?<br/>
우리가 네트워크에서 데이터를 송수신하기 위해 반드시 거쳐야 하는 연결부에 해당한다.

## socket의 종류
___

소켓의 역할은 언제나 같지만 종류는 여러가지가 있다.<br/>
대표적으로 TCP, UDP 프로토콜을 사용하는 2가지의 소켓이 있는데,<br/>
아주 일반적으로는 안정적인 데이터 송수신을 위해 TCP 소켓을 사용하는 경우가 대부분이지만,<br/> 
일부 패킷이 손실되어도 괜찮거나 빠른 전송 속도가 필요한 경우 UDP 소켓을 사용하기도 한다.

## 웹 socket은 무엇일까?
___

실시간 웹 서비스를 제공하기 위해 만들어진 Socket이라고 생각하면 된다.<br/>
최근 Google Docs 등 여러 협업툴이 실시간 공동 편집 기능, 웹 메신저 등에서 많이 사용되는 기술로 최근 점점 많이 사용하는 기술이지만 <br/>
일부 브라우저들이 웹소켓을 지원하지 않기 때문에 모든 브라우저에서의 동작을 보장하지는 못한다.

## socket io 란?
___

자바스크립트를 사용해 웹소켓을 사용하길 원한다면 가장 많이 사용되는 라이브러리다.<br/>
그러나 이 라이브러리는 순수한 웹소켓 기술만 이용한 라이브러리가 아니다.<br/>
위에서 말했듯 웹소켓 기술은 아직 모든 브라우저에서 동작하지는 못하기 때문에, 모든 사용자를 고려해야 하는 경우 실시간성 기능 구현에 어려움이 생기게 된다.<br/>
이 어려움을 해결하기 위해서는 웹소켓을 사용할 수 없는 브라우저인 경우 <br/>
서버에서 데이터를 일정 간격마다 받아오는 polling 기능으로 실시간 기능 구현을 가능케 해준다.











