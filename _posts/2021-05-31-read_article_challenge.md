---
layout: post
title: '(21년 5월) 기술 아티클 읽기 챌린지!'
subtitle: read tech articles
categories: review-Tech-Articles
tags: article
---

매일 매일 한 개의 기술 아티클 읽기 도전 중 (2021-05-01 ~ )

(매일 매일... -> 꾸준히...)

---

### 5월

#### 1일

일요일. 쉬었음.

#### 2일

깔끔한 리액트 프로젝트(코드)를 위한 21가지 좋은 예제들을 보여주고 있다. 평소에도 잘 실천하고 있던 부분들도 있었지만, 미처 알지 못했던 부분들도 짚고 넘어갈 수 있어서 가볍게 읽기 좋았다.

> [21 Best Practices for a Clean React Project](https://betterprogramming.pub/21-best-practices-for-a-clean-react-project-df788a682fb)

#### 3일

같이 스터디를 진행하는 팀원이 우리도 이렇게 회고를 하면 좋겠다는 의견을 내며 이번 글을 공유해 주었다. 페어, 혹은 팀 프로젝트의 마무리는 항상 회고를 한다. 회고를 하면서 서로가 더 좋은 방향으로 나아가기 위해 어떻게 피드백을 나누어야 할지 항상 궁금했는데, 이번 글에서 어떤 방식으로 팀 문화를 정리하고 회고를 해야 할지 명확히 알게 되었다.

> [팀 문화의 탄생](https://woowabros.github.io/experience/2020/05/13/birth-of-team-culture.html)

#### 4일

useState의 지연 초기화를 통해 리액트 함수 컴포넌트의 속도를 향상시키는 방법이 무엇일까? 한 번만 사용하지만 계산 비용이 큰 부분을 렌더링 될 때마다 계산을 한다는 건 큰 부담일 것이다. 이런 부분을 지연 초기화를 통해 최초 렌더링에 계산하고 그 이후에는 계산을 하지 않아 성능을 높일 수 있다.

> [글자 4개로 리액트 컴포넌트를 최적화하는 방법](https://ui.toast.com/weekly-pick/ko_20201022)

#### 5일

코로나가 예상보다 길어지며 재택근무를 하는 회사들이 늘고 있다. 우아한 형제들에서는 어떻게 온라인으로 근무를 하고 있을까? 또 온라인으로 짝 프로그래밍을 하면서 어떤 것을 느꼈는지, 참고할 내용들이 많다.

> [[함께 일하기] 온라인 근무와 회고](https://woowabros.github.io/culture/2021/02/10/work-together-how-product-system-team-works.html)

#### 6일

css를 이용해 시각적인 효과를 위해 transition을 사용하다 보면 원하는 대로 구현이 되지 않을 때가 있다. display none이 transition이 적용되지 않는 이유를 알려주며, 함께 적용할 수 있는 방법 몇 가지를 제시해 주고 있다.

> [display none이 transition이 안먹히는 이유](https://velog.io/@dev-tinkerbell/display-none%EC%9D%B4-transition%EC%9D%B4-%EC%95%88%EB%A8%B9%ED%9E%88%EB%8A%94-%EC%9D%B4%EC%9C%A0)

#### 7일

두고두고 읽을 글이 하나 생겼다. 구글의 코드 리뷰 가이드인데, 너무 길어서 하루에 다 보지는 못했다. 시간 날 때마다 꾸준히 어떠한 방식으로 구글이 서로의 코드를 리뷰하며 함께 성장해나가지는 얼핏 살펴볼 수 있다. 사실 코드 스쿼드에서 미션을 구현하며 코드 리뷰를 받고 있어서 리뷰어에 대한 글은 잘 이해가 되지 않는다. 일단 먼저 작성자 관점의 글만 보는 걸로!

> [구글의 코드 리뷰 가이드](https://soojin.ro/review/)

#### 8일

어쩌다 보니 기술 블로그가 조금 밀려버렸다. 하루에 한 개씩 시간 내서 무조건 읽어야 하는데... 오늘은 useHooks의 첫 번째 페이지를 읽었다. 정말 다양한 Custom Hook이 있다는 것에 놀랬다. 나는 아직 리액트 상태 관리도 어려운데. 언제쯤 저런 커스텀 훅을 만들어서 사용할까? 프로젝트에 한 개씩 적용해봐야겠다.

> [useHooks(🐠)](https://usehooks.com/)

#### 9일

일요일, 쉬었다.

#### 10일

Controlled Component와 Uncontrolled Component의 차이가 무엇인지 찾아보게 되었다. 프로젝트를 진행하면서 Form을 한번 밖에 써보지 못했다. 복잡해지는 form을 조금 더 유연하게 관리하기 위해서는 `useImperativeHandle`을 사용한다. 물론, 이게 무엇인지 몰라서 공식문서에 들어가 찾아봤다. 대략적인 코드를 통해 어떻게 사용이 되는지 알아봤지만 직접 써보지 않고서는 이해할 수 없을 것 같다. 부모컴포넌트에서 전달된 ref값을 쓸 수 있게 해주는 것인가? controlled component의 input은 입력할 때마다 렌더링이 된다. submit 버튼 한번의 클릭을 위해 input의 입력 값들이 계속 재렌더링이 될 필요가 있을까? 그것을 방지하기 위해 uncontrolled component가 있다. ref를 통해 submit 버튼을 클릭하는 그 시점의 value값을 전달하는 것!

> [입력을 다루는 다양한 방법](https://so-so.dev/react/form-handling/)

#### 11일

옆에 있는 스크롤을 제어하기 위해서는 어떤 속성들을 알아야할까? 나는 단순히 `webkit-`을 활용하여 scroll의 너비와 높이 값을 변경하였다. hover를 통해 마우스가 상자 위에 올라왔을 때 스크롤이 나오도록 만들었다. 그렇게 너비 값을 지정하고 컴포넌트를 보니 스크롤의 너비 값 때문인지 마우스가 상자 위에 올라갔을 때와 아닐 때의 너비가 달라졌다. 너비와 높이 같은 기하 정보 관련 속성들을 이번에 좀 더 자세히 알아간다.

    > 샘플 예시에서 스크롤바가 없었다면 콘텐츠 영역 너비는 300px이었을 겁니다. 그런데 스크롤바가 16px을 차지하기 때문에 콘텐츠 영역 너비가 284px(300 – 16)이 되었습니다 (문서 내용 중)

> [요소 사이즈와 스크롤](https://ko.javascript.info/size-and-scroll)

#### 12일

프로젝트를 진행하다보면 조금 더 멋지게 화면을 꾸밀 수 있을 것 같은데...? 라는 생각이 가끔 든다. 하지만 내 디자인 감각이 생각을 따라가지 못한다. 이를 위해 간단히 훑어본 21년 웹 디자인 트렌드. custom cursor 같은 경우는 지금도 바로 적용할 수 있을 것 같다. 아마도!

> [21 unique web design trends for 2021](https://webflow.com/blog/web-design-trends-2021)

#### 13일

우연히 토스 홈페이지를 구경하다가 내게 필요한 유용한 영상들을 알게 되었다. 그 첫번째 영상인 '우아하게 비동기 처리하기'. 나는 지금까지 `undefined` 혹은 `null`을 처리하기 위해 조건문을 사용했다. 그때마다 복잡하다고 생각했는데 `?. (Optional chaining)`이 이러한 부분을 해결해 줄 수 있다. 또, 리액트로 비동기처리를 하면서 항상 loading과 error 처리에 대해서 고민을 했었다. react의 실험 단계에 있는 suspence를 통해 에러와 로딩 상태를 더 깔끔하게 분리할 수 있다. 그러나 아직 실험 단계인 점을 기억하자.

> [프론트엔드 웹 서비스에서 우아하게 비동기 처리하기](https://toss.im/slash-21/sessions/3-1)

#### 14일

스켈레톤 UI를 연습하기 위해 블로그를 참고했다. 스켈레톤을 위한 UI를 기존의 UI와 최대한 비슷하게 만들어야하는 점이 중요한 것 같다. 그렇지 않다면 그냥 loading 화면을 띄우는 거랑 다른 것이 없다. 혼자서 따라해보니 생각만큼 쉬운 건 아니였다. css animation을 잘 다루지 못하는 점이 더 많은 시간을 투자하게 만들었다. 또 예시오 다르게 검은색 바탕화면에 스켈레톤 UI를 적용하려다보니 어떤 색깔을 기본으로 놓고 적용해야할지도 고민이 되었다. dominant color에 따라 UI를 적용할 수도 있는데 더 공부해야 봐야겠다.

> [더 나은 UX를 위한 React에서 스켈레톤 컴포넌트 만들기](https://ui.toast.com/weekly-pick/ko_20201110)

#### 15일, 16일

주말, 쉬었다! 열정을 잃지 말자!

#### 17일

리액트를 사용하면서 아직까지 **useMemo**를 제대로 사용한 경험이 없다. 글 본문에서 말하듯, useState와 useEffect는 이제 많이 익숙해진 것 같다. 이번 3주는 혼자 미션을 진행하면서 최적화도 신경쓰며 useMemo와 useCallback을 써보려한다. 블로그의 다음 글인 useCallback도 읽어봐야지.

> [[짤막글] useMemo를 사용해보자](https://velog.io/@kysung95/%EC%A7%A4%EB%A7%89%EA%B8%80-useMemo)

#### 18일

공식문서에서 useMemo와 useCallback의 개념과 예시 코드를 보며 굉장히 비슷하다고 생각했다.

useCallback(fn, deps)은 useMemo(() => fn, deps)와 같습니다. - [react 공식문서](https://ko.reactjs.org/docs/hooks-reference.html#usecallback)

useMemo와 useCallback의 차이는 무엇일까? 모두 memorization을 반환한다. memo는 함수의 값만, callback은 함수 자체를 반환한다.

최적화도 중요하지만 모든 컴포넌트와 함수에 memo와 callback을 사용할 필요는 없다. 많은 연산이 필요한 부분에 적절히 메모리제이션을 적용하자.

> [[짤막글] useCallback을 사용해보자](https://velog.io/@kysung95/%EC%A7%A4%EB%A7%89%EA%B8%80-useCallback%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EC%9E%90)

#### 19일

코드스쿼드 과정의 끝이 다가오면서 고민이 많아졌다. 나는 성장을 하고 있는 걸까? 라는 고민부터 시작해서 좋은 개발자가 되기 위해서는 어떤 준비를 하고 어떤 고민을 해야하는지 등 내 자신에게 묻는 고민이 쌓여간다. 본문에서 말하는 **나의 관점**이 무엇인지 생각해봐야지.

> [성장에 은탄환은 없다](https://so-so.dev/essay/no-silver-bullet/)

#### 20일

여기저기 둘러보다 웹어셈블리라는 것을 알게되었다. 이게 도대체 무언가해서 MDN을 정독했다. 웹 브라우저에서 실행할 수 있는 새로운 유형의 코드란다. 네이티브에 가까운 속도로 웹에서 돌릴 수 있는 길을 제공한다는 말에 자바스크립트랑 경쟁인가? 라고 생각했는데 함께 보완되고 실행되도록 설계되었다고한다.

> [웹어셈블리](https://developer.mozilla.org/ko/docs/WebAssembly/Concepts)

#### 21일

최근 들어 많은 시간을 의자에 앉아서 보낸다. 나름 신경 써서 자세를 고쳐 앉아있지만 목이 아프고, 눈은 침침하고, 허리도 아프다. 앉는 시간이 길어질수록 내 체력은 반비례로 바닥을 기어가고 있다. 본문에서 말하는 '자원은 한정적이다'라는 말에 깊은 공감을 할 수 있었다. 내가 나를 신경 쓰지 않으면 누가 신경을 써줄까? 나를 좀 더 효율적으로 관리하는 데 신경을 써야겠다. 해결되지 않는 오류를 하루 종일 붙잡는 것보다 잠깐 시선을 돌리고 생각을 정리하는 시간을 가져야겠다.

> [오늘만 코딩할 건 아니잖아](https://velog.io/@snoop2head/self-coaching)

### 22일, 23일

쉬었다.

#### 24일

Typescript로 useRef를 처음 쓰면 타입을 지정하고 사용하는 데 많은 어려움이 있다. (저는 그랬습니다...)

useRef의 3가지 종류를 통해 타입을 어떻게 정의하고 사용하는지 알아볼 수 있는 유익한 블로그 글이었다. 또 타입을 정의하는 것에 문제가 생겼을 때 ctrl + click을 통해 내부 동작이 어떻게 되어있는지 확인하는 습관도 들여야겠다.

> [useRef의 3가지 종류로 살펴보는 타입 정의 확인의 중요성](https://darrengwon.tistory.com/865)

#### 25일

화살표 함수형 컴포넌트가 TypeScript+React에서는 몇몇의 명백한 문제점들을 가지고 온다는 설명의 글이다.

```
type MyComponentProps = { title: string };

// 👍 Like this..
function MyComponentFC(props: MyComponentProps) {}

// 👎 ...not like this
const MyComponent: React.FC<MyComponentProps> = (props) => {};
```

> [The Better Way to Type React Components](https://blog.variant.no/a-better-way-to-type-react-components-9a6460a1d4b7)

#### 26일

Velopert 님의 글. 앞서 읽었던 블로그의 글에 이어서 타입 스크립트와 리액트를 사용하는 데 어려움이 있어서 읽게 된 글이다. 함수형 컴포넌트를 작성할 때, 화살표와 function 컴포넌트의 차이를 살펴보았다. 공식 문서에서도 function 키워드를 사용한다고 하니, 다음 프로젝트에서는 화살표 함수형 컴포넌트보다는 function 키워드를 활용해야겠다.

> [리액트 컴포넌트 타입스크립트로 작성하기](https://velog.io/@velopert/create-typescript-react-component)

#### 27일

이번에 Recoil 라이브러리를 사용해서 상태 관리를 하고 있다. 주요 개념들을 살펴보았다. `atom`과 `selector`, atom(공유 상태)를 활용하여 selector(순수 함수)를 거쳐서 view를 깔끔하게 하고 상태 또한 정말 너무나 쉽게 관리할 수 있다. 이전에 `useState`에서 `useContext`를 쓸 때도 편하다고 느꼈는데, recoil은... 정말 정말 편하다.

> [RECOIL 공식 문서](https://recoiljs.org/ko/docs/introduction/core-concepts)

#### 28일

이번 미션에서 가격에 따른 변동 차트를 컴포넌트로 만들어야 했다. canvas를 활용한 방법과 SVG를 사용하는 방법 중 나는 SVG를 사용해서 차트를 만들고자 마음을 먹고 읽게 된 블로그(?). `svg`내에 `<polyline>`이 있다는 것도 알게 되었다. `<path>`를 이용해 베지에 곡선으로 차트를 좀 더 유연하게 만들 수 있다는데... 내 차트는 아직 딱딱해 보인다.

> [How to Make Charts with SVG](https://css-tricks.com/how-to-make-charts-with-svg/)

#### 29일, 30일

주말 쉬었다.

#### 31일

Recoil 상태 관리 라이브러리의 다양한 활용법과 현재 사용되고 있는 라이브러리들의 간단한 설명. 이 영상과 함께 PDF의 자료를 통해 프로젝트에 Selector를 활용한 비동기처리를 적용해 볼 수 있었다. 😋

> [Recoil: 왕위를 계승하는 중입니다 (새로운 React 상태 관리 라이브러리)](https://tv.naver.com/v/16970954)
