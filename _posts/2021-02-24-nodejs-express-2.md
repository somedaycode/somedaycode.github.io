---
layout: post
title: 'Node.js - express (2) 라우팅이란'
subtitle: what is router
categories: develop
tags: nodejs express server
---

프로젝트를 하면서 느낀건, 서버 환경을 잘 이해하기 위해서는 라우팅이 무엇인지 먼저 알아야한다.

처음에 라우팅을 모듈화하고 json파일을 보내면서 라우팅이 뭔지 정확히 알아야겠다고 느꼈다.

내가 이해하기로는

> 요청 -> 응답을 위한 <b>경로설정</b>이다

라우팅은 URI 및 HTTP 요청 메소드에 대한 클라이언트 요청에 응답하는 것이다.

express generator를 이용해 설치했다면 app.js에 아래와 같은 코드를 볼 수 있다.

```js
const indexRouter = require('./routes/index');
const usersRouter = require('./routes/users');
```

저 경로 안에는 무엇이 있을까?
확인해보자.

아래와 같은 코드를 확인 할 수 있다.

```js
const express = require('express');
const router = express.Router();

/* GET home page. */
router.get('/', function (req, res, next) {
  res.render('index');
});

module.exports = router;
```

홈페이지 경로에서 GET 요청을 통해 index.ejs 파일을 render해주는 것을 확인 할 수 있다.

---

```js
// `/' 이것은 홈페이지 경로
// GET 요청에 'this is message'를 응답한다.

app.get('/', function (req, res) {
  res.send('this is message');
});

// '/user' 경로에 대한 PUT 요청 응답
app.put('/user', function (req, res) {
  res.send('Got a PUT request at /user');
});
```
