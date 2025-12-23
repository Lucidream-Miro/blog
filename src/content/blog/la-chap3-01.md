---
title: 'Linear Algebra Chapter III: Linear Mappins'
description: 'Personal study of linear algebra with Serge Lang textbook.'
pubDate: 'Dec 23, 2025'
---

## Theme 1. Mappings

### 1. Mapping(사상)
- 집합 $S$의 모든 원소가 $S’$의 원소에 관련이 있다면 $S$에서 $S’$으로의 사상을 $F:S\to S’$으로 표시한다.
- 함수 표현법을 차용하여 $T:S \to S’,\;u \in S$일 때 $u$에 대응되는 $S’$의 원소는 $T(u)$로 표시한다.
	- $T(u)$: The value of $T$ at $u$ or the image of $u$ under $T$.
	- $S$의 모든 임의의 원소 $u$에 대한 $T(u)$의 모음을 $T$의 image(상)이라고 부른다. → 함수에서의 치역과 같은 개념
	- $x \mapsto F(x)$: $F$에서 $x$의 상. e.g. $F(x)=x^2 \Rightarrow x \mapsto x^2$.

### 2. 미분/적분 연산자
- 구간 $(0,1)$에서 $S$가 n계 도함수를 가지는 모든 함수의 집합이고, $S’=S$일 때 사상 $D:S\to S’$는 $D=d/dt$로 정의할 수 있다. 이때, $D$가 **미분연산자**로 기능한다. e.g. $df/dt=D(f)$
- $S$가 구간 $[0,1]$에서 연속인 모든 함수의 집합이고 $S’$이 미분가능한 모든 함수의 집합일 때, 사상 $\mathfrak{J}: S \to S'$을 통해 $S$의 어느 함수 $f$에 대한 적분을 mapping할 수 있다. $(\mathfrak{J}f)(x)=\int^x_0f(t)dt$일 때 $\mathfrak{J}$는 **적분연산자**로 기능하고, $\mathfrak{J}(f)$는 FTC(Fundamental Theorem of Calculus)에 의해 **미분가능**하다. 

### 3. 기하적 접근
- $F: \mathbb{R}^2 \to \mathbb{R}^2$을 $F(x,y)=(2x,2y)$로 주어지는 사상이라 할 때, $x^2+y^2=1$ 위의 점 $(x,y)$에 대하여 $(x,y) \mapsto (u,v)$이고, $u=2x,\;v=2y$이므로 $(u/2)^2+(v/2)^2=1 \implies u^2+v^2=4$. 따라서, $F$에 의한 상은 반지름이 2인 원이라고 해석할 수 있다. → 사상에 따라 scale이 달라지기도 한다. Determinant의 기본 개념 중 하나. 
- **평행이동(translation)**: 벡터공간 $V$와 $V$의 상수 $u$에 대해 $T_u:V \to V \Rightarrow T_u(v)=v+u$.

### 4. Parametric curve
- $F,\;G:S \to V$라고 하자. 
	- 벡터공간 $S$의 임의의 원소 $t$에 대해 $F(t) \in V,\;G(t) \in V\Rightarrow F(t)+G(t) \in V$.
	- 스칼라 $c$에 대해 $F(t) \in V \Rightarrow cF(t) \in V$.
- $F(t)=(f_1(t), \cdots, f_n(t))$인 $S$의 함수들이 $F:S \to K^n$에서 성립 $\Rightarrow$ $f_i(t)$는 coordinate function, $F(t)$는 parametric curve in n-space.
- $F,\;G:S \to K^n$일 때,
	- $(F+G)(t) = (f_1(t)+g_1(t), \cdots, f_n(t)+g_n(t))$
	- $(cF)(t)=cF(t)=(cf_1(t),\cdots,cf_n(t))$

### 5. Composite mapping
- $F: U \to V,\; G:V \to W$이면 $G\cdot F:U\to W$로 정의된다. $(G\cdot F)(t)=G(F(t))$. 
- $f,g:\mathbb{R} \to \mathbb{R}$인 $f,g$가 모두 함수라면 $g\cdot f$는 합성함수이다.

### 6. Mapping의 주요 성질과 종류

#### Mapping의 주요 성질
- **결합법칙**: $H\cdot(G\cdot F)=(H\cdot G) \cdot F$

#### Injective mapping(단사)
- $x_1\neq x_2 \implies f(x_1)\neq f(x_2)$. 즉, **일대일함수**

#### Subjective mapping(전사)
- $f:S\to S’$에서 $f$의 상이 $S’$ 전체와 같음($\operatorname{Im} f = S’$). 즉, **공역과 치역이 같음**.

#### Bijective mapping(전단사)
- Injective and subjective at the same time. i.e. **일대일대응**
- **Caution**: $x \mapsto x^2$을 $\mathbb{R} \to \mathbb{R}$에서 보면 단사도 아니고 전사도 아니다. 하지만 $\mathbb{R}^+ \to \mathbb{R}^+$에서 보면 전단사이다.

#### Identity mapping(항등사상)
- $I_s: I_s(t)=x$. 즉 $x \mapsto x$. 
- 어떤 사상 $F$가 **역을 가질 조건**: $G\cdot F=I_s$이고 $F \cdot G=I_s$인 mapping $G:S’ \to S$가 존재한다.

---

## Theme 2. Linear Mappings

### 1. 선형사상의 조건
- $V$, $V’$이 체 $K$ 위의 벡터공간일 때, $F:V \to V’$은
	1. 임의의 $u,\;v \in V$에 대해 $F(u+v)=F(u)+F(v)$
	2. 임의의 수 $c \in K$와 벡터 $v \in V$에 대해 $F(cu)=cF(u)$
	를 만족할 때 $K\text{-linear}$라고 한다. 즉, $F(ax+by)=aF(x)+bF(y)$일 때 선형사상이다.

### 2. Projection(사영)
- $F: K^n \to K^n\;(0<r<n)$인 사영사상 $F$는 $F(x_1,\cdots,x_n) = (x_1,\cdots, x_r)$로 정의된다.

### 3. Linearity of matrix multiplication`
- Let $A$ be $m \times n$ matrix. Let a mapping $L_A:\mathbb{R}^3 \to \mathbb{R}$ be linear mapping $X \mapsto X\cdot A$. i.e. $L(A)=X \cdot A$. 
- $L_A$는 linear mapping이기 때문에 $X$가 n차원 열벡터일 때 언제나 정의됨.
$$
AX=\begin{pmatrix}a_{11}&&\cdots&&a_{1n}\\&&\vdots&&\\a_{m1}&&\cdots&&a_{mn}\end{pmatrix}\begin{pmatrix}x_1\\\vdots\\x_m\end{pmatrix}=\begin{pmatrix}a_1\cdot X\\\vdots\\a_m\cdot X\end{pmatrix}
$$
- **행렬곱도 선형성을 가진다.**

### 4. Identity mapping
- 벡터공간 $V$에서 $V$로의 사상에서 모든 원소가 자기 자신에 대응 → identity mapping.
- $\operatorname{id}$ 혹은 $I$로 표현. (고등학교 과정에서는 $E$ 사용)

### 5. Zero mapping
- $O:V \to V'$에서 $V$의 모든 원소가 $V’$의 $O$와 대응. 
- Let $L:V \to W$ be a linear map → $L(O) = O$
- 영벡터의 상이 영벡터가 아니라면 선형이 아니다. i.e. If $F:V \to W$ is a mapping and $F(O) \neq O$, then $F$ is not linear.

### 6. The space of linear maps
- $V$에서 $V’$으로의 모든 선형사상의 집합을 $\mathfrak{L}(V,V’)$ 또는 그냥 $\mathfrak{L}$이라고 하자. 선형사상끼리의 덧셈, 스칼라곱은 $\mathfrak{L}$을 벡터공간으로 만들면 자연스럽게 정의된다.
	- $(T+F)(u)=T(u)+F(u)$
	- $(T+F)(cu)=T(cu)+F(cu)=cT(u)+cF(u)=c[T(u)+F(u)]=c(T+F)(u)$.

### 7. 미분 연산자와 선형사상
- Let $V=V'$ be the vector space of real valued functions of a real variable, which have derivatives of all order.
- $D(f+g)=Df+Dg$, $D(cf)=cDf$ for any differentiable function $f, g$ 
	- e.g. $(D+I)(f)=Df+f$
	→ **선형변환 자체도 벡터공간의 원소**기 때문에 연산이 가능하다!

### 8. Superposition principle
- $T(a_1u_1+\cdots+a_nu_n)=a_1T(u_1)+\cdots+a_nT(u_n)$

>[!note] 기저 존재성/유일성 정리
>$\{v_1,\cdots,v_n\}$이 $V$의 기저, $w_1,\cdots,w_n$이 $W$의 임의의 원소라 하자. 그렇다면 $T(v_1)=w_1, \cdots, T(v_n)=w_n$을 만족하는 유일한 선형사상 $T:V \to W$이 존재한다.

---

## Theme 3. The kernel and image of a linear mapping

### 1. Kernel

#### Definition
- $V$, $W$가 vector space over $K$일 때 $F: V \to W$가 선형사상이라 하자. $F$의 핵(kernel)은 “$F(v)=0$을 만족하는 $v \in V$의 집합”이다.
- 이때 $\ker F$는 $V$의 부분공간이다. Why?
	1. $F(O) = O$
	2. If $F(v_1)=0 \text{ and } F(v_2)=0 \implies F(v_1+v_2)=F(v_1)+F(v_2)=0+0=0$
	3. Let $c \in K$ be a number. $F(cv)=cF(v)=c0=0$


#### Relationship between kernel and injective mapping
- The kernel of $F$ is equal to $\{O\}$
- If $v$, $w$ are elements of $V$ such that $F(v)=F(w) \Rightarrow v = w$, $F$ is injective. If we rearrange the relation, $F(v)-F(w)=0 \Rightarrow F(v-w)=F(O)=0$. 

>[!note] 선형독립 정리
>Let $F: V \to W$ be a linear map whose kernel is $\{O\}$. If $v_1,\cdots,v_n$ are linearly independent elements of $V$, then $F(v_1),\cdots,F(v_n)$ are linearly independent elements of $W$.

### 2. Image(상)
- 선형사상 $F: V \to W$에서 $v \in V$에 대해 $F(v)=w$ 만족하는 $w \in W$ 집합 $\Rightarrow \operatorname{Im} F$.

>[!note] 선형대수학의 기본 정리
>선형사상 $L: V \to W$에서 $\dim V = \dim \operatorname{Ker} L + \dim \operatorname{Im} L$, i.e. $n=q+s$

>[!note] 전단사 정리
>선형사상 $L: V \to W$에 대해 $\dim V=\dim W$. $\operatorname{Ker} L = \{O\}$ or $\operatorname{Im} L = W$이면 $L$은 전단사이다.

---

## Theme 4. Composition and inverse of linear mappings

### 1. Composite map
- 선형사상 $F:U \to V$, $G: V \to W$에 대해 $G \cdot F$도 선형사상이다.

### 2. Arithmetic
- $(G+H) \cdot F= G \cdot F + H \cdot F$, $G \cdot (F+T)=G \cdot F + G \cdot F$ → 분배법칙 적용됨
- $(cG) \cdot F = c(G \cdot F)$ → 스칼라곱 순서는 상관 없음
- $F$는 연산자(operator)로도 볼 수 있음.
	- $F \cdot F \cdot \cdots \cdot F = F^n$
	- $F^0=I$ ($I$는 identity)
	- $F^{r+s}=F^r \cdot F^s$

### 3. Inverse mapping
- $F:U \to V$가 선형사상일 때 $G:V \to U$라는 inverse mapping을 정의할 수 있다. 이때, $G$ 또한 선형사상이다.
- **조건**: $\ker F=\{0\}$이고 단사($\operatorname{im} F=V$)이면 inverse mapping을 가진다.
- $F:U\to V$가 역 $G:V\to U$를 가질 때 **isomorphism-동형사상**-이라고 함.

---

## Theme 5. Geometric Application

### Line segment
- $u, v \in V$일 때, $v+tu\;(0\leq t\leq 1)$로 선분을 표현할 수 있다. $v+u=w \in V$로 두면, 
	- $v+t(w-v)=(1-t)v+tw=t_1v+t_2w=sv+(1-s)w$. 
- 선분의 상(image)
	- Let $L:V \to V’$ be a linear map. $S$$ is the line segment in $V$ between $v,w$. $\Rightarrow$ $L(t_1v+t_2w)=t_1L(w)+t_2(w)

### Parallelogram
- $v,w$가 선형독립이라면 $t_1v+t_2w\;(0 \leq t_1, t_2 \leq 1)$을 만족하는 점의 집합을 **v, w에 의해 생성(span)된 평행사변형(parallelogram)** 이라고 할 수 있다.
- translation까지 고려하면, $L(u+t_1v+t_2w)=L(u)+t_1L(v)+t_2L(w)\;(0 \leq t_1, t_2 \leq 1)$

### Triangle
- $t_1v+t_2w,\;t_1 \geq 0,\; t_2 \geq 0,\; t_1+t_2 \leq 1$ 
- $t_1v_1+t_2v_2+t_3v_3\;(t_{1,2,3} \geq 0, \; t_1+t_2+t_3 =1)$ $\Rightarrow$ $L:\{O,v,w\} \to \{v_1, v_2, v_3\}$인 선형변환.

### Convex
- For a subset $S$ of a vector space $V$, we shall say that $S$ is convex if given points $P, Q$ in $S$ the line segment between $P$ and $Q$ contained in $S$. $\Rightarrow$ **convex(오목)이라는 기하적 개념을 집합 관점에서 재정의**

>[!note] Theorem
>$P_n$이 벡터공간 $V$의 원소들이고 $S$가 $0 \leq t_i\;\text{and}\;t_1+\cdots+t_n=1$인 $\sum^n_{i=1} t_iP_i$의 집합이면 $S$는 $P_1,\cdots,P_n$에 의해 생성된(spanned) convex set.

**i.e. 선형결합의 집합을 convex set으로 정의가 가능하다.**

>[!note] Theorem
>$P_1,\cdots,P_n$이 벡터공간 $V$ 위의 점일 때 $P_1,\cdots,P_n$ 포함하는 모든 집합은 $t_1P_1+\cdots+t_nP_n$을 포함한다.

### Linear Mappings and Convextiy
- 벡터공간 $V$에 대해 $L:V\to \mathbb{R}$이 선형사상일 때 $L(v)<0$ 만족하는 $v \in V$의 집합은 convex.
	- Proof. Let $L(v)<0, \; L(w)<0, \; 0<t<1 \Rightarrow L(tv+(1-t)w)=tL(v)+(1-t)L(w)$. $tL(v)<0,\;(1-t)L(w)<0$이므로  $tv+(1-t)w$가 $S$에 포함됨.