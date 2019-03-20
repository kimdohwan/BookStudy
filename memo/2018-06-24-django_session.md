
세션

```
브라우저 -> 로그인요청(username/password) -> 서버
    -> authencation(인증)
        주어진 username/password에 해당하는 유저가 있는지 검사
    -> 인증에 성공하면, 그 사용자에 해당하는 "특정값"을 DB에 저장 (세션값을 저장한다)
    -> "특정값"을 HTTP response에 Set-Cookie헤더로 담아 전송
        -> 브라우저는 response를 받고, Set-Cookie헤더에 담긴 내용을 쿠키저장공간에 저장

-> 이후 브라우저 -> 서버로 가는 모든 요청에 쿠키저장공간에 있는 특정값을 함께 보냄
    -> 서버는 받은 request에 특정값이 있는지 검사, 특정 유저에 매칭이되면 같은 유저가 요청을 보냈다고 간주
```