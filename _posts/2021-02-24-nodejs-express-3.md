---
layout: post
title: 'res.sendFile과 path.join'
subtitle: how to use express
categories: develop
tags: nodejs express server
---

express를 이용해 서버 환경을 설정하면 `res.sendFile`과 `path.join`을 사용할 일이 많이 생긴다.

`res.sendFile()`은 해당 경로의 파일을 읽고 해당 내용을 클라이언트로 전송할 수 있게 한다.

`res.path.join()`은 인자로 받은 경로를 하나로 합쳐서 문자열 형태로 리턴한다.

- 절대경로를(\_\_dirname)인자로 전달한 경우에는 이를 반영한 결과를 리턴한다.
- `__dirname`은 현재 실행 중인 폴더 경로를 의미한다.
- `__filename`은 현재 실행 중인 파일 경로를 의미한다.

```js
const express = require('express');
const router = express.Router();
const path = require('path');

router.get('/', (req, res) => {
  res.sendFile(path.join(__dirname, '../data/example.json'));
});

// 현재 폴더 경로에서 바깥으로 빠져나간 다음 data폴더의 example.json 파일을 읽고 / 경로에 내용을 전송
```
