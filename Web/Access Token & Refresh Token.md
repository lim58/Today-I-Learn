# Access Token & Refresh Token

`Access Token` 사용자에 대한 정보를 담아 서비스에 접근하도록 하는 키 (Ex JWT)

`Refresh Token` Access Token을 재발급할 때 사용하는 키

> Access Token 유효기간 짧음
Refresh Token 유효기간 길음
> 

통신 과정에서 탈취당할 위험이 큰 Access Token 만료기간은 짧게 둠

Refresh Token을 주기적으로 재 발급하여 피해 최소화

### **클라이언트 & 서버 통신 과정**

1. 로그인 인증 성공한 클라이언트 `Access Token / Refresh Token` 서버로 부터 받음
2. 클라이언트 `Access Token / Refresh Token` 로컬 저장
3. 클라이언트 `Access Token` 헤더에 넣고 통신일
4. `Access Token` 유효기간 만료
    1. 권한 없는 사용자가 됨 (401에러)
5. 헤더에 `Refresh Token` 을 넣어 API 재요청
6. 사용자 권한을 확인한 서버는 응답 쿼리 헤더에 새로운 `Access Token` 넣어 응답
7. `Refresh Token` 만료되었다면 서버는 401에러를 보내고 클라이언트는 재 로그인 해야함