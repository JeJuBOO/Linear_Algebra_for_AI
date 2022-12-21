# Linear_Algebra_for_AI
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























  
