---
layout: post
title:  "급할 때 보기 위한 Matlab"
date:   2020-08-18 12:30:00 +0900
categories:
  - ETCs
tags: 
  - matlab
  - machine learning
use_math: false
---
<br>
<br>

## 기본 Commands
	>> % 주석

	>> help		% help cmd 	cmd에 관한 도움말 출력

#### 파일 불러오기/저장하기
	>> pwd		% 현재 위치

	>> cmd 		% 디렉토리 변경

	>> ls		% 현재 디렉토리의 파일 출력

	>> load file.dat  	% 파일 불러오기

	>> load('file.dat') % 파일 불러오기

	>> who 		% 작업 공간의 변수 출력

	>> whos 	% 작업 공간의 변수 자세히 출력

	>> clear A 	% 작업 공간의 변수 A 삭제

	>> clear 	% 작업 공간의 모든 변수 삭제

	>> save hello.mat v; 	% v를 hello.mat으로 저장

	>> addpath('C:\User\dic1\dic2')	% 매트랩에 경로 추가

#### 출력
	>> a = 3;
	>> a
	a = 3

	>> disp(sprintf('2 decimals: %0.2f', a))  % disp를 이용한 C 스타일 출력
	2 decimals: 3.00

	>> format long		% 출력을 long 형식으로
	>> pi
	ans = 3.141592653589793

	>> format short 	% 출력을 short 형식으로
	>> pi
	ans = 3.1416

---

## 연산
#### 기본 연산

	>> 1 + 2
	ans = 
		3

	>> 1 - 2
	ans =
		-1

	>> 1 * 2
	ans =
		2

	>> 1 / 2
	ans =
		0.5000

	>> 2^3
	ans =
		8

	>> sqrt(4)
	ans =
		2

	>> log(3)
    ans =
		1.0986

    >> exp(v)	% 지수 함수
	ans =
		20.0855

	>> abs(-3)	% 절댓값
	ans = 
		3

#### 논리 연산

	>> 1 == 2	% false
	ans = 
		logical
		0

	>> 1 == 1	% true
	ans = 
		logical
		1

	>> 1 && 0	% AND
	ans = 
		logical
		0

	>> 1 || 0	% OR
	ans = 
		logical
		1

	>> xor(1,0)	% XOR
	ans =
		logical
		1

---

## 변수
	>> a = 3		% double형
	a = 3

	>> a = 3;		% ;를 붙이면 결과가 출력되지 않음

	>> b = 'hi'		% char형
	b = 'hi' %

	>> c = (3>1)	% logical형
	c =
		logical
		1

---

## 행렬과 벡터
#### 생성
	>> A = [1 2; 3 4; 5 6]
	A = 
		1	2
		3	4
		5	6

	>> v = 1:0.1:2		% a:b:c 	a부터 b씩 c까지
	v = 
		1 ~ 5번 열
		1.0000    1.1000    1.2000    1.3000    1.4000
		6 ~ 10번 열
		1.5000    1.6000    1.7000    1.8000    1.9000
		11번 열
		2.0000

	>> ones(2,3)		% ones(a,b) 	원소가 1인 a*b 행렬
	ans = 
		1	1	1
		1	1	1

	>> zeros(1,3)		% zeros(a,b) 	원소가 0인 a*b 행렬
	ans = 
		0	0	0

	>> rand(3,3)		% rand(a,b) 원소가 랜덤인 a*b 행렬
	ans = 
		0.9575    0.9706    0.8003
    	0.9649    0.9572    0.1419
    	0.1576    0.4854    0.4218

    >> randn(1,3)	% randn(a,b) 원소가 정규분포에서 추출된 랜덤값인 a*b 행렬
	ans =
		1.4897    1.4090    1.4172    

	>> eye(4)			% eye(n) 	n*n의 단위 행렬
	ans = 
		1     0     0     0
    	0     1     0     0
    	0     0     1     0
    	0     0     0     1

    >> magic(3) 	% magic(n) 	n*n인 마방진 행렬 생성
    ans =
		8	1	6
		3	5	7
		4	9	2

#### 분석
	>> A = [1 2; 3 4; 5 6];
	>> v = [1; 2; 3];


	>> size(A)			% 행렬의 크기
	ans =
		3	2

	>> length(v)		% 벡터의 길이
	ans = 
		11

	>> A(3,2)		% 변수명(a,b) 	변수의 (a,b)값 출력
	ans = 
		6

	>> A(2,:)		% 변수명(a,:) 	변수의 a행 값 출력
	ans = 
		3	4

	>> A(:,2) 		% 변수명(:,b) 	변수의 b열 값 출력
	ans = 
		2
		4
		6

	>> A([1 3], :)	% 변수명([a b], :)  변수의 a, b행의 값 출력
	ans = 
		1	2
    	5	6

    >> max(v) 		% v의 최댓값
    ans =
    	3

    >> [val, ind] = max(v)	% v의 최댓값과 그 인덱스
    val =
    	3
    ind =
    	3

    >> max(A, [], 1)	 % 열의 원소 중 최댓값
    ans =
		5	6

    >> max(A, [], 2)	 % 행의 원소 중 최댓값
    ans =
		2
		4
		6

    >> A < 3 		% A의 원소 중 3보다 작으면 참, 아니면 거짓
    ans =
    	3×2 logical 배열
		1	1
		0	0
		0	0

	>> [r, c] = find(A>3) 	% A보다 큰 값의 행, 열 좌표
	r =
	    3
	    2
	    3
	c =
	    1
	    2
	    2


	>> v = [1.000 2.400 3.500];


	>> sum(v) 	% 원소의 합
	ans =
    	6.9000

    >> prod(v)	% 원소의 곱
    ans =
    	8.4000

    >> floor(v) % 원소의 끝자리를 버림
    ans = 
    	1	2	3

    >> ceil(v) 	% 원소의 끝자리를 올림
	ans =
		1	3	4

#### 조작
	>> A(:,2) = [10; 11; 12]	% 덮어쓰기
	A =
    	1    10
    	3    11
    	5    12

    >> A = [A, [100; 101; 102]]	% 붙이기
	A =
    	1    10   100
    	3    11   101
    	5    12   102

    >> A(:)			% 모든 원소를 하나의 벡터로
	ans =
    	1
    	3
    	5
    	10
    	11
    	12
		100
		101
		102

	>> A = [1 2; 3 4; 5 6];
	>> B = [11 12; 13 14; 15 16];
	>> C = [A B] 	% A와 B를 붙여 C로 저장
	C =
    	1     2    11    12
    	3     4    13    14
    	5     6    15    16

    >> C = [A; B]	% A와 B를 세로로 붙여 C로 저장
	C =
    	1     2
    	3     4
    	5     6
    	11    12
    	13    14
    	15    16

#### 연산
	>> A = [1 2; 3 4; 5 6];
	>> B = [11 12; 13 14; 15 16];
	>> C = [1 1; 2 2];
	>> v = [1; 2; 3];

	>> A*C 	 % 행렬의 곱셈
	ans = 
    	5     5
    	11    11
    	17    17

    >> A .* B 	% .은 원소 단위 연산
    ans =
    	11    24
    	39    56
    	75    96

    >> 1./ A
	ans =
		1.0000    0.5000
		0.3333    0.2500
		0.2000    0.1667

    >> -v 		% -를 붙여 *-1
    ans =
		-1
		-2
		-3

    >> A' 		% A의 전치행렬
	ans =
		1	3	5
		2	4	6

---

## 그래프

	>> t = [0:0.01:0.98];
	>> y1 = sin(2*pi*4*t);
	>> y2 = cos(2*pi*4*t);
	>> A = [1 2; 3 4; 5 1];


	>> plot(t, y1);		% (t, y1)의 그래프 출력
<center><img src="\assets\images\2020-08-18-Matlab-Command-Guide-01.jpg" width="300px" height="300px" align=center>
</center>

	>> hold on; 	% 기존 그래프 위에 다음 그래프 출력
	
	>> plot(t, y2);
<center><img src="\assets\images\2020-08-18-Matlab-Command-Guide-02.jpg" width="300px" height="300px" align=center>
</center>

	>> xlabel('time'); 	% x축 이름 추가
	
	>> ylabel('value');	% y축 이름 추가

	>> legend('sin', 'cos'); 	% 그래프에 이름 추가

	>> axis([0.5 1 -1 1]); 	% 축 범위 설정

<center><img src="\assets\images\2020-08-18-Matlab-Command-Guide-03.jpg" width="300px" height="300px" align=center>
</center>

	>> print -dpng 'myPlot';	% png으로 그래프 저장

	>> figure(1); plot(t, y1);	% plot을 figure 1로 새 창에서 열기
	>> figure(2); plot(t, y2);	% plot을 figure 2로 새 창에서 열기

	>> subplot(1,2,1); % subplot(a,b,c) 화면을 a*b로 분할하고 c부터 그래프 출력
	>> plot(t, y1);
	>> subplot(1,2,2);
	>> plot(t, y2);
<center><img src="\assets\images\2020-08-18-Matlab-Command-Guide-04.jpg" width="300px" height="300px" align=center>
</center>

	>> imagesc(A);		% 좌표평면을 행렬에 맞게 색칠
<center><img src="\assets\images\2020-08-18-Matlab-Command-Guide-05.jpg" width="300px" height="300px" align=center>
</center>

	>> colorbar;		% Color Bar 출력
	>> colormap gray;	% 색을 회색 계열로 변경
<center><img src="\assets\images\2020-08-18-Matlab-Command-Guide-06.jpg" width="300px" height="300px" align=center>
</center>

	>> hist(y1, 50); 	% hist(t, n)	v를 히스토그램으로 출력 (기둥 n개)
<center><img src="\assets\images\2020-08-18-Matlab-Command-Guide-07.jpg" width="300px" height="300px" align=center>
</center>

	>> close; 			% 닫기
	>> clf; 			% 화면 지우기

---

## 조건문, 반복문
#### for문 
	>> v = zeros(10,1);

	>> for i=1:10,
	      v(i) = 2^i;
	   end;
	>> v
	v =
		2
		4
		8
		16
		32
		64
		128
		256
		512
		1024

#### whlie문

	>> i = 1;
	>> while(i <= 5),
	      v(i) = 100;
	      i = i+1;
	   end;
	>> v
	v = 
		100
		100
		100
		100
		100
		64
		128
		256
		512
		1024

#### break, if문
	>> i = 1;			
	>> while true,
	      v(i) = 999;
	      i = i+1;
	      if i== 6,
	         break;		
	      end;
	   end;
	>> v
	v = 
		999
		999
		999
		999
		999
		64
		128
		256
		512
		1024

#### if, elseif, else문
	>> v(1) = 2;
	>> if v(1)==1,
	      disp('Value : 1');
	   elseif v(1)==2,
	      disp('Value : 2');
	   else,
	      disp('Value : 3+');
	   end;

	Value : 2

## 함수
Matlab에서 사용자 지정 함수를 사용하기 위해서는 파일로 함수를 작성한 뒤, 저장해서 불러와야 한다. 텍스트 에디터에서 다음과 같이 함수를 작성하고 .m 파일로 저장한다.
	
	function [y1, y2] = squareAndCube(x)

	y1 = x^2;
	y2 = x^3;

addpath 명령어를 통해 squareAndCube.m 파일이 저장된 경로를 추가하면 Matlab에서 squareAndCube(x)를 사용할 수 있다.
	
	>> [a, b] = squareAndCube(5)	
	a =
		25
	b =
		125
		
---