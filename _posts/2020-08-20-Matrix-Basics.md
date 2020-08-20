---
layout: post
title: 급할 때 보기 위한 Matrix Basics
date:   2020-08-20 14:00:00 +0900
categories:
  - ETCs
tags: 
  - machine learning
  - math
use_math: true
---

## 행렬 (Matrix)

- 행렬: 수 또는 식을 사각형의 배열로 나열한 것
- 행렬의 차원 (행렬의 크기) = 행의 개수 x 열의 개수
- $A_{ij}$ : $i$번째 행, $j$번째 열에 있는 원소
- $\mathbb{R}$ : 실수의 집합
- $\mathbb{R}^{n\times m}$ : 실수를 원소로 가지는 $n \times m$ 행렬

---

**EX**

$$
A = \begin{bmatrix}
1&2&3\\
4&5&6\\
7&8&9
\end{bmatrix}
\\
$$

- $A$의 차원 $= 3 \times 3$
- $A_{11} = 1,\;A_{12} = 2,\;A_{21} = 4$

---

<br>

## 벡터 (Vector)

- 벡터 : $n \times 1$ 형태의 행렬
- $v_i$ : 벡터 $v$의 $i$번째 원소
- $\mathbb{R}^n$ : 실수를 원소로 가지는 크기가 $n$인 벡터

---

**EX**  

$$
v = \begin{bmatrix}
1\\2\\3
\end{bmatrix}
\\
$$

- $v$의 크기 : 3
- $v_1 = 1,\; v_2 = 2$

---

<br>

<br>

## 행렬의 연산

#### 행렬의 덧셈/뺄셈

행렬의 각 원소끼리 더하고 뺀다. 크기가 같은 행렬만 더하고 뺄 수 있다.

---

**EX**  

$$
\begin{bmatrix}
a&b\\c&d
\end{bmatrix}
+
\begin{bmatrix}
w&x\\y&z
\end{bmatrix}
=
\begin{bmatrix}
a+w&b+x\\c+y&d+z
\end{bmatrix}
\\
$$

$$
\begin{bmatrix}
a&b\\c&d
\end{bmatrix}
-
\begin{bmatrix}
w&x\\y&z
\end{bmatrix}
=
\begin{bmatrix}
a-w&b-x\\c-y&d-z
\end{bmatrix}
\\
$$

---

<br>

#### 스칼라(scalar)와 행렬의 곱셈/나눗셈

- 스칼라 : 실수와 같이 하나의 값을 가지는 수 (행렬은 여러 개의 값을 가진다.)

행렬을 스칼라로 곱하거나 나눌 수 있다. 모든 원소를 스칼라 값으로 곱하거나 나눈다.

---
**EX**  

$$
\begin{bmatrix}
a&b\\c&d
\end{bmatrix}
\times x = 
\begin{bmatrix}
a\times x&b\times x\\c \times x&d \times x
\end{bmatrix}
$$

$$
\begin{bmatrix}
a&b\\c&d
\end{bmatrix}
\div x = 
\begin{bmatrix}
a\div x&b\div x\\c \div x&d \div x
\end{bmatrix}
\\
$$

---

<br>

#### 행렬과 벡터의 곱셈

행렬의 크기가 $m \times n$이고 벡터의 크기가 $n \times 1$일 때, 행렬과 벡터를 곱할 수 있다. 결과는 $m \times 1$인 벡터이다. 

---

**EX**  

$$
\begin{bmatrix}
a&b\\c&d\\e&f
\end{bmatrix}
\times
\begin{bmatrix}
x\\y
\end{bmatrix}
=
\begin{bmatrix}
a \times x + b \times y\\
c \times x + d \times y\\
e \times x + f \times y
\end{bmatrix}
\\
$$

---

<br>

#### 행렬과 행렬의 곱셈

크기가 $m \times n$인 행렬과 크기가 $n \times o$인 행렬을 곱할 수 있다. 결과는 $m \times o$인 행렬이다. 

---

**EX**  

$$
\begin{bmatrix}
a&b\\c&d\\e&f
\end{bmatrix}
\times
\begin{bmatrix}
w&x\\y&z
\end{bmatrix}
=
\begin{bmatrix}
a \times w + b \times y&a \times x + b \times z\\
c \times w + d \times y&c \times x + d \times z\\
e \times w + f \times y&e \times x + f \times z\\
\end{bmatrix}
\\
$$


---

<br>

#### 행렬의 곱의 성질

- 교환 법칙이 성립하지 않는다.

  $A \times B \neq B \times A$

- 결합 법칙이 성립한다.

  $(A \times B) \times C = A \times (B \times C)$

<br>

<br>

## 단위행렬, 역행렬, 전치행렬

#### 단위행렬 $I$ (Identity Matrix)

- 실수에서 1과 같이, 모든 행렬 $A$에 대해 $A \times I = A$를 만족시키는 행렬 $I$

  $A \times I = I \times A = A$

---

$$
I =
\begin{bmatrix}
1&0\\0&1\\
\end{bmatrix}
\begin{bmatrix}
1&0&0\\0&1&0\\0&0&1\\
\end{bmatrix}
\begin{bmatrix}
1&0&0&0\\0&1&0&0\\0&0&1&0\\0&0&0&1
\end{bmatrix}
\\
$$

---

<br>

#### 역행렬 $A^{-1}$ (Inverse Matrix)

- 행렬 $A$에 대해 $A \times A^{-1} = I$인 행렬 $A^{-1}$
- $m \times m$의 행렬만 역행렬을 가질 수 있다.

---

**EX**  

$$
A = \begin{bmatrix}
4&3\\3&2\\
\end{bmatrix}
\;\;\;\;\;\;\;\;\;\;\;\;\;\;
A^{-1} = \begin{bmatrix}
-2&3\\3&-4\\
\end{bmatrix}
\\
$$

$$
A \times A^{-1} = 
\begin{bmatrix}
4&3\\3&2\\
\end{bmatrix}
\begin{bmatrix}
-2&3\\3&4\\
\end{bmatrix}
=
\begin{bmatrix}
1&0\\0&1\\
\end{bmatrix}
\\
$$

---

<br>

#### 전치행렬 $A^T$ (Transpose Matrix)

- 행렬 $A$의 행과 열이 뒤바뀐 행렬 $A^T$

  $A_{ij}^T = A_{ji}$

---

$$
A =
\begin{bmatrix}
a&b\\c&d\\e&f\\
\end{bmatrix}
\;\;\;\;\;
A^T = \begin{bmatrix}
a&c&e\\b&d&f\\
\end{bmatrix}
\\
$$

---

 <br>

<br>

---

 이 글은 Coursera의 Machine Learning (Andrew Ng) 강의 내용을 정리한 것입니다.  
 <https://www.coursera.org/learn/machine-learning/home/welcome>  
 <br>

