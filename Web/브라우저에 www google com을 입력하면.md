# 브라우저에 www.google.com을 입력하면

<aside>
💡 들어가기 앞서 용어 정리를 하자!

**1. DNS (Domain Name System)**

인터넷의 전화번호부

→ URL 이름과 IP 주소를 저장하고 있는 데이터베이스

`google.com` 도메인 이름을 웹 브라우저에 입력하는 경우 해당 사이트의 올바른 IP 주소를 찾아줌

**2. TCP / IP (Transmission Control Protocol / Internet Protocol)**

송신자가 수신자에게 IP 주소를 사용하여 데이터를 전달하고

데이터의 전송 여부와 순서를 보장하도록 TCP 활용

1. **HTTP (Hyper Text Transfer)**
    
    클라이언트와 서버가 서로 통신할 수 있게 하기 위한 규약
    
</aside>

![image.png](%E1%84%87%E1%85%B3%E1%84%85%E1%85%A1%E1%84%8B%E1%85%AE%E1%84%8C%E1%85%A5%E1%84%8B%E1%85%A6%20www%20google%20com%E1%84%8B%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%85%E1%85%A7%E1%86%A8%E1%84%92%E1%85%A1%E1%84%86%E1%85%A7%E1%86%AB%20318bd8b8d77a444ca80aada42b68062b/image.png)

동작 방식은 위의 그림과 같고

브라우저 주소창에 www.google.com을 입력하면 발생하는 일을 서술 하자면

1. 사용자가 웹브라우저 검색 창에 [www.google.com](http://www.google.com/) 주소를 입력

2. 웹브라우저는 캐싱 된 DNS 기록들을 통해 해당 도메인 주소와 대응하는 IP주소를 확인

3. 웹브라우저가 HTTP를 사용하여 DNS에게 입력된 도메인 주소를 요청

4. DNS가 웹 브라우저에게 찾는 사이트의 IP주소를 응답

    
    > ISP의 DNS 서버가 호스팅하고 있는 서버의 IP를 찾기 위해 DNS query 날림
    > 
    
    > 모든 요청, DNS recursor, IP주소는 작은 데이터 패킷을 통해 보내짐
    > 
    
5. 웹브라우저가 웹서버에게 IP주소를 이용하여 HTML문서 요청

    
    > TCP로 연결되면 브라우저는 GET 요청을 통해 서버에게 [www.google.com](http://www.google.com/)의 웹페이지 요구
    > 
    
6. 웹 애플리케이션 서버(WAS)와 데이터베이스에서 우선 웹페이지 작업을 처리

    
    > WAS? 사용자의 컴퓨터나 장치에 웹애플리케이션을 수행해주는 미들웨어
    
    동적인 페이지(JSP, ASP, PHP…) 처리를 담당하고 DB에 필요한 데이터 정보 받아서 파일 생성
    > 

1. 작업처리 결과를 웹서버로 전송

2. 웹서버는 웹브라우저에게 HTML 문서 결과를 응답

    
    > 응답 결과는 status code로 서버 요청 상태를 보냄
    > 
    
3. 웹브라우저는 화면에 웹페이지 내용물 출력