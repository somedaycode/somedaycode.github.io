---
layout: post
title: '첫 배포'
subtitle: 'heroku deploy'
categories: daily
tags: daily
---

처음으로 `node.js`, `react`를 사용해 개발한 프로젝트를 heroku에 배포해봤다. 배포를 하는 과정은 생각보다 단순해서 금방 끝낼 수 있었다. 하지만 개발 단계에서 제대로 작동했던 로그인 부분이 배포 이후에 문제가 되는 것을 발견했다. **나중에 알고보니 express에서 static으로 사용하는 부분의 경로가 문제가 되었던 것!** 그래서 router 설정에서 문제가 발생해 제대로 파일을 읽어올 수 없었다. 정말 단순한 문제였지만 해결하기까지는 오랜시간이 걸렸다. router의 get, post요청 로직이 잘못됐나, 혹은 주소를 제대로 설정한 것은 아닐까? 생각했었다.

> 개발 단계에서 제대로 작동했었던 경로설정이 heroku에 배포되었을 때 문제가 발생한건 의문으로 남아있다. (개발 서버에서는 도대체 어떻게 읽어온거야?)
