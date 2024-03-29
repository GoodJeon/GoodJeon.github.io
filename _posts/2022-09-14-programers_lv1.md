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
last_modified_at: 2022-10-31
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

  * 시저암호
  ```python
  def solution(s, n):
    # 빈 문자열 생성
    answer = ''
    # 문자열 요소를 반복
    for i in s:
        # 공백이면 공백을 추가
        if i == ' ':
            answer += ' '
        # 소문자이면서 아스키코드가 122보다 크다면 n을 더하고 6을 빼준다.
        elif i.islower() and ord(i)+n > 122:
            answer += chr(ord(i) + n - 26)
        # 대문자이면서 아스키코드가 90보다 크다면 n을 더하고 26을 빼준다.
        elif i.isupper() and ord(i)+n > 90:
            answer += chr(ord(i) + n - 26)
        # 그게 아니라면 그냥 n만큼 더해주고 문자열에 추가
        else:
            answer += chr(ord(i) + n)
    return answer
  ```
  

* [1차] 비밀지도
  ```python
  def solution(n, arr1, arr2):
    answer = []
    # 지도1, 2를 동시에 반복
    for i, j in zip(arr1, arr2):
        # 2진법으로 변환해서 OR을 사용
        a = bin(i | j)
        # 앞에 0b라는 문자열을 빼주기
        a = a[2:]
        # 만약 주어받은 n보다 문자열이 짧다면,
        if len(a) < n:
            # n에서 문자열의 길이만큼 빼주고 그만큼 공백을 생성해준 후에 문자열을 더해준다.
            a = ' ' * (n - len(a)) + a
        # 그리고 0은 공백으로
        a = a.replace('0', ' ')
        # 1은 #으로 교체해준다,
        a = a.replace('1', '#')
        # 그리고 answer 리스트에 추가
        answer.append(a)
    return answer
  ```


* 최소직사각형
  ```python
  def solution(sizes):
    max_w = 0
    max_h = 0
    for i in sizes:
        i.sort()
        if i[0] > max_w:
            max_w = i[0]
        if i[1] > max_h:
            max_h = i[1]
    
    answer = max_w * max_h
    return answer
  ```

* 문자열 내마음대로 정렬하기
  ```python
  def solution(strings, n):
    answer = sorted(strings, key=lambda x: (x[n],x))
    return answer
  ```

* K번째 수
  ```python
  def solution(array, commands):
    answer = []
    for n in range(len(commands)):
        i = commands[n][0]
        j = commands[n][1]
        k = commands[n][2]
        ans = sorted(array[i-1:j])[k-1]
        answer.append(ans)
    return answer
  ```

* 숫자 문자열과 영단어
  ```python
  def solution(s):
    numbers = {'zero':0, 'one':1, 'two':2, 'three':3, 'four':4,
    'five':5, 'six':6, 'seven':7, 'eight':8, 'nine':9}
    str_tmp = ''
    string = ''
    for i in s:
        if i.isdigit():
            string += str(i)
        else:
            str_tmp += i
        
        if str_tmp in list(numbers.keys()):
            string += str(numbers[str_tmp])
            str_tmp = ''
    answer = int(string)

    return answer
  ```

* 두 개 뽑아서 더하기
  ```python
  def solution(numbers):
    answer = []
    for i in range(len(numbers)-1):
        for j in range(i+1, len(numbers)):
            answer.append(numbers[i]+numbers[j])
    answer = sorted(list(set(answer)))

    return answer
  ```

* 삼총사
  ```python
  def solution(number):
    answer = 0

    for i in range(len(number)-2):
        for j in range(i+1, len(number)-1):
            for k in range(j+1, len(number)):
                if number[i] + number[j] + number[k] == 0:
                    answer += 1
    
    return answer
  ```

* 2016년
  ```python
  import datetime as dt
  def solution(a, b):
    days = ['MON','TUE', 'WED', 'THU', 'FRI', 'SAT', 'SUN']
    date = f'2016-{a}-{b}'
    n = dt.datetime.strptime(date, '%Y-%m-%d').weekday()
    return days[n]
  ```


* 폰켓몬
  ```python
  def solution(nums):
    variable = len(list(set(nums)))
    select = len(nums)/2

    if variable > select:
        return select
    else:
        return variable
  ```

* 소수 찾기
```python
# 에라토스의 체를 이용해야 시간초과 X
def solution(n):
    eratos = [True] * (n+1)
    eratos[0] = False
    eratos[1] = False

    for i in range(n+1):
        if eratos[i]:
            for j in range(i*2, n+1, i):
                eratos[j] = False
    
    answer = eratos.count(True)

    return answer

```

* 모의고사
```python
def solution(answers):
    answer = []
    st1 = [1,2,3,4,5]
    st2 = [2,1,2,3,2,4,2,5]
    st3 = [3,3,1,1,2,2,4,4,5,5]

    a_st1, a_st2, a_st3 = 0, 0, 0

    for i in range(len(answers)):
        if answers[i] == st1[i%5]:
            a_st1 += 1
        if answers[i] == st2[i%8]:
            a_st2 += 1
        if answers[i] == st3[i%10]:
            a_st3 += 1
        
    point = [a_st1, a_st2, a_st3]
    
    for i in range(3):
        if point[i] == max(point):
            answer.append(i+1)

    return answer

```

* 소수 만들기
```python
def solution(nums):
    answer = 0
    sums = []

    for i in range(len(nums)-2):
        for j in range(i+1, len(nums)-1):
            for k in range(j+1, len(nums)):
                sums.append(nums[i] + nums[j] + nums[k])

    eratos = [True] * 10001
    eratos[0], eratos[1] = False, False
    
    for i in range(2, 10001):
        if eratos[i]:
            for j in range(i*2, 10001, i):
                eratos[j] = False

    for i in sums:
        if eratos[i]:
            answer += 1
    
    return answer
```

* 실패율
```python
def solution(N, stages):
    answer = []
    players = len(stages)
    
    fail_rates = {}
    for i in range(1, N+1):
        if players:
            fail_rates[i] = stages.count(i) / players
            players -= stages.count(i)
        else:
            fail_rates[i] = 0

    return sorted(fail_rates, key=lambda x: fail_rates[x], reverse=True)


```

* [1차] 다트 게임
```python
def solution(dartResult):
    points = []
    tmp = ''
    for i in dartResult:
        if i.isnumeric():
            tmp += i
        elif i == 'S':
            points.append(int(tmp))
            tmp = ''
        elif i == 'D':
            points.append(int(tmp) ** 2)
            tmp = ''
        elif i == 'T':
            points.append(int(tmp) ** 3)
            tmp = ''
        elif i == '*':
            if len(points) > 1:
                points[-2] = points[-2] * 2
                points[-1] = points[-1] * 2
            else:
                points[-1] = points[-1] * 2
        elif i == '#':
            points[-1] = points[-1] * -1
        
    return sum(points)
```

* 로또의 최고 순위와 최저 순위
  ```python
  def solution(dartResult):
    rank = [6,6,5,4,3,2,1]
    opportunity = lottos.count(0)
    lottos.sort()
    lottos = lottos[opportunity:]
    count = 0
    for i in lottos:
        if i in win_nums:
            count += 1
    answer = [rank[(count+opportunity)], rank[count]]
    return answer
  ```

  * 체육복
  ```python
  def solution(n, lost, reserve):
    set_lost = sorted(list(set(lost)-set(reserve)))
    set_reserve = sorted(list(set(reserve)-set(lost)))
    copy_lost = set_lost.copy()

    for i in set_lost:
      if i -1 in set_reserve:
        copy_lost.remove(i)
        set_reserve.remove(i-1)
      elif i+1 in set_reserve:
        copy_lost.remove(i)
        set_reserve.remove(i+1)
      
    
    return n - len(copy_lost)
  ```

  * 키패드 누르기
  ```python
  def solution(numbers, hand):
    answer = ''
    phone = {1:[0,0], 2:[0,1], 3:[0,2],
            4:[1,0], 5:[1,1], 6:[1,2],
            7:[2,0], 8:[2,1], 9:[2,2],
            '*':[3,0], 0:[3,1], '#':[3,2]}
    
    left_h = [3,0]
    right_h = [3,2]
    
    for i in numbers:
        if i in [1,4,7]:
            answer += 'L'
            left_h = phone[i]
        elif i in [3,6,9]:
            answer += 'R'
            right_h = phone[i]
        elif i in [2,5,8,0]:
            loc = phone[i]
            left_dist = abs(left_h[0]-loc[0]) + abs(left_h[1]-loc[1])
            right_dist = abs(right_h[0]-loc[0]) + abs(right_h[1]-loc[1])
            
            if left_dist < right_dist:
                answer += 'L'
                left_h = phone[i]
            elif left_dist > right_dist:
                answer += 'R'
                right_h = phone[i]
            elif left_dist == right_dist:
                if hand == 'left':
                    answer += 'L'
                    left_h = phone[i]
                else:
                    answer += 'R'
                    right_h = phone[i]
                    
            
            
        
    
    
    return answer
  ```