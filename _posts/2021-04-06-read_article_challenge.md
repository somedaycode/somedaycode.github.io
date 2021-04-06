---
layout: post
title: '기술 아티클 읽기 챌린지!'
subtitle: read tech articles
categories: review-Tech-Articles
tags: article
---

매일 매일 한 개의 기술 아티클 읽기 도전 중 (2021-04-01 ~ )

---

### 4월

#### 1일

코드스쿼드 코드리뷰를 통해 알게된 Proxy 객체. Proxy를 사용하여 옵저버 패턴을 구현할 수 있다는 것을 알게 되었다. Proxy 객체를 사용하는 방법은 여러가지지만, 내가 짜는 코드에 Proxy를 어떻게 적용해볼지는 아직 미지수다. Proxy는 여러가지 행위 (조회, 열거, 함수 호출 등)에 커스텀 동작을 정의할 수 있다.

> [javascript-ES6-Proxy](https://dev-momo.tistory.com/entry/javascript-ES6-Proxy), [사용사례 10가지(toast UI)](https://ui.toast.com/weekly-pick/ko_20170313)

#### 2일

최근 기상청 API를 사용하여 프로젝트를 구현하던 중 CORS 에러를 마주했다. 이 글을 통해 먼저 CORS가 무엇인지 이해했다면 브라우저에서 fetch 요청을 보내고 머리를 감싸쥐며 스트레스를 받을 일은 없었을텐데.. CORS 에러를 계속해서 마주하고 있다면 시간내서 읽어보자!

> [CORS는 왜 이렇게 우리를 힘들게 하는걸까?](https://evan-moon.github.io/2020/05/21/about-cors/)

#### 3일

프론트엔드 개발자라면 브라우저가 어떻게 동작하는지 이해하는 것은 필수다. 브라우저의 동작 방식 이전에 CPU, GPU, 프로세스 그리고 스레드에 대해 간략하게 설명한다. 항상 들어가는 크롬, 그리고 매번 새로운 창을 열기 위해 눌렀던 탭에서 많은 작업들이 이루어지는 걸 알게 되었다. 크롬에는 서로 다른 프로세스들이 존재한다. 이러한 프로세스들은 서로 제어하는 부분들이 다르다. 또, 각 탭은 독립적인 렌더러 프로세스에 의해 실행된다. 자세히 설명되어 있었지만 처음 마주하는 단어들이 많아 오늘 하루만 읽고 모든 것을 이해할 수는 없을 것 같다. 시간이 날 때 틈틈히 계속 보는걸로..

> [네이버 D2의 최신 브라우저의 내부 살펴보기 1편 ](https://d2.naver.com/helloworld/2922312)

#### 4일

어제 읽은 브라우저 내부 살펴보기 1의 다음 편이다. 웹 페이지가 어떤 단계들을 거쳐 화면에 그려지는지 설명해준다. 프로젝트에 캐시스토리지를 사용하며 서비스워커와 함께 사용된다는 글을 MDN에서 읽은 기억이 있는데, 이 글에서도 서비스워커에 대해 간략한 설명이 있다. 오늘 글의 핵심은 '사용자가 사이트를 요청한 이후, 브라우저는 어떤 액션을 취하고 페이지 렌더링을 준비하는가?'이다. 단순히 URL을 입력했지만 4단계나 된다. 추가로 작업하는 것까지 생각한다면 5단계? beforeunload 이벤트가 있다는 것도 알게되었다. 다른 페이지로 넘어가기 전 한번 더 확인한다.

> [최신 브라우저의 내부 살펴보기 2편 ](https://d2.naver.com/helloworld/9274593)

#### 5일

DOM, CSSOM 등 브라우저가 리소스를 어떻게 화면에 렌더링을 해줄까? HTML 문서를 바탕으로 브라우저는 어떠한 절차를 통해서 우리에게 보여주는 걸까? 와 같은 질문들에 명쾌한 대답을 해주는 글이다.

> [최신 브라우저의 내부 살펴보기 3편 ](https://d2.naver.com/helloworld/5237120)

#### 6일

DOM, CSSOM 등 브라우저가 리소스를 어떻게 화면에 렌더링을 해줄까? HTML 문서를 바탕으로 브라우저는 어떠한 절차를 통해서 우리에게 보여주는 걸까? 와 같은 질문들에 명쾌한 대답을 해주는 글이다.

> [최신 브라우저의 내부 살펴보기 4편 ](https://d2.naver.com/helloworld/6204533)