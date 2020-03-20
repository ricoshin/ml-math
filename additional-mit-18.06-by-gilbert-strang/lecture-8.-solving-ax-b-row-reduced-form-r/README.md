# Lecture 8. Solving Ax=b: Row Reduced Form R

## Introduction

* 지난 lecture에서 $$A\bm{x}=\bm{0}$$에 대해 먼저 공부한 것은 이유가 있다. 
  * Homogeneous system 풀기 / nullspace 찾기 
* 바로 이 과정이 $$A\bm{x}=\bm{b}$$를 푸는데 필요하기 때문이다. 
  * Non-homogeneous system 풀기 
    * 왜 이렇게 부르는지는 문서 전체 검색! 
* 이번 lecture에서는 드디어 linear system을 완전히\(completely\) 풀어보자. 
  * **Complete solution** 구하기! 

#### **선형계에 반드시 해가 존재하는 것은 아니다.** 

* 해가 존재하지 않을 수 있다. \(1\)
* 해가 존재할 경우:  
  * 무수히 많은 해 \(2\)
  * 유일한 해  \(3\)

위 세가지 경우를 elimination을 통해 명확히 구별할 수 있다! 

#### 지난 lecture와 똑같은 행렬을 사용하자. 

* $$A=\begin{bmatrix} 1&2&2&2 \\ 2&4&6&8 \\ 3&6&8&10 \end{bmatrix}$$ 
* 다음의 선형방정식계\($$A\bm{x}=\bm{b}$$\)를 푸는 것이다.  
* $$\begin{cases}\begin{aligned}   x_1 + 2x_2 +2x_3 &+ {2x_4} &= b_1 \\   2x_1 + 4x_2 +6x_3 &+ {8x_4} &= b_2 \\   3x_1+ 6x_2 +8x_3 &+ {10x_4 } &= b_3 \\  \end{aligned}\end{cases}$$ 

## 선형계의 해가 존재하도록 하는 $$\bm{b}$$의 조건이 있을까? 

\(Solvability condition on $$\bm{b}$$\)

### 1. 눈으로 읽을 수 있는 조건 

* 위 방정식계에서 세번째 방정식은 첫번째와 두번째를 더한 것과 같다. 
* 선형계에 자기모순이 없으려면 우변도 마찬가지여야 한다. 
  * $$b_1+b_2=b_3$$

### 2. 소거를 통해 드러나는 조건

#### Elimination은 이러한 우변의 조건을 자연스럽게 드러나게 해준다. 

* 이제는 우변이 있으니 augmented matrix를 통해 $$\bm{b}$$도 함께 추적을 해야한다. 
* $$A=\left[ \begin{array}{cccc|c} 1&2&2&2&b_1 \\ 2&4&6&8&b_2 \\ 3&6&8&10&b_3 \end{array} \right] \rightsquigarrow \left[ \begin{array}{cccc|c} 1&2&2&2&b_1 \\ 0&0&2&4&b_2-b_1 \\ 0&0&0&0&b_3-b_2-b_1 \end{array} \right] $$ 
* 마지막 row를 의미하는 방정식: $$0=b_3-b_2-b_1$$
  * 위의 조건과 일치! 

#### **일반화:** 행렬의 row들의 특정 선형조합이 zero row이면, $$b_n$$들의 같은 선형조합도 zero이다. 

* 좌변이 zero이면 우변도 zero. 
* elimination 후에 zero row가 없으면 condition도 없음
  * **No condition:** 모든 $$\bm{b}$$에 대해 해가 존재!

#### **A. 조건을 만족할 경우**

* 세번째 방정식은 선형계에 새로운 정보를 주지 못함. 
* 사실상 2개의 방정식과 4개의 변수로 이루어져 있음. 

#### **B. 조건을 만족하지 않을 경우** 

* 좌변은 dependent한데 우변이 일치하지 않으면 모순. 
* 어떤 해로도 방정식계를 만족시키는 것이 불가능. 

### 3. 기하학적 해석을 통해 드러나는 조건 

* $$\bm{b}$$가 column space 안에 존재해야 함. 
* 위의 수식들과 같은 의미. 

## 해가 존재하는 조건 하에서 계속 진행해보자. 

* 조건에 맞는 $$\bm{b}$$를 준비하자: $$\begin{bmatrix} 1 \\5 \\ 6 \end{bmatrix}$$
* 2개의 방정식과 4개의 변수로 이루어져 있으므로, 해는 무수히 많을 것이다. 
* 이 때의 complete solution은 다음 두 부분의 합으로 구성된다. 
  * **\(Complete solution\)** = **\(Particular solution\)** + **\(Nullspace\)**
* 일반 계산방법에 대해 받아들이고, 이유는 나중에 생각해보자. 
  * Strang 교수님의 전개방식도 상당히 out of the blue 스타일.. 
  * 이런 방식이 효율적일 경우도 많은 것 같다. 

### 1. Particular solution\($$\bm{x}_p$$\) 구하기 

* 특수해라고 번역. 
* 무수히 많은 해 중 특수한 하나일 뿐이므로, 어떤 방법으로 구하든 자유이다. 
* 일단 아래와 같이 구한 뒤에, 그 이유를 생각해보자. 

#### 1. Set all free variables to zero. \(모든 free variable을 0으로 놓는다.\)

* $$x_2=\red0$$, $$x_4=\red 0$$이면, $$\begin{cases} \begin{aligned}x_1 +2x_3&=1 \\ 2x_3&=3 \end{aligned} \end{cases}$$

#### 2. Solve $$A\bm{x}=\bm{b}$$ for pivot variable. \(pivot variable에 대해 선형계를 푼다.\) 

* Back substitution으로 풀면: $$x_1=\green{-2}$$, $$x_3=\green{3/2}$$
* $$\bm{x}_p=\begin{bmatrix} \green{-2} \\ \red 0 \\  \green{3/2} \\ \red0 \end{bmatrix}$$

#### 이렇게 구하는 이유는 지난 강의의 nullsapce의 기저벡터 구할 때의 원리와 정확히 동일하다. 

* Particular solution은 그냥 평면의 아무 점이나 하나 구하면 된다고 생각하면 된다. \(일단 그렇게 믿자.\) 
* 4차원 공간 안의 2차원 평면 위의 임의의 점은 2개의 점을 특정하면 나머지 2개는 유일하게 구해진다.
* Free variable들은 자유롭게\(freely\) 선택하면 pivot variable들은 그에 따라 결정된다!
* 가장 '자연스럽고 쉬운' free variable의 선택은 전부 zero로 놓는 것이다. 

#### \(참고\) RREF까지 나아가면 동일한 결과를 행렬에서 바로 결과를 읽을 수 있다: 

* $$\left[ \begin{array}{cccc|c} 1&2&2&2&1 \\ 2&4&6&8&5 \\ 3&6&8&10&6 \end{array} \right] \rightsquigarrow \left[ \begin{array}{cccc|c} 1&2&2&2&1 \\ 0&0&2&4&3 \\ 0&0&0&0&0 \end{array} \right] \rightsquigarrow \left[ \begin{array}{cccc|c} \fbox1&2&0&-2&\green{-2} \\ 0&0&\fbox1&2&\green{3/2} \\ 0&0&0&0&0 \end{array} \right]$$ 
* 어차피 구해지는 원리는 정확히 똑같다. 
* 그러나, nullspace를 구하기 위해 어차피 RREF 형태로 만들거라면, 이렇게 하는게 더 효율적.  

### 2. Nullspace\($$\bm{x}_{n}$$\) 구하기 

* homogeneous solution\(제차해\)이라고도 한다. 
  * 용어의 뜻은 문서내 검색. 
* 지난 강의\(Lecture 7.\)에서 nullspace 구하는 법을 먼저 배운 이유가 바로 이 것이다. 
* 지난 강의에서 구했던 결과를 가져오면: 
  * $$\bm{x}_n=c_1 \begin{bmatrix} \green{-2}\\ \red1\\ \green 0\\\red 0 \end{bmatrix} + c_2 \begin{bmatrix} \green 2\\ \red0\\\green{-2}\\\red1 \end{bmatrix}$$ 

### 3. Complete solution\($$\bm{x}=\bm{x}_p+\bm{x}_n$$\) 구하기

* 완전해라고 번역. 
* 말 그대로 위의 두 녀석들을 더하면 끝이다: 
  * $$\bm{x}_p=\underbrace{\begin{bmatrix} \green{-2} \\ \red 0 \\  \green{3/2} \\ \red0 \end{bmatrix}}_{(1)} +c_1 \underbrace{\begin{bmatrix} \green{-2}\\ \red1\\ \green 0\\\red 0 \end{bmatrix}}_{(2)} + c_2 \underbrace{\begin{bmatrix} \green 2\\ \red0\\\green{-2}\\\red1 \end{bmatrix}}_{(3)}$$ 
* **\(1\)**: 모든 free variable이 0일때, $$A\bm{x}=\bm{b}$$의 해. 
* **\(2\)**, **\(3\)**: 각각의 free variable이 1이고 나머지가 0일때, $$A\bm{x}=\bm{0}$$의 해. 
  * 사실 별다른 테크닉을 외울 필요없이 위 내용들만 알고있으면 직접 풀 수 있다.  

위 두 타입의 subspace를 더한다는 것은 무슨 의미일까? 

* $$\begin{aligned} A\bm{x}_p&=\bm{b} \\ + \qquad A\bm{x}_n&=\bm{0}\\ \hline  \\[-3ex] A(\bm{x}_p + \bm{x}_n) &= \bm{b}\end{aligned}$$
* $$\bm{x}_p$$에 $$\bm{x}_n$$를 더해도 우변에 영향을 주지 않는다. 
  * Nullspace 안에 있는 어떤 벡터도 선형변환 후에는 영벡터.
  * 즉, 더해도 영향 없음.
* $$\bm{x}_p$$가 솔루션이면, $$\bm{x}_p+\bm{x}_n$$도 반드시 솔루션이다. 
* Nullspace까지 고려해야만 완전한\(complete\) 솔루션! 

\(Remark\) 위에서 구한 솔루션은 무한개의 다른 형태로 표현할 수 있다. 

* Particular solution는 평면 위의 아무 점만 가리키면 되지만, 계산이 편한 놈을 골랐을 뿐이다. 
* Nullspace도 기저벡터를 고를때 편의상 특정 spherical solution들로 골랐음을 기억하자. 

## 해공간의 기하학적 의미 

### 위 상황의 기하학적 해석을 통해 이러한 알고리즘의 의미를 이해해보자. 

#### Nullspace\($$\bm{x}_n$$\)는 원래 원점을 지나는 2차원 평면이었다. 

* \[Fig. 1\]에서 노란색 평면이 원점을 지나도록 평행이동된 상태. 

#### Particular solution\($$\bm{x}_p$$\)은 이 평면을 평행이동 시키는 벡터이다. 

* 평행이동된 평면\(노란색\)은 더이상 원점을 포함하지 않으므로 subspace가 아니다. 
* 그림의 $$\bm{x}_{c}$$\(파란색\)는 하나의 예시일 뿐, 평면의 모든 벡터가 될 수 있다.  

![\[Fig. 1\] &#xCD9C;&#xCC98;: https://twlab.tistory.com/22](../../.gitbook/assets/image%20%28108%29.png)

### 이게 대체 왜 이러한 기하학적 해석이 가능한 것일까? 

* 소거 후에 free column이 존재한다는 것은 column space가 전체 space를 span하지 못하는 것이다. 
* 이것은 선형변환의 결과가 전체 공간보다 작은 일부 subspace로 collapse된다는 뜻이다. 
  * \[Fig. 2\] 가장 왼쪽 상단 그림 \(2차원에서 1차원으로 collapsed\)
  * 이는 변환 후의 부호화된 면적\(determinant\)이 0이 되는 것으로 확인할 수 있다. 
* 또한, collapse된 차원만큼 원점으로 빨려들어가 소실되어야 한다는 것이다. 
  * \[Fig. 2\] 보라색 실선 \(=nullspace\)
* 선형변환이 일어난 후의 어떤 결과벡터\(노란색\)가 있을때, 변환 전의 벡터\(solution\)를 찾아보자. 
  * \[Fig.2\]의 그림들은 차례로 선형변환의 역방향 진행을 나타낸다. \(변환 후 $$\rightarrow$$변환 전\) 
* 공간의 collapsing 때문에 **하나의 결과벡터**\(좌상단\)가 **여러 개의 입력벡터**\(우하단\)에 대응된다. 
  *  역으로 생각하면, 여러 점\(입력공간\)들이 하나의 점\(출력공간\)으로 선형변환되었기 때문. 
* 재미 있는 것은 **여러 개의 입력벡터가 이루는 직선\(빨간색 실선\)이 nullspace와 평행**이라는 점이다. 
* 즉, column space위의 모든 점은 nullspace와 평행하는 subspace로 역변환될 수 있다. 
  * 좌상단 그림의 파란 실선 위의 모든 점에 대해 각각에 collapsed되는 직선이 존재. 
  * \(보라색과 빨간색 실선과 평행하는 직선들\) 

#### **결론:** $$A$$의 column space 위의 모든 벡터\($$\bm{b}$$\)는 nullspace와 평행인 subspace를 solution으로 갖는다. 

* \(완전해\) = \(nullspace 이동벡터\) + \( nullspace 전체\) 

![\[Fig. 2\]](../../.gitbook/assets/image%20%2893%29.png)

## Big picture: $$A\bm{x}=\bm{b}$$에 대한 해의 개수!

* 이것이 이 강의의 요약이다. 

#### Rank는 선형방정식계의 해의 개수에 대한 모든 것을 말해준다! 

|  | CASE 1 | CASE 2 | CASE 3 | CASE 4 |
| :---: | :---: | :---: | :---: | :---: |
| **Rank** | $$r=m=n$$ | $$r=n<m$$ | $$r=m<n$$ | $$r<m,  r<n$$ |
| **RREF** | $$R=I $$ | $$R=\begin{bmatrix} I \\ \bm{0} \end{bmatrix}$$ | $$R=\begin{bmatrix} I \ F \end{bmatrix}$$ | $$R= \begin{bmatrix} I  \ F \\\bm{0} \ \bm{0} \end{bmatrix}$$ |
| **\# solution** | $$ \text{1 solution}$$ | $$\text{0 or 1 solution}$$ | $$\infty \text{ solution}$$ | $$\text{0 or } \infty \text{ solution}$$  |
| **\# free var.** | $$0$$ | $$0$$ | $$n-r$$ | $$n-r$$ |

* **Zero row\(**$$\bm{0}$$**\)가 존재:** 해의 개수가 0일 수 있다.  **\(CASE 2, 4\)**
  * 매우 제한적인 $$b$$의 조건을 만족해야만 해가 존재 \(in $$\mathcal{C}(A)$$\) 
    * 실제 상황에서는 만족하는 것이 거의 불가능.
  * 역으로 $$\bm{0}$$가 존재하지 않으면, 조건없이 무조건 해가 존재한다. **\(CASE 1, 3\)**  
* **Free column\(**$$F$$**\)이 존재:** nullspace가 존재하므로, 무수히 많은 해가 존재한다. **\(CASE 3, 4\)**
  * 역으로 $$F$$가 존재하지 않으면, 단 하나의 해\(particular solution;$$\bm{x}_p$$\)만 존재한다. **\(CASE 1, 2\)**
    * free variable의 개수가 0이므로 nullspace의 차원도 0.
    * 오직 영벡터만이 nullspace\($$\bm{x}_n$$\)에 포함됨.  
* **CASE 1**은 역행렬이 존재하는 유일한 케이스
  * 구하는 방법: Gauss-Jordan elimination with augmented matrix. 
* **CASE 2**를 full column rank, **CASE 3**를 full row rank라고 부른다. 
* **CASE 4**는 $$m=n$$인 경우\(square matrix\)도 포함한다.   
* $$I$$와 $$F$$가 함께 존재할 경우는 서로 행이 뒤섞여 있을 수 있다.  

## 기하학적 원인의 관점에서 재해석해보자. 

![\[Fig. 3\]](../../.gitbook/assets/image%20%2838%29.png)

#### **\[Fig. 3\]은 CASE 2,3,4를 조금 더 세분화해서 나타낸 것이다.** 

* 각 원의 크기는 차원의 크기를 의미한다. 
* $$n$$에서 $$r$$방향으로 변화를 표현하는 사다리꼴 도형은 선형변환을 의미한다. 
* 입력은 항상 전체 차원에서 이루어진다. 
* column space는 전체 출력차원을 span하지 않을 수 있다. 
* column space의 차원은 입력이나 출력차원보다 클 수 없다. 
* 사다리꼴은 오른쪽 높이가 더 넓어질 수 없다.  \(유지되거나 좁아지는 것만 가능\) 

{% hint style="info" %}
#### **무수히 많은 해가 존재할 수 있는 경우\(**$$F$$**가 존재\) - \[Fig. 3\] 상단 그림**  

* _빗금친_ 사다리꼴의 높이가 오른쪽으로 갈수록 줄어드는 경우 해당. 
* 즉, 고차원\($$n$$\)의 입력이 저차원\($$r$$\)의 column space로 찌부러진다. \($$n<r$$\) 
* 찌부러드는 차원만큼 nullspace로 옮겨진다. \(nullspace의 기저가 되는 $$F$$의 행 개수 증가\) 
* 해가 존재한다면, 하나의 출력에 많은 입력이 대응된다. _\(무수히 많은 해\)_ 
{% endhint %}

{% hint style="info" %}
#### **해가 존재하지 않을 확률이 높은 경우\(**$$\bm{0}$$가 존재\) - \[Fig. 3\] 하단 그림 

* _빗금친_ 원 사이의 간격이 존재하는 경우 해당. 
* Column space\($$r$$\)가 $$\bm{b}$$의 활동공간\($$m$$\)보다 작다. \($$r<m$$\) 
* 선형종속인 방정식들의 우변에 모순이 전혀 없을때만 $$\bm{b}$$가 column space 안에 존재한다. 
* 매우 운이 좋지 않다면, $$\bm{b}$$는 column space 밖에 존재할 것이다. _\(해가 없음\)_ 
{% endhint %}

{% hint style="warning" %}
#### $$\bm{0}$$가 $$F$$보다 강하다!

* 둘이 동시에 나타날 경우, zero-row가 우선한다. 
* 즉, 해가 존재할 조건을 충족하고 난 다음에야, 무수히 많이 존재할 수도 있는 것이다.  
{% endhint %}

#### Invertible square matrix는 아주 이상적인 상황이다. 

* 우리가 강의 초기에 가정 했던 상황\[Fig. 4\]이 얼마나 이상적인가를 그림으로 비교해보자. 
* 실제 상황에서는 기가 막힌 인연이 있지 않고서는 만나기 힘든 아름다운 그림이다. 

![\[Fig. 4\]](../../.gitbook/assets/image%20%2869%29.png)

