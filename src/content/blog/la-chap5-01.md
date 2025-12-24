---
title: 'Linear Algebra Chapter V-01: Scalar Products'
description: 'Personal study of linear algebra with Serge Lang textbook.'
pubDate: 'Dec 23, 2025'
---

## Theme 1. Scalar Product <small>(스칼라 내적)</small>

고등까지의 벡터 연산에서 내적은 '앞에 있는 것끼리 곱하고 뒤에 있는 것끼리 곱해서 더하는' 단순한 연산이었다. 하지만 Serge Lang의 책에서는 내적의 일반화된 개념을 다룬다. 이제부터의 내적은, 둘 이상의 벡터를 입력받아 스칼라를 내놓는 사상<small>mapping</small>중 하나이다. 즉, 쌍선형성<small>bilinearity</small>을 가지는 선형사상이다. 아래의 조건을 만족하는 특수한 사상들을 가리킨다. 당연히 지금까지 다루었던 내적도 '점곱'<small>dot product</small> 또는 표준 내적<small>standard product</small>이라는 이름으로 포함된다.

### #1. 스칼라 내적의 조건

벡터공간 $V$의 원소 $u, v, w$에 대해 스칼라 내적 $\langle , \rangle$을 다음과 같이 정의한다.
1. $\langle u, v \rangle = \langle v, u \rangle$: 대칭성 (교환법칙)
2. $\langle u, v + w \rangle = \langle u, v \rangle + \langle u, w \rangle$: 덧셈에 대한 선형성 - 중첩원리
3. $\langle xu, v \rangle = \langle u, xv \rangle = x\langle u,v\rangle \; (x \in K)$: 스칼라곱에 대한 선형성

우리에게 익숙한 점곱으로 예를 들면, 
1. $a \cdot b = b \cdot a$
2. $a \cdot (b + c) = a \cdot b + a \cdot c$
3. $(xa) \cdot b = a \cdot (xb) = x(a \cdot b)$

이렇게 표준 내적 $\cdot$에 대해서도 당연히 스칼라 내적의 성질을 찾을 수 있다.

### #2. 비퇴화(비축퇴)<small>non-degenerate</small>

양자역학에서 중요하다고 알고 있다. $v \in V$이고 모든 $w \in V$에 대해 $\langle v, w \rangle = O \implies v = O$이면 내적이 비퇴화되었다고 한다.

### #3. 함수공간에서 스칼라 내적

스칼라 내적을 일반적으로 정의했으므로 일반적인 2차원, 3차원의 수들로 이루어진 벡터공간뿐 아니라 함수공간에서도 내적이 정의될 수 있다. 단, 스칼라 내적의 정의에 부합하는지 한번쯤은 확인해볼 필요가 있다.

벡터공간 $V$가 폐구간 $[0,1]$에서 연속인 실함수의 집합일 때, $f,g\in V$에 대해 다음과 같은 사상을 생각하자.

$$ \langle f, g \rangle = \int^1_0 f(t) g(t) dt $$

이 사상은 내적이 맞을까? 예시로 다항함수 공간 $\mathbb{P}$의 부분공간으로 $V$를 잡아보자. 임의의 함수 $f = x$, $g = x^2$이라 하면 $\langle x, x^2 \rangle = \int^1_0 x \cdot x^2 dt=\int^1_0 x^2 \cdot x dt=1/4$. 일단 스칼라가 나오는 것은 맞고, 곱셈의 교환법칙에 따라 대칭성도 성립한다. 분배법칙에 의해 선형성도 자명하다. 즉 내적이 아니라고 할 수 없다. 이렇게 두 개의 벡터를 넣어서 스칼라를 만드는 연산 중 대칭성과 선형성이 보장되는 연산을 스칼라 내적이라고 한다.

### #4. 직교공간

직교는 스칼라 내적을 통해 정의된다. 처음 벡터의 내적(점곱)을 배울 당시 $a \cdot b = |a||b| \cos \theta$로 배웠다.