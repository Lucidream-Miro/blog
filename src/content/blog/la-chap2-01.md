---
title: 'Linear Algebra Chapter II: Matrices'
description: 'Raw notes of personal study of linear algebra with Serge Lang textbook.'
pubDate: 'Dec 25, 2025'
---

<br>
<br>
<br>

## Theme 1. The space of matrices

### 1. Matrices and vector spaces
- 행렬은 벡터공간의 성질을 모두 만족함. 즉, 행렬은 벡터로 다룰 수 있음.


### 2. 기본 용어
- symmetric(대칭): $A^T=A$. (Serge Lang 교재에서는 $A^T= {}^tA$)
- diagonal(대각): 대각성분을 제외한 나머지 성분들이 모두 0 → 대각행렬은 모두 대칭행렬이다.

---
## Theme 2. Linear Equation

### 1. **선형방정식**

- 아래의 형태로 나타나는 방정식을 뜻한다:
$$
\begin{align}
a_{11}x_1+\cdots+a_{1n}x_n=b_1\\
\vdots\\
a_{m1}+\cdots+a_{mn}x_n=b_m
\end{align}
$$

- 이때, $b_1,\cdots,b_m=0$이면 동차(제차; homogeneous)방정식.
- Trivial solution과 non-trivial solution을 갖는다.
	- Trivial solution: $x_1,\cdots,x_n=0$
	- Non-trivial solution: $x_1,\cdots,x_n\neq0$

### 2. 연립방정식의 선형대수적 해석

- $A^j$를 행렬 $A$의 열벡터라고 하면 위의 선형방정식을 다음과 같이 쓸 수 있다: $$x_1\begin{pmatrix}a_{11}\\\vdots\\a_{m1}\end{pmatrix}+\cdots+x_n\begin{pmatrix*}a_{1n}\\\vdots\\a_{mn}\end{pmatrix*}=0 \implies x_1A^1+\cdots+x_nA^n=0$$위의 방정식을 푼다는 것은 $\implies$ $X=(x_1,\cdots,x_n)\neq0$와 $A^j$의 선형결합이 0이 되는 선형 종속 관계를 찾는 것.
- **Homogeneous linear system에서 n개의 미지수로 이루어진 m개의 방정식(n>m)이 있다면 system은 비자명해(non-trivial solution)를 가진다.**
- **$x_1A^1+\cdots+x_nA^n=B$에서 m=n이고 행렬 A의 열벡터들이 서로 선형독립이라면 system은 특수해(unique solution)을 가진다.**

---

## Theme 3. Matrix Multiplication

### 1. Dot product(recall)

![[Linear Algebra Chapter 1. Vector Spaces#3. Dot Product(Scalar Product)]]

- **실수체** $\mathbb{R}$에서 구성된 임의의 벡터 $A$에 대해, $A\cdot A=A^2=a_1^2+\cdots+a_n^2\geq0$ → $A\neq0$이라면 $A^2>0$. 이유는 점곱이 대표적인 positive definite scalar product이기 때문임.

- **비퇴화(non-degeneracy)**: If $A \in K^n$, and if $A\cdot X=0$ for all $x \in K^n$ then $A=O$.

### 2. 행렬곱
- $A=(a_{ij}), B=(b_{jk})$라 하고 $(c_{ik})=C=AB$일 때, $c_{ik}=\sum^n_{j=1} a_{ij}b_{jk}$. 
- $A$의 행벡터를 $A_1,\cdots,A_m$, $B$의 열벡터를 $B^1,\cdots, B^n$이라 하면, $$AB=\begin{pmatrix}A_1\cdot B^1 && \cdots && A_1B^n\\\vdots&&\ddots&&\vdots\\A_m \cdot B^1 && \cdots && A_m \cdot B_n \end{pmatrix}$$
- $A(B+C)=AB+AC$: 분배법칙
- $(AB)C=A(BC)$: 결합법칙

**전치행렬과 행렬곱**
- ${}^t(AB)={}^tB{}^tA$

### 3. Invertible(non-singular) Matrix
- $AB=BA=I_n$을 만족하는 행렬.
- 하나의 $A$에 대하여 위의 관계를 만족하는 $B$는 유일하다. → $B$는 $A$의 역(inverse)행렬.