# Linear Algebra for AI
[boostcouse](https://www.boostcourse.org/ai251/joinLectures/195088)에 공개된 주재걸 교수님의 강의를 정리한 글입니다.


![image](https://user-images.githubusercontent.com/71332005/208824570-cce4b1f8-8970-4eb0-aead-fbdeede20beb.png)

**주재걸 교수**  
KAIST AI대학원 교수  
[홈페이지](https://sites.google.com/site/jaegulchoo/)

---
## References
**Main textbook**  
• [Lay et al. Linear Algebra and Its Applications, 5th edition, 2015](https://www.amazon.com/Linear-Algebra-Its-Applications-5th/dp/032198238X)  

**Other textbook**  
• Gilbert Strang, Introduction to Linear Algebra, 5th edition, 2016  
• Gilbert Strang, Linear Algebra and Its Applications, 4th edition, 2016  

**Online lecture**  
• [Gilbert Strang’s MIT Lecture](https://ocw.mit.edu/courses/mathematics/18-06-linear-algebra-spring-2010/)  

---

## 목차
[1. 선형대수의 기초(Elements in linear algebra)](#1-선형대수의-기초elements-in-linear-algebra)  
[2. 선형시스템 및 선형변환(Linear Systems and Linear Transformation)](#2-선형시스템-및-선형변환linear-systems-and-linear-transformation)  
[3. 최소제곱문제(Least Squares Problem)](#3-최소제곱문제least-squares-problem)  
[4. 고유값 분해](#4-고유값-분해)  
[5. 특이값 분해](#5-특이값-분해)  

---

## 1. 선형대수의 기초(Elements in linear algebra)

### Scalar, Vector, and Matrix
* 스칼라(Scalar) : 다들 아는 하나의 숫자이다.
* 벡터(Vector) : 한 방향으로 존재하는 1차원의 숫자들의 집합이다.

$$ \mathbf{x}=\begin{bmatrix}x_1 \\
x_2 \\
\vdots \\
x_n\end{bmatrix}$$  
* 행렬(Matrix) : 2차원 배열의 숫자들의 집합이다.   
  - 아래 예시 행렬의 사이즈는 $4 \times 2$행렬 이고 4행(Rows) 2열(Colums)이다. 
  - 즉, 4개의 가로 행이 있고 2개의 세로 열이 있다. 

$$ A=\begin{bmatrix}1 & 6\\
3 & 4\\
5 & 2 \\
8 & 1 \end{bmatrix}$$ 

### Matrix Notations
* $B\in\mathbb{R}^{n\times n}$ : Square matrix, 정사각 행렬, 행과 열의 개수가 같음.  

$$ A=\begin{bmatrix}5 & 3\\
1 & 2\end{bmatrix}$$ 
* $A\in\mathbb{R}^{m\times n}$ : Rectangular matrix, 직사각 행렬, 행과 열의 개수가 다름.  

$$ A=\begin{bmatrix}1 & 6\\
3 & 4\\
5 & 2 \\
8 & 1 \end{bmatrix}$$ 
* $A^T$ : transpose of matrix,전치 행렬, 행렬의 대각선을 기준으로 위아래로 변환하는것, 행과 열을 바꾸는것이다.

$$ A^T=\begin{bmatrix}1 & 3 & 5 & 8\\
6 & 4 & 2 & 1\end{bmatrix}$$ 

* 행렬의 요소
  - $A_{i,j}$ : i번째 행, j번째 열에 있는 요소값을 가리킴. 예) $A_{2,1}=3$
  - $A_{i,:}$ : i번째 행에 있는 요소값을 가리킴. 예) $A_{2,:}=[3 \quad 4]$
  - $A_{:,i}$ : i번째 열에 있는 요소값을 가리킴. 예) $A_{:,2}=[6 \quad 4 \quad 2 \quad 1]^T$

### Vector, Matrix Addition and Multiplication
* $C=A+B$ : Element-wise addition, 요소들 끼리 더함. 즉, $C_{i,j}=A_{i,j}+B_{i,j}$
  - A, B, C는 모두 같은 크기여야 한다. $A,B,C\in\mathbb{R}^{m\times n}$

* $c\mathbf{a},cA$ : Scalar multiple of Vector/Matrix, 벡터/행렬과 스칼라의 곱.

$$2\begin{bmatrix}3 \\
2 \\
1 \end{bmatrix}=\begin{bmatrix}6 \\
4 \\
2\end{bmatrix}, 2\begin{bmatrix}1&6\\
3&4\\
5&2\end{bmatrix}=\begin{bmatrix}2&12\\
6&8\\
10&4\end{bmatrix}$$
* $C=AB$ : Matrix-matrix multiplication, 행렬간의 곱셉, 즉, $C_{i,j}=\sum_k A_{i,k}B_{k,j}$
  - $AB\neq BA$ : 곱하는 순서가 달라지면 다른 값이다.
  - 행렬끼리의 곱은 앞 행렬의 열의 개수와 뒤 행렬의 행의 개수가 같아야 가능하다. 예) $A\in\mathbb{R}^{2\times 3} \text{and} B\in\mathbb{R}^{3\times 5}=C\in\mathbb{R}^{2\times 5}$  

$$\begin{bmatrix}1&6\\
3&4\\
5&2\end{bmatrix}\begin{bmatrix}1&-1\\
2&1\end{bmatrix}=\begin{bmatrix}13&5\\
11&1\\
9&-3\end{bmatrix}$$

* **Other Properties**
  - 분배법칙(Distibutive) : $A(B+C)=AB+AC$
  - 결합법칙(Associative) : $A(BC)=(AB)C$
  - 전치의 성질(Property of transpose) : $(AB)^T=B^TA^T$

[맨 위로..](#linear-algebra-for-ai)

## 2. 선형시스템 및 선형변환(Linear Systems and Linear Transformation)

### Linear Equation
* 선형 방정식(Linear Equation)은 변수(Variables)들$x_1,\dots,x_n$, 계수(coefficients)로 만들어진 방정식이다.

$$a_1x_1+a_2x_2+\dots+a_nx_n=b$$
* 위 방정식은 다음과 같이 쓸 수 있다.

$$\mathbf{a}^T\mathbf{x}=b$$

$$\text{Where }\mathbf{a}=\begin{bmatrix}a_1\\
a_2\\
\vdots\\
a_n\end{bmatrix}\text{ and }\mathbf{x}=\begin{bmatrix}x_1\\
x_2\\
\vdots\\
x_n\end{bmatrix}$$

* A system of linear equations (or a linear system) is a collection of one or more linear equations
involving the same variables.  
선형시스템이란 위 선형 방정식들의 집합이다. 

#### Linear System Example
* 사람들의 몸무게, 키, 흡연의 유뮤, 수명의 데이터를 모아 선형 시스템으로 만들어본다.
* 이를 이용하여 새로운 사람의 몸무게, 키, 흡연의 유무를 통해 대략적인 수명을 알아낼 수 있도록 할 수 있다.

![image](https://user-images.githubusercontent.com/71332005/208854159-d346f08e-3f34-4190-a17f-bf287c434438.png)

* 위 표를 선형시스템으로 다음과 같이 표현한다.

$$60x_1+5.5x_2+1\cdot x_3=66$$  

$$65x_1+5.0x_2+0\cdot x_3=74$$  

$$55x_1+6.0x_2+1\cdot x_3=78$$

* 행렬로 표현 하면 다음과 같이 표현한다.

$$A=\begin{bmatrix}60&5.5&1\\
65&5.0&0\\
55&6.0&1\end{bmatrix},\quad \mathbf{x}=\begin{bmatrix}x_1\\
x_2\\
x_3\end{bmatrix}, \quad \mathbf{b}=\begin{bmatrix}66\\
74\\
78\end{bmatrix}$$
* 여러개의 방정식을 하나의 행렬식으로 표현한다.

$$\begin{bmatrix}60&5.5&1\\
65&5.0&0\\
55&6.0&1\end{bmatrix}\begin{bmatrix}x_1\\
x_2\\
x_3\end{bmatrix}=\begin{bmatrix}66\\
74\\
78\end{bmatrix} \therefore A\mathbf{x}=\mathbf{b}$$  

* 행렬식(Matrix equation)을 가지고 문제를 풀어 보자...

### Identity Matrix
* 항등행렬(Identity Matrix) : 기본적으로 정사각 행렬의 크기에 대각성분들(Diagonal entries)이 모두 1이고, 
  나머지 성분들은 모두 0인 행렬을 의미한다. $I_n\in\mathbb{R}^{n\times n}$
  
$$I_3=\begin{bmatrix}1&0&0\\
0&1&0\\
0&0&1\end{bmatrix}$$
* 항등행렬은 어떠한 벡터와 곱해졌을 때의 결과가 벡터 그대로 나온다. $I_n\mathbf{x}=\mathbf{x}$

### Inverse Matrix
* 역행렬(Inverse Matrix) : 정사각 행렬을 기본으로 하고, 행렬과의 곱이 항등행렬이 나오도록 하는 행렬을 의미한다.

$$A^{-1}A=AA^{-1}=I_n$$

* $2\times 2$행렬의 역행렬 공식은 다음과 같다.

$$A=\begin{bmatrix}a&b\\
c&d\end{bmatrix}, \quad A^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d&-b\\
-c&a\end{bmatrix}$$

* 직사각행렬의 역행렬은 결론적으로 존재하지 않는다. 만약 $A\in\mathbb{R}^{2\times 3}$행렬의 역행렬을 찾는다면
  $AA^{-1}=I_2$와 $A^{-1}A=I_3$으로 두가지를 찾을 수 있지만 일반적으로 $A^{-1}A=I_3$의 역행렬의 없다.  

* 역행렬은 다음과 같이 찾을 수 있다.

$$\begin{eqnarray}
A\mathbf{x}=&\mathbf{b}\\
A^{-1}A\mathbf{x}=&A^{-1}\mathbf{b}\\
I_n\mathbf{x}=&A^{-1}\mathbf{b}\\
\mathbf{x}=&A^{-1}\mathbf{b}\end{eqnarray}$$

#### Solving Linear System via Inverse Matrix

* Example  

$$\begin{bmatrix}60&5.5&1\\
65&5.0&0\\
55&6.0&1\end{bmatrix}\begin{bmatrix}x_1\\
x_2\\
x_3\end{bmatrix}=\begin{bmatrix}66\\
74\\
78\end{bmatrix} \quad A^{-1}=\begin{bmatrix}0.0870&0.0087&-0.0870\\
−1.1304&0.0870&1.1314\\
2.0000&−1.0000&−1.0000\end{bmatrix}$$  

* $A^{-1}A=AA^{-1}=I_n$를 만족하는지 확인하고,

$$\mathbf{x}=A^{-1}\mathbf{b}=\begin{bmatrix}0.0870&0.0087&-0.0870\\
−1.1304&0.0870&1.1314\\
2.0000&−1.0000&−1.0000\end{bmatrix}\begin{bmatrix}66\\
74\\
78\end{bmatrix}=\begin{bmatrix}-0.4\\
20\\
-20\end{bmatrix}$$

* 이로써 수명을 다음과 같이 계산할 수 있다.

$$\text{수명}=-0.4\times\text{몸무게}+20\times\text{키}-20\times\text{흡연유무}$$

### Non-Invertible Matrix
* 역행렬이 존재하지 않을 경우.
  - 예) $2\times 2$ 역행렬 식의 분모부분 $ad-bc$이 0이 될 경우, 역행렬이 존재하지 않는다.
* 여기서 $ad-bc$는 판별식, Determinant of A, det A, 라고 부른다.

### Rectangular Matrix
* 만약 $A$행렬이 직사각행렬일 경우, 즉, $A\in\mathbb{R}^{m\times n},where m\neq n$
  - $m$은 식의 개수(#equations), $n$은 변수의 개수(#variables)이다.
  - $m < n$ : 변수의 개수가 식의 개수보다 많으면 해의 개수가 무수히 많아질 수 있다. (under-determined ststem)
  - $n < m$ : 식의 개수가 변수의 개수보다 많으면 보통 해가 존재하지 않는다. (over-determined system)
  








  
[맨 위로..](#linear-algebra-for-ai)
