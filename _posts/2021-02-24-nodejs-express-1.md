---
layout: post
title: 'Node.js - express(1) 설치'
subtitle: how to use express
categories: develop
tags: nodejs express server
---

지금까지 따로 서버 환경을 만들지 않고 자바스크립트를 연습하거나 VScode의 live server를 이용하여 프로젝트를 실행해왔다.

클론코딩을 하면서 이번에는 node.js의 프레임워크 Express를 이용해 개발환경을 구성했는데 모르는게 산더미, 그만큼 공부해야할 것이 많다는 것을 깨닫게 되었다.

이 글을 통해 express를 이용해 간단히 서버환경을 구성하는 법을 정리한다.

먼저, 프로젝트를 시작할 폴더를 생성한다.

```
mkdir express-example
cd express-example
```

다음으로 `npm init -y`를 통해 pacakge.json 파일을 만든다.

마지막으로 `npm install express --save`을 터미널에 입력하면 node.js에서 express를 시작할 준비가 되었다.

app.js를 프로젝트 폴더 안에 생성한 후 아래와 같이 입력하면 서버가 만들어진다.

```js
// app.js

[express] 기본 예제

const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`)
})
```

#### 더 쉽게 서버 환경을 구성하는법

`npm install express-generator -g`를 이용해 express-generator를 설치한다음

프로젝트 폴더 안에서,
`expree --view ejs --css sass`를 입력하면

ejs 엔진을 사용하고 sass를 사용하는 node.js express 환경이 구성된다.

마지막으로 `npm install`을 해주면 된다.

```
├── app.js
├── bin
│   └── www
├── package.json
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
│       └── style.css
├── routes
│   ├── index.js
│   └── users.js
└── views
    ├── error.ejs
    ├── index.ejs
```
