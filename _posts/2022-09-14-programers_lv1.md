---
layout: posts
comments: true
title: "[프로그래머스]파이썬 - Lv.1 풀이 코드 모음"
categories: Algorithm
tag: [프로그래머스, algorithm, 알고리즘, python, 파이썬]


toc: true
toc_icon: "cog"
toc_sticky: true
date: 2022-09-14
last_modified_at: 2022-10-04
---



# 프로그래머스 Lv.1 풀이 코드 모음

모든 문제의 코드가 적혀져 있는 것은 아니며, 풀 때 마다 추가할 예정이다.

* 정수 내림차순으로 배치하기
  ```python
  def solution(n):
    a = sorted(list(str(n)), reverse = True)
    b = ''
    for i in a:
        b += i
        
    return int(b)
  ```
* 하샤드 수
  ```python
  def solution(x):
    a = sum(list(map(int, list(str(x)))))
    if x % a == 0:
        return True
    else:
        return False
  ```

* 문자열을 정수로 바꾸기
  ```python
  def solution(s):
    return int(s)
  ```
  
* 콜라츠 추측
  ```python
  def solution(num):
    count = 0
    
    while num != 1:
        if num % 2 == 0:
            num /= 2
        else:
            num *= 3
            num += 1
        
        count += 1
    
    if count < 500:
        return count
    else:
        return -1
  ```

* 두 정수 사이의 합
  ```python
  def solution(a, b):
    nums = [a,b]
    sum = 0
    for i in range(min(nums), max(nums)+1):
        sum += i
    
    return sum
  ```

* 서울에서 김서방 찾기
  ```python
  def solution(seoul):
    return f"김서방은 {seoul.index('Kim')}에 있다"
  ```

* 제일 작은 수 제거하기
  ```python
  def solution(arr):
    arr.remove(min(arr))
    
    if len(arr) == 0:
        return [-1]
    else:
        return arr
  ```

* 나누어 떨어지는 숫자 배열
  ```python
  def solution(arr, divisor):
    arr2 = []
    
    for i in arr:
        if i % divisor == 0:
            arr2.append(i)
        
    arr2.sort()
    
    if len(arr2) == 0:
        return [-1]
    else:
        return arr2
  ```

* 음양 더하기
  ```python
  def solution(absolutes, signs):
    sum = 0
    for i,j in zip(absolutes, signs):
        if j == True:
            sum += i
        else:
            sum -= i
    
    return sum
  ```

* 수박수박수박수박수박수?
  ```python
  def solution(n):
    if n % 2 == 0:
        return '수박' * (n//2)
    else:
        return ('수박' * (n//2)) + '수'
  ```

* 가운데 글자 가져오기
  ```python
  def solution(s):
    if len(s) % 2 == 0:
        return s[len(s)//2-1:len(s)//2+1]
    else:
        return s[len(s)//2]
  ```

* 없는 숫자 더하기
  ```python
  def solution(numbers):
    sum = 0
    for i in range(10):
        if i not in numbers:
            sum += i
    
    return sum
  ```

* 내적
  ```python
  def solution(a, b):
    sum = 0
    for i,j in zip(a,b):
        sum += (i * j)
    
    return sum
  ```

* 문자열 내림차순으로 배치하기 
  ```python
  def solution(s):
    rev_s = sorted(list(s), reverse=True)
    result = ''
    for i in rev_s:
        result += i
    
    return result
  ```

* 문자열 다루기 기본
  ```python
  def solution(s):
    if s.isdigit() and (len(s) == 4 or len(s) == 6):
        return True
    else:
        return False
  ```

* 약수의 개수와 덧셈
  ```python
  def solution(left, right):
    sum = 0
    for i in range(left, right+1):
        check = 0
        for j in range(1, i+1):
            if i % j == 0:
                check += 1
        
        if check % 2 == 0:
            sum += i
        else:
            sum -= i
    
    return sum
  ```

* 부족한 금액 계산하기
  ```python
  def solution(price, money, count):
    spend = 0
    for i in range(1, count+1):
        spend += price * i
    
    if money >= spend:
        return 0
    else:
        return spend - money
  ```

* 최대공약수와 최소공배수
  ```python
  def solution(n, m):
    answer = [0,0]
    nums = [n,m]
    # 최대 공약수
    for i in range(1, min(nums)+1):
        if n % i == 0 and m % i == 0:
            answer[0] = i
    # 최소 공배수
    lcm = max(nums)
    while True:
        if lcm % n == 0 and lcm % m == 0:
            break
        else:
            lcm += 1
    answer[1] = lcm
    
    return answer
  ```

* 같은 숫자는 싫어
  ```python
  def solution(arr):
    new_arr = []
    new_arr.append(arr[0])
    for i in range(1, len(arr)):
        if new_arr[-1] != arr[i]:
            new_arr.append(arr[i])
    return new_arr
  ```

* 이상한 문자 만들기
  ```python
  def solution(s):
    s_list = s.split(' ')
    new_s_list = []
    for i in s_list:
        new_s = ''
        for j in range(len(i)):
            if j % 2 == 0:
                new_s += i[j].upper()
            else:
                new_s += i[j].lower()
        new_s_list.append(new_s)
    return ' '.join(new_s_list)
  ```

  * 3진법 뒤집기
  ```python
  def solution(n):
    # 3진법 수를 담을 문자열 생성
    three = ''

    # n이 0보다 클 때까지 반복
    while n:
        # divmod를 사용해서 몫은 n에 나머지는 mod에 저장
        n, mod = divmod(n, 3)
    
        # 나머지수를 문자열에 더해주자
        three += str(mod)

    # int를 사용해 3진법 수를 10진법 수로 출력
    three = int(three, 3)
    return three
  ```

  * 예산
  ```python
  def solution(d, budget):
    d.sort()
    count = 0 
    for i in range(len(d)):
        if budget >= d[i]:
            count += 1
            budget -= d[i]
    return count
  ```