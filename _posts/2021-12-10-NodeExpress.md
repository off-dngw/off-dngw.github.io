---
title: "Node Express Module"
author: DongWoo Kim
date: 2021-12-10
categories: [Node]
tags: [Node, Express]
---

**Express**

{:.no_toc}

- Will be replaced with the ToC, excluding the "Contents" header
  {:toc}

---

<br/>

## **꼭 알아둘 개념!**

|---|---|
개념 | 설명 |
express 모듈 | http 모듈처럼 사용할 수 있지만 더 많은 기능이 있는 외부 모듈입니다.
미들웨어 | express 모듈 use() 메소드의 매개변수에 입력하는 함수를 말합니다.
router | 페이지 라우팅을 지원하는 미들웨어 입니다.
morgan | 웹 요청이 들어왔을 때 로그를 출력합니다.
cookie parser | 요청 쿠키를 추출합니다.
connnect-multiparty | multipart/form-data 인코딩 방식을 사용해 POST 요청 데이터를 추출합니다.
express-session | 세션을 쉽게 생성할 수 있게 도와줍니다.

<br/>

---

## **기본 서버 설정**

```js

// 예시 1
let express = require('express')
let app = express();

// requst 이벤트 리스너를 설정합니다.
app.use((req, res) => {
    res.writeHead(200, {'Content-type' : 'text/html'})
    res.end(`<h1> Hello Express</h1>`)
)}

// 서버를 실행 합니다.
app.listen(8080, () => {
    console.log('Server Running http://127,0.0.1:8080')
})

// 예시2

let http = require('http')
let express = require('express');

let app = express()

http.createServer(app).listen(8080, () => {
    console.log('Server Running http://127,0.0.1:8080')
})
```

<br/>

---

<br/>

## **기본 응답 메소드**

|---|---|
메소드 이름 | 설명
response.send() | 매개변수의 자료형에 따라 적절한 형태로 응답합니다.
response.json() | JSON 형태로 응답합니다.
response.jsonp() | JSONP 형태로 응답합니다.
response.redirect() | 웹 페이지 경로를 강제로 이동시킵니다.

<br/>

---

<br/>

## **send() 메소드를 사용한 JSON 전달**

```js
let express = require("express");

let app = express();

app.use((req, res) => {
  let output = [];
  for (let i = 0; i < 3; i++) {
    output.push({
      count: i,
      name: "name -" + 1,
    });
  }
  res.send(output);
});

app.listen(8080, () => {
  console.log("Server Running at http://127.0.0.1:8080");
});
```

<br/>

---

<br/>

## **기본 요청 메소드**

|---|---|
메소드 이름 | 설명 |
params | 라우팅 매개변수를 추출합니다.
query | 요청 매개변수를 추출합니다.
headers | 요청 헤더를 추출합니다.
header() | 요청 헤더의 속성을 지정 또는 추출합니다.
is(type) | 요청헤더의 Content-type 속성을 확인 합니다.

<br/>

---

<br/>

## **요청 헤더의 속성 추출**

```js
let express = require("express");

let app = express();

app.use((req, res) => {
  // User-Agent 속성을 추출합니다.
  let agent = req.header("User-Agent");
  console.log(req.headers);
  console.log(agent);
  res.sendStatus(200);
});

app.listen(8080, () => {
  console.log("Server Running at http://127.0.0.1:8080");
});
```

<br/>

---

<br/>

## **router 미들웨어**

- express 모듈은 페이지 라우팅을 지원합니다.
- 페이지 라우팅은 클라이언트 요청에 적절한 페이지를 제공하는 기술입니다.

#### app 객체의 메소드

|---|---|
메소드 이름 | 설명
get(path, callback, [callback]) | GET 요청이 발생했을 때의 이벤트 리스너를 지정합니다.
post(path, callback, [callback]) | POST 요청이 발생했을 때의 이벤트 리스너를 지정합니다.
put(path, callback, [callback]) | PUT 요청이 발생했을 때의 이벤트 리스너를 지정합니다.
delete(path, callback, [callback]) | DELETE 요청이 발생했을 때의 이벤트 리스너를 지정합니다.
all(path, callback, [callback]) | 모든 요청이 발생했을 때의 이벤트 리스너를 지정합니다.

<br/>

---

#### router 미들웨어 예시

```js

let express = require('express')
let app = express()

//라우터를 설정합니다.
app.get('/a', (req, res) => {
    res.send('<a href='/b'>GO TO B</a>')
})

app.get('/b', (req, res) => {
    res.send('<a href='/b'>GO TO A</a>')
})

app.listen(8080, () => {
    console.log("Server Running at http://127.0.0.1:8080");
})

```

#### router 모듈화

```js
let express = require("express");
let app = express();

//라우터를 생성합니다.
let routerA = express.Router();
let routerB = express.Router();

//라우터 A를 설정합니다.
routerA.get("/index", (req, res) => {
  res.send("<h1> INDEX PAGE </h1>");
});

//라우터 B를 설정합니다.
routerB.get("/index", (req, res) => {
  res.send("<h1> INDEX PAGE </h1>");
});

// 라우터를 설정합니다.
app.use("/a", routerA);
app.use("/b", routerB);

app.listen(8080, () => {
  console.log("Server Running at http://127.0.0.1:8080");
});
```

- 이렇게 설정하면 routerA는 /a/index 경로에 페이지를 생성 하며 routerB는 /b/index 경로에 페이지를 설정하게 됩니다.

<br/>

---

<br/>

## **cookie parser 미들웨어**

- cookie parser 미들웨어는 요청 쿠키를 추출하는 미들웨어 입니다.
- request, response 객체에 cookie 속성과 cookie() 메소드가 부여됩니다.
- npm install cookie-parser 명령어로 설치합니다.
- cookie() 메소드의 세 번째 매개변수에는 다음과 같이 옵션을 줄 수 있습니다.

<br/>

```js
res.cookie("string", "cookie", {
  maxAge: 600,
  secure: true,
});
```

<br/>

#### 쿠키의 메소드 옵션 속성

|---|---|
속성 이름 | 설명
httpOnly | document.cookie를 활용해 쿠키를 조작 할 수 없도록 합니다.
secure | https 통신에서만 쿠키에 접근 할 수 있습니다.
expires | 쿠키의 유효기간을 설정합니다.
Max-Age | 얼마동안 유지할것인지 설정합니다.
Domain | 브라우저가 쿠키값을 전송할 서버의 도메인을 지정합니다.
Path | 브라우저가 쿠키값을 전송할 URL을 지정합니다.

```js
let express = require("express");
let cookieParser = require("cookie-parser");

let app = express();

// 미들웨어를 설정합니다.
app.use(cookieParser());

// 라우터를 설정합니다.
app.get("/getCookie", (req, res) => {
  res.send(req.cookies);
});

app.get("/setCookie", (req, res) => {
  //쿠키를 생성합니다.
  res.cookie("string", "cookie");
  res.cookie("json", {
    name: "cookie",
    property: delicious,
  });
  //응답합니다.
  res.redirect("/getCookie");
});

app.listen(8080, () => {
  console.log("Server Running at http://127.0.0.1:8080");
});
```

<br/>

---

<br/>

## **express-session 미들웨어**

- 쿠키가 클라이언트의 웹 브라우저 정보를 저장하는 것이라면 세션은 서버에 정보를 저장합니다.
- 세션은 클라이언트에 세션 식별자 쿠키를 부여합니다
- npm install express-session 명령어로 설치합니다.

#### session() 메소드의 옵션

#### session 메소드의 매개변수 메소드

|---|---|
메소드 이름| 설명
name | 쿠키의 name 속성을 지정합니다.
store | 세션 저장소를 지정합니다.
cookie | 생성할 cookie 와 관련된 정보를 지정합니다.
secret | 비밀 키를 지정합니다.
resave | 세션이 변경되지 않았어도 세션 저장소에 resave할지 설정합니다.
saveUnitialized | 초기화 되지 않은 세션을 저장소에 저장할지 설정

#### session 객체의 메소드

|---|---|
regenerate() | 세션을 다시 생성합니다.
destroy() | 세션을 삭제 합니다.
reload() | 세션을 다시 불러옵니다.
save() | 세션을 저장합니다.

<br/>

---

<br/>

#### session 미들웨어 예제

```js

let express = require('express')
let session = require('express-session')

let app = express()

// 미들웨어를 설정합니다.
app.use(session({
    secret : 'secret key'
    resave : false,
    saveUnitialized : true,
    cookie : {
        maxAge : 60 * 1000
    }
}))

app.use(8080, (req, res) => {
     console.log("Server Running at http://127.0.0.1:8080");
})

```
