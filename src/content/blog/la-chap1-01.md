---
title: 'Linear Algebra Chapter I: Vector Spaces'
description: 'Raw notes of personal study of linear algebra with Serge Lang textbook.'
pubDate: 'Dec 25, 2025'
---

<br>
<br>
<br>

## Theme 1. Field, Vector Space, Vector

### 1. Field(체)
- **0으로 나누는 것을 제외한 모든 사칙연산에 대한 닫힘성**과 **0, 1의 존재**를 보장하는 수의 집합.
- 이때 한 체의 부분집합에 대해 위의 조건을 만족한다면 **부분체-subfield**-라고 한다.
- field에 포함되는 원소들을 number, or scalar로 부른다.
- $\mathbb{C}$(복소수체), $\mathbb{Q}$(유리수체), $\mathbb{R}$(실수체)가 대표적 예시. 단, $\mathbb{Z}$(정수집합)은 나눗셈에 대한 닫힘이 보장되지 않기 때문에 field가 아니다.
- 교재에서는 임의의 체 $K$가 $\mathbb{C}$의 부분체라고 정의하고 진행한다.

### 2. Vector Space

#### 2-1) Vector Space
- 체 $K$의 부분집합 $V$의 모든 원소에 대해 다음의 성질들이 모두 성립한다면 **벡터공간**으로 정의한다.
- $u, v,w \in V$라 하자.
	- $u+v=v+u$ → 덧셈의 교환법칙
	- $(u+v)+w=u+(v+w)$ → 덧셈의 결합법칙
	- $u+O=O+u=u$ → 덧셈의 항등원 O
	- $u+(-u)=O$ → 덧셈의 역원
	- $u(v+w)=uv+uw$ → 곱셈의 분배법칙
	- $(uv)w=u(vw)$ → 곱셈의 결합법칙
	- $1\cdot u=u$ → 곱셈의 항등원 1
#### 2-2) Subspace
- 체 $K$에서 벡터공간 $V$에 대하여, $V$의 부분집합 $W$의 모든 원소가 다음의 성질을 모두 만족한다면 **부분공간(subspace)** 으로 정의한다.
	- $u, v\in W$이면 $(u+v)\in W$ → 벡터 덧셈에 대한 닫힘
	- $c$가 스칼라, $u\in W$면 $cu\in W$ → 스칼라 곱셈에 대한 닫힘
	- $V$의 영벡터 $O$가 $W$에도 포함

#### 2-3) Generate(span)
- 벡터공간 $V$의 원소 $v_n$과 상수 $x_n, y_n\in K$에 대하여 임의의 선형결합 $x_1v_1+ … + x_nv_n$이 벡터공간 $W$의 원소라 하자.
- 임의의 원소 $u, w\in W$에 대해
	- $u=x_1v_1+ ... + x_nv_n$ 
	- $w=y_1v_1+ … + y_nv_n$ 
	부분공간의 정의를 적용하면,
	1. $u+w=(x_1+y_1)v_1 + … + (x_n+y_n)v_n \in W$ 
	2. $cu=(cx_1)v_1+ … + (cx_n)v_n \in W$ 
	3. $O\in W$
	따라서 $W$는 $V$의 부분공간이며, $v_1, ..., v_n$은 $W$를 생성한다.
- $\operatorname{span} (v_1, …, v_n) = W$

### 3. Dot Product(Scalar Product)
- $V=K^n$이라 하자. $A, B\in K^n$이고 $A=(a_1, …, a_n), B=(b_1, …, b_n)$일 때 $A\cdot B= a_1b_1+ … + a_nb_n$ 로 정의한다.
- Dot product(점곱)의 성질
	1. $A\cdot B = B \cdot A$
	2. $A \cdot (B+C)=A \cdot B + A \cdot C = (B+C) \cdot A$
	3. $x\in K$면 $(xA)\cdot B= x(A\cdot B),\; A\cdot (cB) = x(A\cdot B)$

>[!note] 완전제곱식
>$(A \pm B)^2 = A^2\pm2A\cdot B + B^2$

### 4. Perpendicular(orthogonal) vectors
- $A\subset K^n$일 때, $A\cdot B=0 \iff$ $A$, $B$는 서로 직교
- $A$와 $C$도 수직이라면, $(B+C)\cdot A = B\cdot A + C \cdot A = 0 \implies$ $(B+C)$도 $A$에 수직 
- $x$가 스칼라라면, $(xB)\cdot A = x(B \cdot A) = 0$ 
- $\therefore W$는 $K^n$의 부분공간.

### 5. Function Spaces
**Let S be a set and K a field.**
- A function of S into K: S의 모든 원소가 K의 원소와 한번씩 대응. $\Rightarrow f:S → K$, $K$-valued function이라 함.
- Let $V$ be the set of all functions of $S$ into $K$.
	$f$, $g$가 $V$에 포함되는 함수라면, $f+g$ 또한 포함됨.
	- $(f+g)(x)=f(x)+g(x)$ : 덧셈에 대한 닫힘
	- $(cf)(x)=cf(x)$ : 스칼라곱에 대한 닫힘
	- $O(x)=O \text{ for all } x \in S$ : 영벡터가 공통
	$\implies$ $V$가 체 $K$ 위의 벡터공간이 되도록 연산을 정의할 수 있다. i.e. 함수의 집합 또한 벡터공간이 된다.
- Let $V$ be the set of all functions of $\mathbb{R} → \mathbb{R}$, $W$ be the subset of continuous functions.
	- $f$, $g$가 연속 → $f+g$도 연속
	- $f$가 연속 → $cf$도 연속(c는 스칼라)
	$\implies$ $W$는 $V$의 부분공간이다. 
- 같은 논리로, 미분가능한 모든 함수의 집합 $U$도 $W$의 부분공간이자 $V$의 부분공간이다.
	e.g. Let $f(t) = e^t$, $g(t)=e^{2t}$ for all $t\in \mathbb{R}$. $f,g \in U$. → $f$와 $g$의 선형결합으로 부분공간이 생성됨. 

---
## Theme 2. 기저(basis, pl: bases)

### 1. 선형독립
- 벡터공간 $V$의 원소 $v_n$과 스칼라 $a_n$에 대하여 $$\sum^n_{i=1} a_iv_i=0$$ 을 만족하는 0이 아닌 $a_n$이 있다면 → 종속관계!
- $a_n$이 모두 0일 때만 성립한다면 선형독립이다.

### 2. 기저(basis)
- $v_1, \cdots, v_n$이 $V$를 생성하고 서로 독립이라면 $v_1, \cdots, v_n$은 $V$의 기저이다.

### 3. 좌표벡터(coordinate vector)
- 벡터공간 $V$의 성분 $v$가 $V$의 기저 $v_1, \cdots , v_n$에 대하여 $v=x_1v_1+ \cdots + x_nv_n$으로 나타난다면 $(x_1, \cdots , x_n)$이 벡터 $v$의 좌표이다. 즉, 좌표벡터 $X=(x_1, \cdots, x_n)$ 

### 4. Maximal linearly independent subset(극대 선형독립 부분집합)
- 벡터공간 $V$의 원소에 대하여 서로 선형독립인 원소들의 최대 집합.
- Maximal linearly independent subset은 벡터공간 $V$의 기저가 될 수 있다. 

---
## Theme 3. Dimension of a vector space

>[!note] 선형종속 정리
>$V$를 체 $K$ 위의 벡터공간이라고 하자. $\{v_1,\cdots,v_m\}$을 $V$의 기저라고 하자. $w_1,\cdots,w_n$이 $V$의 원소이고 $n>m$일 때, $w_1,\cdots,w_n$은 선형종속이다.

### 1. 벡터공간의 차원
- 벡터공간 $V$에 대해 서로 다른 두 기저가 $m$개와 $n$개의 원소를 가질 때, $m=n$이다. 
- 선형종속 정리에 의하면 같은 벡터공간의 두 벡터가 서로 다른 원소를 가지면 적은 쪽이 많은 쪽에 종속일 수밖에 없다. 
- 기저 $V$가 $n$개 원소의 기저로 이루어질 때, $n$은 $V$의 차원이다. $n=\operatorname{dim} V$. 
- $V$의 원소가 영벡터 뿐이라면 $n=0$. 기저는 존재하지 않는다.
- $n$이 유한할 때 finite dimensional, 무한하다면 infinite dimensional.

### 2. 스칼라 체의 벡터공간적 해석
- 체 $K$에 대하여 $K$는 $K$ 위의 1차원 벡터공간으로 볼 수 있다.
- 기저는 $\{1\}$이다. $x\in K$에 대하여 기저를 $v$로 놓으면, $K$의 모든 원소는 $xv$로 나타낼 수 있기 때문이다. 
→ 수직선을 대수적으로 정의한 것으로 볼 수 있음.

### 3. 벡터 부분공간의 차원
- 벡터공간 $V$에서 $\{v_1,\cdots,v_n\}$이 선형독립이고 maximal linearly independent subset이라면 → $V$의 기저이다. i.e. $w \in V$일 때 $w=x_1v_1+\cdots+x_nv_n$
- n차원 벡터공간 $V$의 원소 $v_1$부터 $v_n$까지 n개의 벡터가 선형독립이라면 $v_1,\cdots,v_n$은 $V$의 기저를 구성한다.
- 벡터공간 $V$, $W$에 대해 $W \subset V$일 때 $\operatorname{dim} W = \dim V \Rightarrow V=W$ → **부분공간인데 차원이 같다면 동일한 공간**.
- n차원 벡터공간 $V$에서 $r\;(v<n)$개의 선형독립인 벡터를 알 때, 선형독립인 또다른 벡터 $(n-r)$개를 추가하여 $V$의 기저를 구성할 수 있다.
- n차원 벡터공간 $V$와 0차원 아닌 부분공간 $W$에 대하여 $\dim W \leq n$. 등호가 성립할 때는 $V=W$일 때!

---
## Theme 4. Sums and direct sums

### 1. Sum: 합공간
- 벡터공간 $V$의 부분공간 $U, W$에 대해서 $U+W=\{u+w\;|\;u\in U,\;w\in W\}$ 
- 왜 “합공간”인가?
	1. $(u_1+w_1)+(u_2+w_2)= u_1+u_2+w_1+w_2 \in (U+W)$ → 덧셈에 대해 닫혀있다.
	2. $c(u_1+w_1)=cu_1+cw_1 \in (U+W)$ → 스칼라곱에 대해서도 닫혀있다.
	3. $O+O=O \in (U+W)$ → 영벡터도 공유한다.
	따라서 두 벡터공간의 원소들의 합으로 이루어진 집합은 $V$의 부분공간이며, $U$와 $W$의 합공간이다.

### 2. Direct sum(직접합)
- 임의의 $i$에 대해 $v_i=u_i+w_i$를 만족하는 $u_i$와 $w_i$의 조합이 **항상 유일**하다면 $\Rightarrow$ direct sum이다.

**Properties of Direct Sum**
- $U+W=V \text{ and } U \cap W=\{O\} \iff V=U \oplus W$.
- $V$가 유한차원 벡터공간일 때 부분공간 $U$에 대하여 $V = U \oplus W$인 $W$가 존재한다.
- $\dim V = \dim U + \dim W$
- $\dim (U\times W) = \dim U + \dim W$.
	- $U \times W = \{(u,w)\;|\;u \in U,\; w \in W \}$일 때,
		(1) $(u_1,w_1)+(u_2,w_2)=(u_1+u_2,w_1+w_2) \in U \times W$.
		(2) $c(u_1,w_1) = (cu_1,cw_1) \in U \times W$. 
		$\Rightarrow$ $U$와 $W$의 direct product. 
- $n=r+s>0$일 때, $K^n=K^r \times K^s$ → $\dim (U \times W) = \dim U + \dim W$.
- $V=\displaystyle\bigoplus^n_{i=1} V_i=V_i \oplus \cdots \oplus V_n$ → $v=v_1+\cdots+v_n$ 일 때 $v=v_1’+\cdots+v_n’$이라면 $v_i’=v_i$.
- $\displaystyle \prod^n_{i=1} W_i=W_1 \times \cdots \times W_n \Rightarrow (w_1,\cdots, w_n)$ → 벡터공간의 곱셈으로 표현하는 것은 **벡터공간의 차원**이다.