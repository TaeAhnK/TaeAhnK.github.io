---
layout: post
title: "[ML] 1. 머신러닝이란, 2. 지도 학습과 비지도 학습"
date: 2020-08-11 15:00:00 +0900
categories:
  - Machine Learning
tags: 
  - machine learning
use_math: true

---
Coursera > Machine Learning (Andrew Ng) > Week 1  

***

<br>
# 1. 머신 러닝(Machine Learning)이란?

&nbsp;&nbsp;&nbsp;&nbsp;머신 러닝에 대한 명확하게 약속된 정의는 없다. 보통 "머신 러닝"이라는 용어를 대중화한 아서 사무엘 (Arthur Lee Samuel) 교수의 정의와 톰 미첼 (Tom Mitchell) 교수의 정의를 사용한다.  

&nbsp;&nbsp;&nbsp;&nbsp;아서 사무엘 교수는 머신 러닝을 다음과 같이 설명했다.
 <center> <i>"A field of study that gives computers the ability to learn without being explicitly programmed."(1959)   
<br>
 "컴퓨터가 특정 행동을 하도록 프로그래밍하지 않고, 스스로 학습할 수 있게 하는 학문"</i>  
</center> <br>

 &nbsp;&nbsp;&nbsp;&nbsp;톰 미첼 교수는 머신 러닝을 이렇게 정의한다.
 <center> <i> "A computer program is said to learn 
	from experience \(E\) 
	with respect to some task \(T\) 
	and some performance measure \(P\), 
	if its performance of \(T\), as measured by \(P\), improves with experience \(E\)." (1998)   
<br>
"컴퓨터 프로그램이 작업($T$)의 성능($P$)을 경험($E$)을 통해 향상시켰을 때, 컴퓨터 프로그램이 학습(Learn)했다고 할 수 있다." </i>
</center>  

<br>
>얼굴을 인식하는 프로그램이 있다고 가정해보자.  
얼굴 사진을 보고 사진이 나의 얼굴인지 분류하는 작업을 $T$라고 할 수 있다.  
이 프로그램이 얼마나 정확하게 얼굴을 인식하는 지를 $P$라고 할 수 있다.  
여러가지 얼굴 사진과 사진의 주인공의 이름을 컴퓨터 프로그램에 입력했다. 이를 $E$라고 할 수 있다.
사진 데이터를 통해 컴퓨터 프로그램이 나의 얼굴을 더 잘 인식한다면, 컴퓨터 프로그램은 학습한 것이다.



<br>

***

<br>
# 2. 지도 학습과 비지도 학습
#### 머신 러닝 알고리즘
- 지도 학습 (Supervised Learning)
- 비지도 학습 (Unsupervised Learning)
- ...

 &nbsp;&nbsp;&nbsp;&nbsp; 머신 러닝의 알고리즘은 크게 지도 학습과 비지도 학습으로 구분된다.  
<br>

## 2.1 지도 학습 (Supervised Learning)

 &nbsp;&nbsp;&nbsp;&nbsp; 지도 학습은 가장 흔히 쓰이는 머신 러닝 알고리즘이다. 알고리즘에 특정 입력에 대한 정답을 주기 때문에 "지도"라는 표현을 사용한다. 다시 말해, 입력에 대한 올바른 결과를 알고 있다. 여기서 알고리즘의 역할은 입력과 출력의 관계를 통해 다른 입력에 대해서도 올바른 결과를 찾는 것이다.  
<br>

 > 집의 평수를 통해 집값을 예측해보자. 이때, 미리 알고 있는 집의 평수와 가격 데이터를 통해 평수와 가격의 관계를 파악할 수 있다. 파악한 관계를 통해 정답이 주어지지 않은 데이터의 가격도 예측할 수 있다.  

<br>

#### 지도 학습을 통해 해결할 수 있는 문제
- 회귀 (Regression Problem)
- 분류 (Classification Problem)  

### 회귀 (Regression)
 &nbsp;&nbsp;&nbsp;&nbsp; 알고리즘을 통해 연속된 값을 가진 결과를 예측하는 문제를 "회귀"라고 한다. 입력값을 연속 함수에 매칭시키면 함수를 통해 입력에 따른 연속된 출력을 구할 수 있다.  
<br>

<center><img src="\assets\images\2020-08-11-Machine-Learning-01-01.PNG" width="300px" height="300px" align=center>
</center>

>위에서 사용한 집값의 예시가 회귀이다. 집의 가격은 집마다 모두 다른 연속적인 값이다. 평수를 $x$, 가격을 $y$라고 했을 때 $x$에 대한 $y$의 대략적인 연속 함수를 구할 수 있고, 이 함수를 통해 입력에 따라 다른 집의 가격을 예측할 수 있다.  

<br>

### 분류 (Classification)
 &nbsp;&nbsp;&nbsp;&nbsp; 알고리즘을 통해 이산적인 값을 가진 결과를 예측하는 문제를 "분류"라고 한다. 입력값을 이산적인 카테고리에 매칭시키면 함수를 통해 결과를 분류할 수 있다.  
<br>

<center><img src="\assets\images\2020-08-11-Machine-Learning-01-02.PNG" width="300px" height="300px" align=center>
</center> 

>종양의 크기와 나이에 따른 암의 양성/음성 결과를 예측해보자. 이때의 결과는 양성 혹은 음성의 이산적인 값이다. 종양의 크기와 나이에 관한 대략적인 함수를 통해 양성과 음성을 분류할 수 있다.

<br>
## 2.2 비지도 학습 (Unsupervised Learning)
 &nbsp;&nbsp;&nbsp;&nbsp; 비지도 학습은 지도 학습과 다르게 정답을 미리 주지 않는다. 변수가 어떤 효과를 가지는지 알지 못하더라도 구조를 구할 수 있으며, 결과가 어떤 값일지 모르는 문제에 접근할 수 있다.  

### 군집화 (Clustering Algorithm)
 &nbsp;&nbsp;&nbsp;&nbsp; 변수의 관계를 바탕으로 변수를 군집화해 구조를 구할 수 있다.  

<center><img src="\assets\images\2020-08-11-Machine-Learning-01-03.PNG" width="600px" height="300px" align=center>
</center>
>데이터가 그림과 같은 모양을 보인다고 할 때, 오른쪽과 같이 원소들을 묶을 수 있다. 묶인 원소를 바탕으로 구조를 추론할 수 있다.

 ***
 <br>
 이 글은 Coursera의 Machine Learning (Andrew Ng) 강의 내용을 정리한 것입니다.  
 <https://www.coursera.org/learn/machine-learning/home/welcome>  
 <br>