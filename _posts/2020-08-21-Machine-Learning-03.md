---
layout: post
title: "[ML] 4. 다변수 선형 회귀와 다항 회귀"
date: 2020-08-21 21:00:00 +0900
categories:
  - Machine Learning
tags: 
  - machine learning
use_math: true
---

Coursera > Machine Learning (Andrew Ng) > Week 2  

---

# 2. 다변수 선형 회귀

&nbsp;&nbsp;&nbsp;&nbsp;이전에 예시로 사용한 $h(x)= \theta_0 + \theta_1x$ 는 변수가 1개였다. 선형 회귀에선 더 많은 변수를 사용해 예측 함수를 만들 수 있는데 이를 다변수 선형 회귀 (Multivariate Linear Regression)라고 한다.  


## 2.1 다변수 선형 회귀의 예측 함수

&nbsp;&nbsp;&nbsp;&nbsp;먼저 아래의 개념을 다음과 같이 정의한다.

- $n$ : 변수의 개수
- $m$ : 학습 예제의 개수
- $x^{(i)}$ : $i$번째 학습 예제의 입력 변수
- $x_j^{(i)}$ : $i$번째 학습 예제의 변수 $j$의 값

&nbsp;&nbsp;&nbsp;&nbsp;이때, 예측 함수의 일반식은

$$
h\theta(x) = \theta_0 + \theta_1x_1 + \theta_2x_2 + \dots + \theta_nx_n \\
$$

이다. 편의를 위해 $x_0$를 추가하고 $x_0 = 0$으로 정의하면 아래와 같이 정리할 수 있다.

$$
\begin{align*}
h\theta(x) &= \theta_0x_0 + \theta_1x_1 + \theta_2x_2 + \dots + \theta_nx_n
\\
\\&= [\theta_0 \; \theta_1 \; \theta_2 \; \dots \; \theta_n] \begin{bmatrix}
x_0 \\
x_1 \\
x_2 \\
\dots \\
x_n \\
\end{bmatrix} \\
\\&= \theta^Tx
\end{align*}
\\
$$

<br>

## 2.2 변수의 추가

&nbsp;&nbsp;&nbsp;&nbsp;변수를 추가하는 방법은 두 가지가 있다. 집의 가로 $x_1$에 대한 집값의 가설함수 $h$가 있다고 가정해보자.

$$
h_\theta(x) = \theta_0 + (\theta_1\times x_1)
$$

여기에 집의 세로 $x_2$라는 변수를 추가해보자. 방법1은 가설 함수에 변수를 더하는 것이다.

$$
h_\theta(x) = \theta_0 + (\theta_1\times x_1) + (\theta_2\times x_2)
$$

아니면, $x_1$과 $x_2$를 이용해 새로운 변수를 만들 수도 있다. 집의 가로 $x_1 \times$ 집의 세로 $x_2$인 집의 넓이 $S$를 구할 수 있다. 이처럼 변수에 따라서 새로운 변수를 만드는 것이 더 효율적인 경우도 있다.

$$
h_\theta(x) = \theta_0 + (\theta_1\times S)
$$


<br>

## 2.3 다변수 선형 회귀의 경사 하강법

&nbsp;&nbsp;&nbsp;&nbsp;변수가 여러 개일 경우에도 경사 하강법의 기본 모양은 같다. 이전 예제에서 $\theta_0$과 $\theta_1$을 업데이트한 것처럼 $n$개의 $\theta$를 모두 업데이트하고 알고리즘을 반복하면 된다.

$$
\begin{align*}
&Repeat\;until\;convergence:\;\{\\
	&\theta_0 := \theta_0 - \alpha\frac{1}{m}\sum_{i=1}^m\big(h_\theta(x^{i}) - y^{(i)}\big) \cdot x_0^{(i)}\\
	&\theta_1 := \theta_1 - \alpha\frac{1}{m}\sum_{i=1}^m\big(h_\theta(x^{i}) - y^{(i)}\big) \cdot x_1^{(i)}\\
	&\theta_2 := \theta_2 - \alpha\frac{1}{m}\sum_{i=1}^m\big(h_\theta(x^{i}) - y^{(i)}\big) \cdot x_2^{(i)}\\
	&\vdots \\
	&\theta_n := \theta_n - \alpha\frac{1}{m}\sum_{i=1}^m\big(h_\theta(x^{i}) - y^{(i)}\big) \cdot x_n^{(i)}\\
	&\}
\end{align*}
\\
$$

$$
\downarrow\\
\begin{align*}
\\&Repeat\;until\;convergence:\;\{\\
	&\theta_j := \theta_j - \alpha\frac{1}{m}\sum_{i=1}^m\big(h_\theta(x^{i}) - y^{(i)}\big) \cdot x_j^{(i)}\\
	&for\;j := 0 \cdots n \\
	&\}
\end{align*}
\\
$$



#### Feature Scaling

&nbsp;&nbsp;&nbsp;&nbsp;변수들의 범위를 조정하면 경사 하강법을 더 편하게 적용할 수 있다.

<center><img src="\assets\images\2020-08-21-Machine-Learning-03-01.PNG" width="700px" height="400px" align=center>
</center>


&nbsp;&nbsp;&nbsp;&nbsp;변수의 범위가 넓고 $x_1$과 $x_2$의 범위 차이가 크게 나는 경우, 왼쪽과 같이 긴 타원 모양의 등고선이 생긴다. 이 경우, 경사 강법을 통해 최솟값을 찾는 데 시간이 많이 소요된다.

&nbsp;&nbsp;&nbsp;&nbsp; $x_1$과 $x_2$를 적절한 수로 나누어 범위를 $-1\leq x_1, x_2\leq1$로 조정해보자. 이 경우, 왼쪽과 같이 원에 가까운 등고선이 생긴다. 이때, 변수의 범위를 조정하지 않았을 때보다 훨씬 빠르게 최솟값을 찾을 수 있다.  

##### Mean Normalization

&nbsp;&nbsp;&nbsp;&nbsp;범위를 조정할 때, 주로 사용하는 방법은 Mean Normalization이다. 변수 $x$대신 아래 공식을 통해 구한 값을 사용한다.


$$
\begin{align*}
&x_i := \frac{x_i - \mu_i}{s_i} \\
\\\mu_i : \;average\;&x_i\\
s_i : range\;of\;&values\;or\;standard\;deviation
\end{align*}
$$


이때, $s_i$에 따라 조정된 $x_i$의 범위가 달라진다.

<br>

#### 학습 속도

&nbsp;&nbsp;&nbsp;&nbsp;경사 하강법의 학습 속도 $\alpha$가 너무 작으면 최솟값을 찾는 속도가 느리고, 너무 크면 값이 왜곡된다. 적절한 $\alpha$를 사용했는지 확인하기 위해 그래프를 그려본다.

<center><img src="\assets\images\2020-08-21-Machine-Learning-03-02.PNG"  width="400px" height="400px" align=center>
</center>

&nbsp;&nbsp;&nbsp;&nbsp;경사 하강법이 제대로 적용된 경우, 알고리즘이 반복되는 동안(Number of Iterations가 커지는 동안) $J(\theta)$가 증가하지 않고, 감소하며 수렴한다. 아래와 같이 $J(\theta)$가 증가하면 경사 하강법이 제대로 이뤄지지 않고 있는 것이다. 이때는 $\alpha$의 값을 줄여야한다. (보통 0.001부터 3씩 곱해가며 조정한다.)

<center><img src="\assets\images\2020-08-21-Machine-Learning-03-03.PNG"  height="400px" align=center>
</center>

&nbsp;&nbsp;&nbsp;&nbsp;Automatic Convergence Test를 통해 $J(\theta)$가 수렴하는지 판단할 수 있다. Automatic Convergence Test는 $J(\theta)$가 한 Iteration 동안 기준 $E$ (예 : $10^{-3}$)보다 적게 감소했다면, $J(\theta)$는 수렴한다고 판단한다.  

<br>

## 2.4 정규 방정식 (Normal Equation)

&nbsp;&nbsp;&nbsp;&nbsp;정규 방정식은 경사 하강법과 마찬가지로 특정 상황에서 비용 함수 $J$의 최솟값을 구할 수 있게 해준다. $J(\theta)$가 $\theta$에 대한 이차함수라고 생각해보자. $J$의 최솟값은 $J$를 $\theta$에 대해 미분하여 0이 되는 지점이다. 그러나 변수가 많은 경우, $J(\theta)$는 $\theta_0\dots\theta_n$ 벡터에 대한 함수이다. 따라서 각각의 $\theta$에 대해 편미분한 뒤, 그 값이 0이 되는 지점을 찾아야 한다. 이때, 다음의 공식을 사용한다.

$$
\theta = (X^TX)^{-1}X^Ty
\\
$$

&nbsp;&nbsp;&nbsp;&nbsp;아래 표와 같은 $m = 4$인 학습 예제가 있다고 하자.

| $x_0$ | $x_1$ | $x_2$ | $x_3$ | $x_4$ | $y$  |
| :---: | :---: | :---: | :---: | :---: | :--: |
|   1   |  21   |   5   |   1   |  45   | 460  |
|   1   |  14   |   3   |   2   |  40   | 232  |
|   1   |  15   |   3   |   2   |  30   | 315  |
|   1   |   8   |   2   |   1   |  36   | 178  |

이를 행렬로 표현하면,

$$
X = \begin{bmatrix}
1&21&5&1&45\\
1&14&3&2&40\\
1&15&3&2&30\\
1&8&2&1&36\\
\end{bmatrix}
\;\;\;\;\;\;
y = \begin{bmatrix}
460\\232\\315\\178
\end{bmatrix}
$$

이다. 이 행렬을 공식에 대입하면,

$$
\theta = \begin{bmatrix}
256.51\\
25.04\\
2.8653\\
-75.94\\
-5.80
\end{bmatrix}
\\
$$

의 $\theta$ 벡터를 구할 수 있다.  

#### 경사 하강법과 정규 방정식의 비교

|          **경사 하강법**          |                     **정규** 방정식                      |
| :-------------------------------: | :--------------------------------------------------: |
|       학습 속도를 정해야 함        |             학습 속도를 정하지 않아도 됨             |
|       알고리즘을 반복해야 함       |               알고리즘을 반복하지 않음               |
|             $O(kn^2)$             |        $O(n^3)$, $X^TX$의 역함수를 계산해야 함        |
| $n$이 커져도 속도가 느려지지 않음 | $n$이 커지면 속도가 느려짐 <br> (ex : $n\geq10,000$) |
|                                   |           변수의 범위를 조정할 필요가 없음           |

<br>

#### 정규 방정식을 쓸 수 없는 경우

역행렬 $(X^TX)^{-1}$이 존재하지 않을 경우, $\theta$를 계산할 수 없다. 역행렬이 존재하지 않는 이유는

1. 불필요한 변수가 있는 경우
2. 변수가 너무 많은 경우

1의 경우 불필요한 변수를 제거해야 한다. 2의 경우 변수를 제거하거나 정규화해야 한다.

###### (정규화는 뒤에서 설명할 예정입니다.)
<br>
<br>

# 3. 다항 회귀

&nbsp;&nbsp;&nbsp;&nbsp;때에 따라선 직선인 가설 함수보다 곡선인 가설 함수가 더 정확하다. $x_i$을 세제곱, 네 제곱을 하거나 제곱근을 씌우는 등 여러 방법을 통해 곡선 형태의 $h(x)$를 구현할 수 있다.

<center><img src="\assets\images\2020-08-21-Machine-Learning-03-04.PNG" width="400px" height="400px" align=center>
</center>

&nbsp;&nbsp;&nbsp;&nbsp;다항 회귀를 사용할 때는 변수의 범위를 신경 써야 한다. $x_1$의 범위가 1에서 1,000까지라도, 제곱은 1에서 1,000,000, 세제곱은 1,000,000,000까지 늘어난다.

<br>

---

<br>
이 글은 Coursera의 Machine Learning (Andrew Ng) 강의 내용을 정리한 것입니다.  
<https://www.coursera.org/learn/machine-learning/home/welcome>  
수식이 길어 모바일 환경에서 잘릴 수 있습니다. 긴 수식은 스크롤을 지원합니다.  
<br>

