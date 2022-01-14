---
layout: posts
comments: true
title: "[Matplotlib]기초 요약"
categories: Python
tag: [python, 파이썬, matplotlib, 데이터 시각화]
toc: true
toc_sticky: true
date: 2022-01-15
last_modified_at: 2022-01-15
---

**[Noitce]** 고쳐야하거나 틀린 것이 있으면 말씀해주세요!
{: .notice--info}



<br>





# Matplotlib

- 시각화 패키지
- 파이썬 표준 시각화 도구로 불림
- 2D 평면 그래프에 관한 다양한 포맷과 기능 지원
- 데이터 분석 결과를 시각화 하는데 필요한 다양한 기능 제공
- https://matplotlib.org/

---

### 패키지 호출


```python
# matplotlib 주 패키지 사용시 
import matplotlib as mpl
    

# pyplot 서브 패키지 사용시 : 주로 사용
import matplotlib.pyplot as plt
```


```python
# 주피터 노트북 매직 명령어

# 노트북 내부에 그림을 표시하도록 지정하는 명령어
%matplotlib inline 
# 그래프가 다른 창에 나오게 하는 명령어
# %matplotlib qt
```


```python
# 판다스 넘파이
import numpy as np
import pandas as pd
```


```python
# 주피터 노트북 결과값 여러개 반환하게 하는 모듈
# from IPython.core.interactiveshell import InteractiveShell
# InteractiveShell.ast_node_interactivity="all"
```


```python
# 한글 문제
# matplotlit의 기본 폰트에서 한글 지원되지 않기 때문에
# matplotlib의 폰트 변경 필요

import platform

from matplotlib import font_manager, rc
plt.rcParams['axes.unicode_minus'] = False

if platform.system() == 'Darwin':  # 맥OS 
    rc('font', family='AppleGothic')
elif platform.system() == 'Windows':  # 윈도우
    path = "c:/Windows/Fonts/malgun.ttf"
    font_name = font_manager.FontProperties(fname=path).get_name()
    rc('font', family=font_name)
else:
    print('Unknown system...  sorry~~~')
```

---

### 지원 되는 플롯 유형
- matplot홈페이지 참조 : [https://matplotlib.org/stable/tutorials/introductory/usage.html](https://matplotlib.org/stable/tutorials/introductory/usage.html)

### 그래프 용어 정리
- figure(x,y) : 그래프 크기 설정 : 단위 인치
- title() : 제목 출력
- xlim : x 축 범위
- ylim : y 축 범위
- xticks():yticks() : 축과 값을 잇는 실선    
- legend() : 범례
- xlabel() : x축라벨(값)
- ylabel() : y축라벨(값)
- grid() : 그래프 배경으로 grid 사용 결정 함수
![image](https://user-images.githubusercontent.com/75322297/149467530-8d80809b-fb45-4cb5-b3a0-39a2772c5bc5.png)  
사진 출처 : [https://matplotlib.org/stable/_images/anatomy.png](https://matplotlib.org/stable/_images/anatomy.png)

### 그래프 속성


#### 축의 눈금 설정 : plt.xticks(), plt.yticks()
- tick은 축상의 위치 표시 지점
- 축에 간격을 구분하기 위해 표시하는 눈금


- xticks([x축값1,x축값2,...]) #튜플,리스트등 이용해서 축 값(위치 나열)
- yticks([y축값1,y축값2,...]) #튜플,리스트등 이용해서 축 값(위치 나열)
- tick_params()
- tick label(눈금 레이블) : tick에 써진 숫자 혹은 글자

#### 범례(legend)표시
- plot에 label 속성이 추가되어 있어야 함
    - plt.plot(x,y,label='a')
- plt.legend(loc=, ncol= ) #범례표시, 
- loc = 1/2/3/4/5/6/7/8/9/10 # 범례표시 위치값
- loc = (x,y)
- ncol= 열갯수

#### 그래프 제목 및 축 레이블 설정
- 그래프 제목 설정: plot.title(data,loc=, pad=, fontsize=)
     - loc= 'right'|'left'| 'center'| 'right'로 설정할 수 있으며 디폴트는 'center'
     - pad=point 은 타이틀과 그래프와의 간격 (오프셋)을 포인트(숫자) 단위로 설정
     - fontsize=제목폰트크기
     
- 축 레이블 설정
    - plot.xlabel()
    - plot.ylabel()

#### plt.subplot() : 여러 플롯 표시

: 하나의 윈도우(figure)안에 여러 개의 플롯을 배열 형태로 표시

- 그리드 형태의 Axes 객체들 생성

- 형식 : subplot(인수1,인수2,인수3)
    - 인수1 과 인수2는 전체 그리드 행렬 모양 지시
    - 인수3 : 그래프 위치 번호


    - subplot(2,2,1) 가 원칙이나 줄여서 221로 쓸 수 있음
    - subplot(221) 2행 2열의 그리드에서 첫번째 위치
    - subplot(224) 2행 2열의 그리드에서 마지막 위치


​    
- tight_layout(pad=) : 플롯간 간격을 설정
    - pad = 간격값(실수)

---

## 1. plt.plot() : 선그래프(line plot)
* matplotlib.pyplot.plot(*args, scalex=True, scaley=True, data=None, **kwargs)

: *args : x, y 축값을 리스트 형식으로 입력, y축값만 쓰는 경우 x축값은 자동 생성

### 선 모양 속성
   *  선 색깔 : color **(c)**
   *  선 굵기 : linewidth  **(lw)**
   *  선 스타일 : linestyle **(ls)**
   *  마커 종류 :  **marker**
   *  마커 크기 : markersize **(ms)**
   *  마커선색깔 : markeredgecolor **(mec)**
   *  마커선굵기 : markeredgewidth **(mew)**
   *  마커내부색깔 : markerfacecolor **(mfc)**    

### 색상

- 정말 다양함.
- 해당 사이트 참조 [https://www.w3schools.com/cssref/css_colors.asp](https://www.w3schools.com/cssref/css_colors.asp)

### 스타일(linestyle = '선스타일') 
1. '-.' : 1점 쇄선
2. '--' : 파선
3. ':' : 점선
4. '-' : 실선

### 예제


```python
# 2 x 2 형태의 네 개의 플롯

# Plot Number 1
plt.subplot(221) # 서브플랏 1번(1/4)
x=[0,1,2,3,4,5,6]
y=[1,4,5,8,9,3,2]
# plt.figure(figsize=(3,3)) # 그래프배경 크기
plt.plot(x, y, c='green', ls='-.', marker = 'p', mfc= 'red', ms=10)
plt.title('스타일 적용 : 약어로 지정')

# Plot Number 2
plt.subplot(222) # 서브플랏 2번(2/4)
t=np.arange(0.,5.,0.2)
t
# plt.figure(figsize=(5,3))
plt.title('라인 플롯에서 여러개의 선 그리기')
plt.plot(t,t,'r--'
,t,0.5*t**2,'bs:',
t,0.2*t**3,'g^-')
# 인수 순서 (x, y, color, marker, linestyle)


# Plot Number 3
plt.subplot(223) # 서브플랏 3번(3/4)
# 데이터 생성
x=[10,20,30,40,50,60]
y=[11,15,40,40,20,10]
# 그래프 그리기
plt.title('그래프제목')
plt.plot(x,y, color='green',linestyle='dashed',marker='o')
# x,y축 눈금 설정
plt.xticks(x,('10대','20대','30대','40대','50대','60대'))
plt.yticks([0,10,20,30,40,50])
# x,y축 제목
plt.xlabel('x축제목')
plt.ylabel('y축제목')
# 그리드 표시
plt.grid(True)


# Plot Number 4
plt.subplot(224) # 서브플랏 4번 (4/4)
# x, y(sin값) 생성
x = np.arange(0,12,0.1)
x
y = np.sin(x)
y
plt.plot(x,np.cos(x),c = 'red') # 코사인 그래프
plt.plot(x, y) # 사인 그래프
plt.grid() # 눈금?격자?
plt.xlabel('time') # x축 이름
plt.ylabel('Amplitude') # y축 이름
plt.title('Example of sine/cosine wave') # 제목


plt.tight_layout(pad=1.5) # 각 plot의 간격 조절
plt.show()
```


​    
![png](/assets/images/output_24_0.png)
​    


---

## 2. bar(), barh(), df.plot() : 막대그래프

### 2-1. 세로 막대 그래프 그리기: bar()
- bar(x,y,color=[],alpha=)
    - color = [] : 색상값 설정
    - alpha = 투명도 설정


```python
# 데이터 생성
y=[2,3,1,4]
x=np.arange(len(y))

z=[2,3]
s=[0,1]

e=[1,4]
h=[2,3]

xlabel=['가','나','다','라']
```


```python
# 막대그래프 그리기
plt.title('Bar Chart')
plt.bar(x,y)
plt.xticks(x,xlabel)
plt.yticks(sorted(y))
plt.text(-0.1, 1, r'test')
plt.xlabel('가나다라')
plt.ylabel('빈도수')
plt.plot(s, z, color='green',linestyle='dashed',marker='o')
plt.plot(h, e, color='green',linestyle='dashed',marker='o')

plt.show()



# r'문자열 : 문자열 렌더링 rowformat으로 랜더링하는 명령
# rowformat : 장치에서 가장 표준 형태로 변환
```


​    
![png](/assets/images/output_29_0.png)
​    


### 2-2. 가로 막대 그래프 그리기 : barh()
- barh(x,y,color=[], alpha=)


```python
np.random.seed(0)
people=['몽룡','춘향','방자','향단']
y=np.arange(len(people))
performance = 3+ 10 * np.random.rand(len(people))

# 가로 막대그래프 그리기
plt.title("Barh Chart")
plt.barh(y, performance, alpha=0.4)
plt.yticks(y,people)
plt.xlabel('xlabel')
plt.ylabel('ylabel')
plt.grid(True)
plt.show()

```


​    
![png](/assets/images/output_31_0.png)
​    


### 2-3. 데이터프레임으로 막대그래프 그리기
- **데이터프레임.plot**(kind=그래프종류, grid=T/F, figsize=그래프크기)
- **plt.bar**(데이터프레임.변수1, 데이터프레임.변수2)

**데이터프레임.plot()으로 막대그래프 그리기**

- plt.xticks()의 rotation 인수에 따라 가로형 또는 세로형 막대그래프 생성
    - plt.xticks(ticks=None, labels=None, **kwargs)
    - plt.xticks(ticks=None, labels=None) : vertical 기본
    - plt.xticks(ticks=None, labels=None, rotation='vertical') : 가로형막대
    - plt.xticks(ticks=None, labels=None, rotation='horizontal') : 세로형막대


```python
df1 = pd.DataFrame({
    '나이':[15,20,17,50,2,30,23],
    '이름':['둘리','도우너','또치','길동','희동','마이클','영희']
},columns=['나이','이름'])
df1

# xticks 시 위치 표시에 사용할 변수 지정
x=[0,1,2,3,4,5,6] 

# 막대그래프 그리기
df1.plot(kind='bar', grid=True, figsize=(10,10))
plt.xticks(x, df1.이름, rotation='horizontal')
plt.show()

```


​    
![png](/assets/images/output_34_0.png)
​    


**데이터프레임.plot()를 이용하여 묶음 막대그래프 그리기**
- 그래프를 그리기 위한 데이터를 지정하지 않는 경우
- 데이터프레임에 있는 모든 수치데이터를 이용하여 묶음 막대그래프를 그림


```python
# 데이터 생성 :df1
df1 = pd.DataFrame({
    '나이':[15,20,17,50,2,30,23],
    '키' : [165,150,151,175,80,175,185],
    '이름':['둘리','도우너','또치','길동','희동','마이클','영희']
},columns=['나이','키','이름'])

# xticks 시 위치 표시에 사용할 변수
x=[0,1,2,3,4,5,6] 

# df.plot()으로 막대그래프 그리기
df1.plot(kind='bar',grid=True,figsize=(10,10))
plt.xticks(x,df1.이름,rotation='horizontal')
plt.show()

```


​    
![png](/assets/images/output_36_0.png)
​    


**plt.bar(데이터프레임)를 이용하여 막대그래프 그리기**


```python
# 데이터프레임으로 막대그래프 그리기2 : plt.bar(데이터프레임)
# 데이터 생성 :df1
# plt.bar()로 막대그래프 그리기
df1 = pd.DataFrame({
    '나이':[15,20,17,50,2,30,23],
    '키' : [165,150,151,175,80,175,185],
    '이름':['둘리','도우너','또치','길동','희동','마이클','영희']
},columns=['나이','키','이름'])

# plt.bar()로 막대그래프 그리기
plt.bar(df1.이름,df1.나이)
plt.show()

```


​    
![png](/assets/images/output_38_0.png)
​    


**데이터프레임의 일부 필드를 데이터프레임으로 추출하여 그래프 작성**


```python
# 데이터 생성 : df1
df1 = pd.DataFrame({
    '나이':[15,20,17,50,2,30,23],
    '키' : [165,150,151,175,80,175,185],
    '이름':['둘리','도우너','또치','길동','희동','마이클','영희']
},columns=['나이','키','이름'])

# xticks 시 위치 표시에 사용할 변수
x=[0,1,2,3,4,5,6] 

# 막대그래프 그리기
df1[['키']].plot(kind='bar',grid=True,figsize=(10,10))
plt.xticks(x,df1.이름,rotation='horizontal')
plt.show()

```


​    
![png](/assets/images/output_40_0.png)
​    


**정렬된 데이터를 이용하여 막대그래프 그리기**


```python
# 정렬된 데이터를 이용하여 막대그래프 그리기

# 데이터 생성 : df1 
df1 = pd.DataFrame({
    '나이':[15,20,17,50,2,30,23],
    '이름':['둘리','도우너','또치','길동','희동','마이클','영희']
},columns=['나이','이름'])
 
# xticks 시 위치 표시에 사용할 변수
a=[0,1,2,3,4,5,6] 

# 나이로 df1 정렬하여 새로운 df2 생성
df2=df1.sort_values(by='나이')
df2

# 가로 막대그래프 그리기
df1.sort_values(by='나이').plot(kind='barh',grid=True,figsize=(5,5))

plt.yticks(a, df1.sort_values(by='나이').이름, rotation='horizontal')
plt.show()
```


​    
![png](/assets/images/output_42_0.png)
​    


## 3. scatter() : 산점도

- 두 수치형 변수간의 관계를 나타내기 위해 사용하는 그래프
    - 상관관계 표현 : 선형성


```python
# 데이터 생성
t = np.array([0,1,2,3,4,5,6,7,8,9])
y = np.array([9,8,7,9,8,3,2,4,3,4])
```


```python
# 산점도 그리기
plt.scatter(t,y)
plt.show()
```


​    
![png](/assets/images/output_46_0.png)
​    


- 산점도의 marker 변경


```python
# 산점도에 marker 변경
plt.figure(figsize=(10,6))
plt.scatter(t,y,marker='>') #마커지정
plt.show()

```


​    
![png](/assets/images/output_48_0.png)
​    


#### 버블차트
- 점의 크기와 색상을 이용하여 서로 다른 데이터 값을 표시하는 그래프
- scatter(c, s)를 이용하여 작성
    - s 인수 : size
    - c 인수 : color


```python
# 데이터 생성
N=30
np.random.seed(0)
x=np.random.rand(N)
y1 =np.random.rand(N)
y2 =np.random.rand(N)
y3=np.pi *(15 * np.random.rand(N))**2

# 버블차트 그리기
plt.title("Bubble Chart")
plt.scatter(x,y1,c=y2,s=y3)
plt.show()

```


​    
![png](/assets/images/output_50_0.png)
​    


#### 산점도에 colorbar() 적용
- 산점도를 그린 후 colorbar()를 생성하여 색상 정보를 막대로 표현


```python
# colorbar()을 이용해서 산점도 그리기
colormap = t

plt.figure(figsize=(10,6))
plt.scatter(t,y, s=50, c=colormap, marker='>')
plt.colorbar() # 색상 데이터를 bar 형태로 출력
plt.show()

```


​    
![png](/assets/images/output_52_0.png)
​    


## 4. hist() : 히스토그램

- 연속형 수치형 데이터의 분포 시각화
- 참고. 막대그래프는 범주형 데이터의 빈도(비율) 분포 시각화


```python
# 데이터 생성
np.random.seed(0)
x = np.random.randn(1000) #난수 1000개 발생

# 히스토그램 그리기
plt.figure(figsize=(10,6))
plt.title('Histogram')
plt.hist(x)
plt.show()
```


​    
![png](/assets/images/output_55_0.png)
​    


## 5. boxplot() : 박스플롯

- 데이터의 분포를 파악해주는 플롯
    - 최소값, 제1사분위수, 중위수, 제3사분위수, 최대값
    
- 이상치 데이터 탐색을 위해 사용


```python
# 다차원 array 형태로 무작위 샘플을 생성
# np.random.normal(정규분포평균,표준편차,(행열) or 개수)
# 정규분포 확률 밀도에서 표본 추출해주는 함수
# 데이터 3개 생성
s1=np.random.normal(loc=0,scale=1,size=1000)
s2=np.random.normal(loc=5,scale=0.5,size=1000)
s3=np.random.normal(loc=10,scale=2,size=1000)

```


```python
# boxplot 그리기
plt.figure(figsize=(10,6))
plt.boxplot((s1,s2,s3))
plt.grid()
plt.show()
```


​    
![png](/assets/images/output_59_0.png)
​    


## 6. pie() : 파이차트 

- 범주형 데이터의 빈도(비율)을 비교하기 위해 사용하는 차트
- 원의 형태를 유지할 수 있도록 다음 명령을 실행해야 함
    - plt.axis('equal')
    - 콘솔에서는 별 다른 변화 없으나 plot창에서는 필요함


```python
# 데이터 생성
labels=['개구리','돼지','개','통나무']
size=[15, 30, 45, 10]
colors=['yellowgreen','gold','lightskyblue','lightcoral']
explode=(0,0.4,0,0.5)

# plot 그리기
plt.figure(figsize=(10,6))
plt.title('Pie Chart')
plt.pie(size, explode=explode, labels=labels, colors=colors,
       autopct='%1.1f%%', shadow=True, startangle=90)
plt.axis('equal') # 원의 형태 유지 설정
plt.show()

```


​    
![png](/assets/images/output_62_0.png)
​    

