## 특별한 정보

- Host: 요청한 호스트 정보( 도메인 )


- Location: 페이지 리다이렉션


- Allow: 허용 가능한 HTTP 메서드


- Retry-After: 유저 에이전트가 다음 요청을 하기까지 기다려야 하는 시간


---

### Host
#### 요청한 호스트 정보( 도메인 )

> 요청
>
> ---
>
> GET / search?q=hello&hl=ko HTTP/1.1
>
> Host: www.google.com


- 요청에서 사용


- 필수 값이다
  - 다른 건 없어도 되지만 애는 필수


- 하나의 서버가 여러 도메인을 처리해야 할 때


- 하나의 IP 주소에 여러 도메인이 적용되어 있을 때
  - 이때 구분해주는 것

---

### Host
#### 요청한 호스트 정보( 도메인 )

> 클라이언트 **IP: 100.100.100.1**
> 
> ---
> 
> GET /hello HTTP/1.1


> 서버 **IP: 200.200.200.2**
>
> ---
>
> aaa.com
>
> bbb.com
>
> ccc.com
>
> ---
>
> 가상호스트를 통해 여러 도메인을 한번에 처리할 수 있는 서버
>
> 실제 애플리케이션이 여러개 구동될 수 있다

- 클라이언트가 보낸 메시지 hello 가 서버의 여러 어플리케이션 중 어떤 어플리케이션에 들어갈지를 구분할지 알 수 가 없다
  - 어느 도메인으로 가야하는지 구분할 방법이 아예 없다

---

### Host
#### 요청한 호스트 정보( 도메인 )

> 클라이언트 **IP: 100.100.100.1**
>
> ---
>
> GET /hello HTTP/1.1
> 
> **Host: aaa.com**


> 서버 **IP: 200.200.200.2**
> 
> ---
> 
> aaa.com
> 
> bbb.com
> 
> ccc.com

- 따라서, 이렇게 Host 정보를 넣어줌으로써 어느 도메인으로 가는지 알 수 있는 것
  ( host 정보는 필수!! )

---

### Location
#### 페이지 리다이렉션

- 웹 브라우저는 3xx 응답의 결과에 Location 헤더가 있으면, Location 위치로 자동 이동( 리다이렉트 )


- 응답코드 3xx 에서 설명


- 201( Created ) : Location 값은 요청에 의해 생성된 리소스 URI


- 3xx( Redirection ) : Location 값은 요청을 자동으로 리다이렉션하기 위한 대상 리소스를 가르킴

---

### Allow
#### 허용 가능한 HTTP 메서드

- 405 ( Method Not Allowed ) 에서 응답에 포함해야함

- Allow: GET , HEAD , PUT
  - url 경로는 있는데 만약, GET 헤더는 제공을 하고, POST 를 제공하지 않는다면 HTTP 405 에러를 넣고 이 Allow 헤더를 응답에 넣는다
  - 실무에서 그다지 사용하지는 않음

---

### Retry-After
#### 유저 에이전트가 다음 요청을 하기까지 기다려야 하는 시간

- 503( Service Unavailable ): 서비스가 언제까지 불능인지 알려줄 수 있음


- Retry-After: Fri, 31 Dec 1999 23:59:59 GMT( 날짜 표기 )


- Retry-After: 120( 초 단위 표기 )

날짜 or 초 단위로 표기 가능하다 

실제로 사용하기는 쉽지 않다

---