---
layout: post
title: '1143. longest common subsequence'
subtitle: longest common subsequence'
categories: algorithm
tags: leetcode algorithm
---

요새 알고리즘 스터디에서 DP를 풀고 있다. 이번 문제도 역시나 어려웠다.

---

**문제 설명**

Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

- For example, "ace" is a subsequence of "abcde".

A common subsequence of two strings is a subsequence that is common to both strings.

---

첫 시도에서 문제를 풀지 못했다. 2차원 배열로 접근했어야했는데, 1차원 배열로 DP를 만들어서 접근하다보니 답을 구할 수 없었다. 그래도 문제를 풀기 위해 고민했던 방식이 LCS 알고리즘과 많이 다르지 않았음에 아쉬움을 떨쳐본다.

LCS 알고리즘은 최장 공통 부분 수열이다. 말이 어렵지.

`ABCDE`와 `WABLE`의 최장 공통 부분 수열은 `ABE`이다.

2차원 배열로 표를 만들어 이전의 값들을 계속 비교하고 값을 채워나간다.

이전의 값? DP로 접근해야한다.

> 조금 더 자세한 설명은 이 블로그를 참조하면 좋다.
>
> > [ChanBLOG](https://chanhuiseok.github.io/posts/algo-34/)

**제출 코드**

```js
var longestCommonSubsequence = function (text1, text2) {
  const dp = Array(text1.length + 1)
    .fill(0)
    .map(() => Array(text2.length + 1).fill(0));

  for (let i = 1; i < dp.length; i++) {
    for (let j = 1; j < dp[i].length; j++) {
      if (text1[i - 1] === text2[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1] + 1;
      } else dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
    }
  }

  return dp[text1.length][text2.length];
};
```

---

1143. Longest Common Subsequence

**[페이지 이동](https://leetcode.com/problems/longest-common-subsequence/)**
