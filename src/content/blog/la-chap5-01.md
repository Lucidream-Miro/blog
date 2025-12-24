---
title: 'Serge Lang Linear Algebra 따라가기 Chapter V(1): Scalar Products'
description: 'Personal study of linear algebra with Serge Lang textbook.'
pubDate: 'Dec 23, 2025'
---

## Theme 1. Scalar Product <small>(스칼라 내적)</small>

고등까지의 벡터 연산에서 내적을 떠올려보면 다음과 같다. 점 $A(a_1, a_2)$와 점 $B(b_1,b_2)$가 있을 때,
$$\overrightarrow{OA}\cdot \overrightarrow{OB}=a_1b_1+a_2b_2.$$

하지만 Serge Lang의 책에서는 내적의 일반화된 개념을 다룬다. 이제부터의 내적은, 둘 이상의 벡터를 입력받아 스칼라를 내놓는 사상<small>mapping</small>중 하나이다. 당연히 지금까지 다루었던 내적도 '점곱'<small>dot product</small> 또는 표준 내적<small>standard product</small>이라는 이름으로 포함된다.

### 1. 스칼라 내적의 조건

벡터공간 $V$의 원소 $u, v, w$에 대해 스칼라 내적 $\langle , \rangle$을 다음과 같이 정의한다.
1. $\langle u, v \rangle = \langle v, u \rangle$: 대칭성 (교환법칙)
2. $\langle u, v + w \rangle = \langle u, v \rangle + \langle u, w \rangle$: 덧셈에 대한 선형성 - 중첩원리
3. $\langle xu, v \rangle = \langle u, xv \rangle = x\langle u,v\rangle \; (x \in K)$: 스칼라곱에 대한 선형성

우리에게 익숙한 점곱으로 예를 들면, 
1. $a \cdot b = b \cdot a$
2. $a \cdot (b + c) = a \cdot b + a \cdot c$
3. $(xa) \cdot b = a \cdot (xb) = x(a \cdot b)$

이렇게 표준 내적 $\cdot$에 대해서도 당연히 스칼라 내적의 성질을 찾아볼 수 있다.

### 2. 비퇴화(비축퇴)<small>non-degenerate</small>

$v \in V$이고 모든 $w \in V$에 대해 $\langle v, w \rangle = O \implies v = O$이면 내적이 비퇴화되었다고 한다.

### 3. 함수공간에서 스칼라 내적

스칼라 내적을 일반적으로 정의했으므로 일반적인 2차원, 3차원의 수들로 이루어진 벡터공간뿐 아니라 함수공간에서도 내적이 정의될 수 있다. 단, 스칼라 내적의 정의에 부합하는지 한번쯤은 확인해볼 필요가 있다.

벡터공간 $V$가 폐구간 $[0,1]$에서 연속인 실함수의 집합일 때, $f,g\in V$에 대해 다음과 같은 사상을 생각하자.

$$ \langle f, g \rangle = \int^1_0 f(t) g(t) dt $$

이 사상은 내적이 맞을까? 예시로 다항함수 공간 $\mathbb{P}$의 부분공간으로 $V$를 잡아보자. 임의의 함수 $f = x$, $g = x^2$이라 하면 $\langle x, x^2 \rangle = \int^1_0 x \cdot x^2 dt=\int^1_0 x^2 \cdot x dt=1/4$. 일단 스칼라가 나오는 것은 맞고, 곱셈의 교환법칙에 따라 대칭성도 성립한다. 분배법칙에 의해 선형성도 자명하다. 즉 내적이 아니라고 할 수 없다. 이렇게 두 개의 벡터를 넣어서 스칼라를 만드는 연산 중 대칭성과 선형성이 보장되는 연산을 스칼라 내적이라고 한다.

### 4. 직교공간

직교는 스칼라 내적을 통해 정의된다. 처음 벡터의 내적(점곱)을 배울 당시 $a \cdot b = |a||b| \cos \theta$로 배웠다. 이때 두 벡터 사이의 각도가 $90\degree$가 되면 내적의 결과는 $0$이 되는 것을 통해 벡터의 직교를 보였는데, 스칼라 내적도 동일하다. 직교는 스칼라 내적의 값이 $0$이 되는 상황을 말한다. 이를 수식으로는 다음과 같이 표현한다. $$\text{When }v, w \in V, \langle v, w \rangle =0 \implies v \perp w$$
직교공간이란 벡터공간에서 이렇게 서로 직교인 벡터들끼리 모아둔 부분공간이다. 즉, $S \subseteq V$일 때, $S$에 대한 직교공간 $S^\perp$는 $w \in S$인 모든 $w$에 대하여 $\langle w, v \rangle=0$을 만족하는 $v \in V$의 집합으로 볼 수 있다. 