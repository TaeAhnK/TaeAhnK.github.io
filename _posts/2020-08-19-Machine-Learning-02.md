---
layout: post
title: "[ML] 3. 회귀와 선형 회귀"
date: 2020-08-19 15:00:00 +0900
categories:
  - Machine Learning
tags: 
  - machine learning
use_math: true

---
Coursera > Machine Learning (Andrew Ng) > Week 1  

---

# 회귀 (Regression)

&nbsp;&nbsp;&nbsp;&nbsp;회귀의 경우, 학습 예제를 학습 알고리즘에 대입하면 가설 함수 $h (hypothesis)$를 구할 수 있다. 가설 함수 $h$의 형태에 따라 선형 회귀와 다항 회귀 등으로 분류할 수 있다. $h$에 새로운 데이터 $x$를 대입하면 결과 $y$를 예측할 수 있다. 이 과정을 도식화하면 아래 그림과 같다.

$$
\begin{align*}
 Trai&ning\;Set \\
 &\downarrow\\
  Learning&\;Algorithm \\
 &\downarrow \\
 x\;\rightarrow&\;h \rightarrow \; predicted\;y
\end{align*}
\\
$$

&nbsp; &nbsp; &nbsp; &nbsp; 예를 들어, 평수를 통해 집의 가격을 예측한다고 하자. 먼저 우리는 여태까지 판매된 집의 가격과 평수의 데이터를 살펴볼 것이다. 데이터를 통해 평수와 가격의 관계를 나타내는 적당한 가설 함수를 도출하고, 함수에 예측하고자 하는 평수를 대입해 집의 가격을 예측할 것이다.  
<br>

# 1. 선형 회귀

## 1.1 선형 회귀의 표기

&nbsp;&nbsp;&nbsp;&nbsp;다양한 개념을 수식으로 표현하기 위해 아래와 같은 표기를 사용한다.

$m$ : 학습 예제의 개수  
$x's$ : 입력 변수/특성  
$y's$ : 출력 변수/특성  
$(x, y)$ : 학습 예제 한 쌍  
$(x^{(i)}, y^{(i)})$ : $i$번째 학습 예제  

&nbsp;&nbsp;&nbsp;&nbsp;선형 회귀 모델의 함수 $h$는 직선의 형태로, 다음과 같은 일반식을 가진다.

$$
h(x) = \theta_0 + \theta_1x\\
\\
$$

$h(x)$는 $x$에 관한 식으로, 학습 알고리즘을 통해 $\theta$를 구한다.  
<br>


## 1.2 비용함수 (Cost Function)

&nbsp;&nbsp;&nbsp;&nbsp; 학습 알고리즘을 통해 도출한 가설 함수 $h$는 비용함수를 통해 정확도를 측정할 수 있다. 가설 함수는 가설 함수의 결과 $h(x)$와 실제 결과 $y$의 차(오차)가 작을수록 정확하다고 할 수 있다. 따라서 다음 식을 통해 정확도를 측정할 수 있다.

$$
J(\theta_0, \theta_1) = \frac{1}{2m}\displaystyle\sum_{i=1}^{m}(\hat{y_i} - y_i)^2 = \frac{1}{2m}\displaystyle\sum_{i=1}^{m}(h_\theta(x_i) - y_i)^2
\\
$$

&nbsp;&nbsp;&nbsp;&nbsp; $h(x)$를 $x$에 관한 식의 입장에서 보면 $\theta$를 계수로 가지는 입력 변수 $x$에 대한 식이다. 즉, 함수의 모양을 결정하는 것은 $\theta$이며, 정확도 $J$또한 $\theta$에 의해 결정된다. 따라서, $J(\theta_0, \theta_1)$를 비교하여 가장 오차가 작은 $\theta$를 구할 수 있다.

&nbsp;&nbsp;&nbsp;&nbsp;모든 $h(x)$와 $y$의 차를 제곱해 더한 뒤, 이를 학습 예제의 개수로 나누어 평균을 구하고, 다시 2로 나눈다. 제곱해 나누는 이유는 차가 제일 작은, 즉, 절댓값이 제일 작은 값을 구하기 위해서이다. 2로 나누는 이유는 미분할 때의 편의를 위해서이다. 이 함수를 "Squared Error Function" 혹은 "Mean Squared Error"라고 부르며, $J(\theta_1)$이 가장 작은 지점이 $h(\theta_0)$이 가장 잘 예측한 지점이다. 

<center><img src="\assets\images\2020-08-19-Machine-Learning-02-01.PNG" width="500px" height="500px" align=center>
</center>

&nbsp;&nbsp;&nbsp;&nbsp;위와 같은 예제(빨간 X)가 있다고 가정해보자. 학습 알고리즘을 통해 $h_1(x) = x$ (파랑), $h_2 = \frac{2}{3}x$ (초록)를 구했다.  $h_1$의 $\theta_1$은 $1$, $h2$의 $\theta_1$은 $\frac{2}{3}$이다.

$$
\begin{align*}
J_1 &= \frac{1}{2m}\displaystyle\sum_{i=1}^{m}(h_1(x_i) - y_i)^2 \\ \\
&= \frac{1}{6}\big\{ (1-1)^2 + (2-2)^2 + (3-3)^2\big\} \\ \\
&= \;0 \\ \\
J_2 &= \frac{1}{2m}\displaystyle\sum_{i=1}^{m}(h_2(x_i) - y_i)^2 \\ \\
&= \frac{1}{6}\big\{ (\frac{2}{3}-1)^2 + (\frac{4}{3}-2)^2 + (2-3)^2\big\} \\ \\
&\approx  \;0.26 \\
\end{align*}
\\
$$

이때, $h_1$의 오차는 0, $h_2$의 오차는 0.26이다. 모든 $\theta$에 대한 $J$의 그래프를 그리면 다음과 같다.

<center><img src="\assets\images\2020-08-19-Machine-Learning-02-02.PNG" width="500px" height="500px" align=center>
</center>

<br>

<center><img src="\assets\images\2020-08-19-Machine-Learning-02-03.PNG" width="500px" height="500px" align=center>
</center>

&nbsp;&nbsp;&nbsp;&nbsp; $\theta_0$와 $\theta_1$을 모두 사용하는 경우를 보자. 가설 함수는 $h_1 = x+\frac{1}{2}$, $h_2 = \frac{2}{3}x + 1$이다. 이 경우의 오차는 

$$
\begin{align*}
J_1 &= \frac{1}{2m}\displaystyle\sum_{i=1}^{m}(h_1(x_i) - y_i)^2 \\ \\
&= \frac{1}{6}\big\{ (\frac{3}{2}-1)^2 + (\frac{5}{2}-2)^2 + (\frac{7}{2}-3)^2 + (\frac{9}{2}-3)^2 + (\frac{11}{2}-3)^2\big\} \\ \\
&\approx \;0.93 \\ \\
J_2 &= \frac{1}{2m}\displaystyle\sum_{i=1}^{m}(h_2(x_i) - y_i)^2 \\ \\
&= \frac{1}{10}\big\{ (\frac{5}{3}-1)^2 + (\frac{7}{3}-2)^2 + (3-1)^2 + (\frac{11}{3}-1)^2 + (\frac{13}{3}-1)^2\big\} \\ \\
&\approx  \;2.44 \\
\end{align*}
\\
$$

이다. 모든 $\theta_0$, $\theta_1$에 대해 $J(\theta_0, \theta_1)$를 구해 그래프로 나타내면 아래와 같은 3차원 곡면 모양이다.

<center><img src="\assets\images\2020-08-19-Machine-Learning-02-04.PNG" width="500px" height="500px" align=center>
</center>

$J$가 0에 가까운 진한 파란색일수록 더 정확한 $(\theta_0, \theta_1)$ 쌍이다. 곡면을 더 편하게 보기 위해 등고선으로 나타내면 다음과 같다.

<center><img src="\assets\images\2020-08-19-Machine-Learning-02-05.PNG" width="500px" height="500px" align=center>
</center>

같은 색의 곡선은 같은 $J$를 가진다. 타원의 중심에 가까울수록 $J$가 작고, 더 정확하다고 할 수 있다. $h_1$이 $h_2$보다 중심에 가까우므로 $h_1$이 더 정확한 가설 함수이다.  
<br>


## 1.3 선형 회귀의 경사 하강법 (Gradient Descent)

경사 하강법은 비용 함수의 최솟값을 구하기 위한 알고리즘이다. 

<center><img src="\assets\images\2020-08-19-Machine-Learning-02-06.PNG" width="500px" height="500px" align=center>
</center>

경사 하강법을 이용해 최솟값을 찾는 경우, 임의의 $(\theta_0, \theta_1)$ 쌍을 하나 정한 다음, 그 값을 계속 변경해 더 작은 $J$를 찾는다. 그리고 더 이상 더 작은 값을 찾을 수 없을 때까지 반복한다. 이때, 함수 위의 점에서의 접선(미분, 도함수)을 통해 다음 이동 좌표를 구할 수 있다. 도함수의 기울기가 가장 큰 방향으로 이동하면 최솟값에 도달할 수 있다.

이를 수식으로 표현하면 다음과 같다.

$$
\begin{align*}
&repeat\;until\;convergence:\\
&\theta_j := \theta_j - \alpha\frac{\partial}{\partial\theta_j}J(\theta_0, \theta_1)\\
(&for\;j=0\;and\;j=1)
\end{align*}
\\
$$

$\alpha$는 학습 속도(Learning Rate)로, 한 번에 얼마만큼 내려가는지를 결정한다.  
$:=$는 C언어에서 값을 저장하는 것과 마찬가지로 $\theta_j$에 우변의 값을 할당함을 의미한다.  
$\frac{\partial}{\partial\theta_j}J(\theta_0, \theta_1)$는 미분 계수이다. 알고리즘 실행 시 $\theta_0$, $\theta_1$을 모두 구하고 동시에 업데이트해야 변경된 $\theta_0$값이 $\theta_1$을 계산할 때 사용되지 않는다.  

<center><img src="\assets\images\2020-08-19-Machine-Learning-02-07.PNG" width="500px" height="500px" align=center>
</center>

&nbsp;&nbsp;&nbsp;&nbsp;이차함수에 위의 임의의 점에서 시작해보자. 점에서의 접선은 기울기가 양수인 직선이다. 기울기가 양수이므로 $- \alpha\frac{\partial}{\partial\theta_j}J(\theta_0, \theta_1)$는 음수가 되며, $\theta$는 점점 작아진다. 이때, 작아지는 정도는 Learning Rate가 결정한다. 반대로 접선이 음수인 경우, $- \alpha\frac{\partial}{\partial\theta_j}J(\theta_0, \theta_1)$는 양수가 되어 $\theta$는 점점 커진다. 그리고 접선이 0일 경우, 더 변화하지 않는다. 이때, $\theta_1\approx\theta_1$이며, 알고리즘이 종료된다.

&nbsp;&nbsp;&nbsp;&nbsp; $\frac{\partial}{\partial\theta_j}J(\theta_0, \theta_1)$는 최솟값에 가까워질수록 0에 가까워진다. 따라서 $\alpha\frac{\partial}{\partial\theta_j}J(\theta_0, \theta_1)$는 최솟값에 가까워질수록 조금 변화한다. 두 변수를 사용해 자동으로 최솟값에 수렴할 수 있어 학습 속도를 수정하지 않고도 최솟값을 구할 수 있다.

<center><img src="\assets\images\2020-08-19-Machine-Learning-02-08.PNG" width="500px" height="500px" align=center>
</center>

&nbsp;&nbsp;&nbsp;&nbsp; 학습 속도가 작을 경우, 경사를 내려오는 속도가 느리다. 그러나, 학습 속도가 너무 클 경우, 최적값을 찾지 못하거나, 벗어날 수도 있다.

<center><img src="\assets\images\2020-08-19-Machine-Learning-02-09.PNG" width="500px" height="500px" align=center>
</center>


위에서 선형 회귀 모델의 일반식 $h(x)$와 비용 함수 $J(\theta)$를 설명했다. 비용 함수 $J(\theta)$를 경사 하강법에 대입해 최소화해보자.

먼저, 미분 계수를 단순화하면,

$$
\begin{align*}
\frac{\partial}{\partial\theta_j}J(\theta) &= \frac{\partial}{\partial\theta_j}\frac{1}{2m}\sum_{i=1}^{m}\big(h_\theta(x^{(i)})-y^{(i)}\big)^2 \\
&= \frac{\partial}{\partial\theta_j}\frac{1}{2m}\sum_{i=1}^{m}\big(\theta_0 + \theta_1x^{(i)}-y^{(i)}\big)^2 \\ \\
j = 0 :\;\;\;\;\frac{\partial}{\partial\theta_j}J(\theta) &= \frac{1}{m}\sum_{i=1}^{m}\big(h_\theta(x^{(i)})-y^{(i)}\big)^2 \\
j = 1 :\;\;\;\;\frac{\partial}{\partial\theta_j}J(\theta) &= \frac{1}{m}\sum_{i=1}^{m}\big(h_\theta(x^{(i)})-y^{(i)}\big)^2 x^{(i)} \\
\end{align*}
\\
$$

이다. 이 식을 경사 하강법에 대입하면,

$$
\begin{align*}
&repeat\;until\;convergence\;\{\\
&\theta_0 := \theta_0 - \alpha\frac{1}{m}\sum_{i=1}^{m}\big(h_\theta(x^{(i)})-y^{(i)}\big)^2\\
&\theta_1 := \theta_1 - \alpha\frac{1}{m}\sum_{i=1}^{m}\big(h_\theta(x^{(i)})-y^{(i)}\big)^2 \cdot x^{(i)}\\
\}
\end{align*}
\\
$$

이다.

<center><img src="\assets\images\2020-08-19-Machine-Learning-02-10.PNG" width="500px" height="500px" align=center>
<img src="\assets\images\2020-08-19-Machine-Learning-02-11.PNG" width="500px" height="500px" align=center>
</center>

&nbsp;&nbsp;&nbsp;&nbsp; 모양이 복잡한 함수의 경우 $(\theta_0, \theta_1)$의 시작값에 따라 결과가 달라질 수도 있다. 그러나 선형 회귀의 비용 함수는 항상 아래로 볼록한 모양을 띠기 때문에 반드시 최솟값을 향해 수렴한다.

&nbsp;&nbsp;&nbsp;&nbsp; 이처럼 매 단계 모든 학습 예제를 확인하는 방법을 배치 경사 하강법 (Batch Gradient Descent: BGD)라고 한다.  


<br>

***

<br>
이 글은 Coursera의 Machine Learning (Andrew Ng) 강의 내용을 정리한 것입니다.  
<https://www.coursera.org/learn/machine-learning/home/welcome>  
수식이 길어 모바일 환경에서 잘릴 수 있습니다. 긴 수식은 스크롤을 지원합니다.  
<br>






