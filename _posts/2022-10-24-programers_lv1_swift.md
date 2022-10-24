---
layout: posts
comments: true
title: "[프로그래머스]Swift - Lv.1 풀이 코드 모음"
categories: Algorithm
tag: [프로그래머스, algorithm, 알고리즘, Swift, 스위프트]


toc: true
toc_icon: "cog"
toc_sticky: true
date: 2022-10-24
last_modified_at: 2022-10-24
---



# 프로그래머스 Lv.1 풀이 코드 모음

모든 문제의 코드가 적혀져 있는 것은 아니며, 풀 때 마다 추가할 예정이다.

* 짝수와 홀수
  ```swift
  func solution(_ num:Int) -> String {
    var answer: String = ""
    if num % 2 == 0 {
        answer += "Even"
    } else {
        answer += "Odd"
    }

    return answer
  }
  ```

* 평균 구하기
  ```swift
  func solution(_ arr:[Int]) -> Double {
    var sum: Int = 0
    for i in arr {
        sum += i
    }

    var answer = Double(sum) / Double(arr.count)
    return answer
  }
  ```