# HTTP

**HyperText Transfer Protocol**

인터넷에서 데이터를 주고 받기 위해 사용되는 프로토콜

클라이언트와 웹 서버 간 데이터를 주고받는데 사용되는 통신 규약

`HTML` `JSON`과 같은 문서 및 데이터를 전송

### **HTTP 특징**

1. **비연결성 Connectionless**
    
    요청과 응답이 한 번 이루어지면 연결이 종료
    
    각각의 요청은 독립적으로 처리됨
    
2. **무상태성 Stateless**
    
    HTTP는 상태를 유지하지 않는 프로토콜
    
    이전 요청의 연결이나 상태 기억 X 이를 보완하고자 cookie session JWT token를 사용
    
3. **Request-Response 모델**
    
    클라이언트가 요청을 보내면 서버가 응답을 반환하는 방식
    

---

### HTTP Message

클라이언트와 서버간 통신은 요청(Request) / 응답(Response)로 구성 

![image.png](HTTP%208d0aa0d9d3e346fda2ba017e7416a2d4/image.png)

| start line / status line | 요청 / 응답의 상태 |
| --- | --- |
| http headers | 전송에 필요한 모든 부가 정보 |
| empty line | 헤더 본문 구분하는 빈 줄 |
| body | 요청 / 응답과 관련된 데이터 or 문서 |

### Request (요청)

클라이언트가 서버에게 보내는 HTTP 메세지

**start line**

- HTTP Method  수행할 작업이나 방식
- 요청 대상(URI or URL) 리소스를 요청하는 주소
- HTTP version

**header**

HTTP 전송에 필요한 모든 부가 정보

**body**

실제 전송할 데이터

### Response (응답)

서버가 클라이언트에게 보내는 HTTP 메세지

**status line**

- Protocol version
- Status code 상태 코드
- Status message 상태 코드에 대한 설명

**header**

HTTP 전송에 필요한 모든 부가 정보

**body**

전송 받은 데이터

[HTTP 기본 - HTTP | MDN](https://developer.mozilla.org/ko/docs/Web/HTTP/Basics_of_HTTP)