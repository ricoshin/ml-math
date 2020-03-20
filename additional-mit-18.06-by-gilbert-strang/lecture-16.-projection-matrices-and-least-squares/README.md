# Lecture 16. Projection Matrices and Least Squares

## Recap: Projection Matrix

* 이전 챕터를 복습해보자. 

{% page-ref page="../lecture-15.-projections-onto-subspaces.md" %}

$$
P=A(A^\top A)^{-1}A^\top
$$

* $$P$$는 어떤 행렬 $$A$$가 주어졌을때, 이 행렬의 column space로의 projection을 생성하는 행렬이다.

#### If $$\bm{b}$$ in column space: $$P\bm{b}=\bm{b}$$

* subspace 안에 있는 벡터의  projection은 자기 자신.
* $$\bm{b}$$가 column space안에 존재하면 $$A$$의 column들의 선형조합으로 표현할 수 있으므로: $$\bm{b}=A\bm{x}$$
* $$P\bm{b}=A(A^\top A)^{-1}A^\top \underbrace{\bm{b}}_{= \ A\bm{x}}=A\cancel{(A^\top A)^{-1}A^\top  A}\bm{x}=A\bm{x}=\bm{b}$$ **\(확인\)**

#### If $$\bm{b}$$$$\perp$$column space: $$P\bm{b}=\bm{0}$$

* subspace와 수직인 벡터의 projection는 원점으로. 
* $$\bm{b}$$가 column space와 수직인 left nullspace에 포함되어 있으므로: $$A^\top\bm{b}=\bm{0}$$
* $$P\bm{b}=A(A^\top A)^{-1}\underbrace{A^\top\bm{b}}_{= \ \bm{0}}=\bm{0}$$ **\(확인\)**

### 벡터 $$\bm{e}$$의 재발견: Left nullspace로의 projection!

![\[Fig. 1\]](../../.gitbook/assets/image%20%2845%29.png)

#### \[Fig. 1\]의 왼쪽 그림은 지난 챕터에서 본 그림이다. 

* 여기서 직교성을 이용하기 위해 사용했던 오차벡터 $$\bm{e}=\bm{b}-\bm{p}$$를 기억하는가?
* 사실 $$\bm{e}$$는 또다른 의미를 가지고 있었다. 
* 바로 $$\bm{b}$$의 $$A$$의 **left nullspace에 대한 projection과 같다**는 것이다. **\(오른쪽 그림\)** 

#### 이제 같은 식을 다음과 같이 표현하는 것이 더 자연스럽다: $$\bm{b}=\bm{p}+\bm{e}$$

* 지난 챕터에서 $$\bm{p}=P\bm{b}$$임을 이미 알고 있다. \(projection onto subspace\)
* 등식이 성립하려면 $$\bm{e}=(I-P)\bm{b}$$임을 새로 알 수 있다. \(projection onto $$\perp$$subspace\)
* $$\bm{e}=\red{\bm{p}}+{\color{blue}\bm{e}}=\red{P\bm{b}}+{\color{blue}(I-P)\bm{b}}$$

#### 두 개의 성분의 합으로 분리되었다! 

* 어떤 벡터든 서로 orthogonal한 두개의 subspace에 대한 projection으로 나타낼 수 있다. 

## 실제 projection을 활용의 예: Least Squares\(최소제곱법\)

### 다음 그림\[Fig.2\]의 세 점을 대표하는 최선의 직선을 구하라. 

* 이러한 문제를 통계학자들은 linear regression\(선형회귀\)라고 부른다. 

![\[Fig. 2\]](../../.gitbook/assets/image%20%2820%29.png)

* 세 점 $$\{(1,1), (2,2), (3,2)\}$$을 동시에 만족하는 직선 $$y=x_1+x_2t$$은 존재하지 않는다. 
  * Not solvable! 
* 세 점은 세 개의 방정식을 만들어 내며, 이를 linear system으로 표현할 수 있다. 
  * $$A\bm{x}=\begin{bmatrix}1&1\\1&2\\1&3\end{bmatrix}\begin{bmatrix}x_1 \\x_2\end{bmatrix}=\begin{bmatrix} 1 \\2 \\3 \end{bmatrix}=\bm{b}$$
  * $$\bm{b}$$는 $$A$$의 column space 안에 존재하지 않는다. 
    * Not solvable!
* 시스템의 해가 존재하지 않을때, 그림의 빨간 직선과 같은 가장 최선의 직선을 어떻게 구할 수 있을까? 
  * 최소제곱법을 사용해보자! 

### 최소제곱법은 다음 두가지의 관점으로 해석할 수 있다. \[Fig. 3\]

![\[Fig. 3\] Two pictures of Least Squares Regression](../../.gitbook/assets/image%20%2883%29.png)

* 최소제곱법이란 \(실제값과의\) 오차의 제곱합을 최소화하는 직선을 찾는 방법이다.
* 위 두 그림은 같은 상황\(최소제곱법\)을 다른 시각에서 표현한 것이다. 
  * **왼쪽 그림**은 실제 fitting하고자 하는 line\($$\hat{\bm{x}}$$에 의해 결정\)을 중심으로 표현된다. 
  * **오른쪽 그림**은 vector space에서 해석되는 그림으로 원래 line은 드러나지 않는다. 

#### \(1\) 왼쪽 그림의 관점 

* 주어진 값 $$b_n$$과 직선의 원소인 $$p_n$$사이의 오차 $$e_n$$을 최소화하는 직선\($$x_m$$\)을 찾는 것. 
* **Overall error:** 각 오차들이 항상 양수를 갖도록 제곱한 뒤, 모두 더한 것.
* **Estimation:** $$\displaystyle \hat{\bm{x}}=\underset{\hat{\bm{x}}}\text{argmin} \ {e_1}^2+{e_2}^2+{e_3}^2=\underset{\hat{\bm{x}}}\text{argmin}  \sum_{i=1}^{3} {e_i}^{2}=\underset{\hat{\bm{x}}}\text{argmin} \sum_{i=1}^{3}{(b_i-p_i)}^2$$

#### \(2\) 오른쪽 그림의 관점 

* 주어진 벡터 $$\bm{b}$$와 column space의 원소 $$\bm{p}$$사이의 오차벡터 $$\bm{e}$$를 최소화하는 선형조합 $$\bm{x}$$를 찾는 것.
* **Overall error:** 오차벡터 $$\bm{e}$$의 길이의 제곱한 것.  
  * 제곱하는 이유는 계산과정에서 제곱근을 취하는 불필요함을 없애기 위한 것이다. \(계산의 편이성\) 
  * 제곱근은 단조증가 함수이므로 최소값을 바꾸지 않으므로, 최적화 결과에는 영향이 없다. 
* **Estimation:** $$\hat{\bm{x}}=\underset{\hat{\bm{x}}}\text{argmin}\Vert A\bm{x}-\bm{b}\Vert^2  =\underset{\hat{\bm{x}}}\text{argmin}{\Vert \bm{e}\Vert}^2$$
  * $$\bm{b}$$의 projection의 선형조합을 찾는 과정이 위의 최소값을 만족하는 $$\hat{\bm{x}}$$를 찾는 것과 같다.
  * 왼쪽 그림에서의 결과와 수치적으로 같음을 알 수 있다.  

### 최소제곱법의 단점: Outlier\(이상치\)에 취약하다!

![\[Fig. 4\]](../../.gitbook/assets/image%20%2832%29.png)

* 처음 세 점에서 매우 멀리 떨어진 **네번째 점을 추가**했다고 가정해보자. \[Fig. 4\] 
* 이런 점을 **outlier**\(이상치\)라고 부르며, 보통 원래의 패턴에서 벗어난 **오류**나 **특이값**일 확률이 높다. 
* 오차에 제곱을 하는 최소제곱법의 특성상 이러한 outlier에 의해 **overall error는 크게 왜곡**될 수 있다. 
* 그렇다고 최소제곱법의 가치가 모두 사라지는 것은 아니지만, 염두해 두어야할 사실이다. 

### 각각의 관점에서 $$\hat\bm{x}$$을 구해보자.  

#### \(1\) 왼쪽 그림의 관점

* **미분을 이용**해서  overall error를 최소로 만드는 $$\hat\bm{x}=\begin{bmatrix}\hat{x}_1\\\hat{x}_2\end{bmatrix}$$를 찾아보자. 
* 각 변수의 **partial derivative**\(편미분\)가 0이 되는 값을 구하면 최소점이 된다. 
* $$\displaystyle  e_{\text{overall}}=\sum_{i=1}^{3}{(b_i-p_i)}^2=(\hat{x}_1+\hat{x}_2-1)^2+(\hat{x}_1+2\hat{x}_2-2)^2+(\hat{x}_1+3\hat{x}_2-2)^2$$
* $$\begin{aligned}\dfrac{\partial e_{\text{overall}}}{\partial \hat{x}_1}&=2(\hat{x}_1+\hat{x}_2-1)+2(\hat{x}_1+2\hat{x}_2-2)+2(\hat{x}_1+3\hat{x}_2-2)\\&=6\hat{x}_1+12\hat{x}_2-10\\&=3\hat{x}_1+6\hat{x}_2-5=0 \end{aligned}$$
* $$\begin{aligned}\dfrac{\partial e_{\text{overall}}}{\partial \hat{x}_2}&=2(\hat{x}_1+\hat{x}_2-1)+4(\hat{x}_1+2\hat{x}_2-2)+6(\hat{x}_1+3\hat{x}_2-2)\\&=12\hat{x}_1+28\hat{x}_2-22\\&=6\hat{x}_1+14\hat{x}_2-11=0 \end{aligned}$$ 
* 다음 두 연립방정식을 만족하는 $$\hat{\bm{x}}$$가 최종 답이 된다. 
  * $$\begin{cases}  3\hat{x}_1+\phantom{0}6\hat{x}_2-\phantom{0}5=0 \\ 6\hat{x}_1+14\hat{x}_2-11=0\end{cases}$$

#### \(2\) 오른쪽 그림의 관점 

* Lec. 15에서 배운 방법으로 **projection을 만드는 선형조합**을 찾아보자. 
* $$A\bm{x}=\bm{b}$$
  * $$\begin{bmatrix}1&1\\1&2\\1&3\end{bmatrix}\begin{bmatrix}x_1 \\x_2\end{bmatrix}=\begin{bmatrix} 1 \\2 \\2 \end{bmatrix}$$
* $$A^\top A\hat{\bm{x}}=A^\top\bm{b}$$
  * $$A^\top[A|\bm{b}]=\begin{bmatrix}1&1&1\\1&2&3\end{bmatrix}\left[ \begin{array}{cc|c} 1&1&1\\1&2&2\\1&3&2\end{array}\right]=\left[ \begin{array}{cc|c} 3&6&5 \\6&14&11 \end{array} \right]=[A^\top A|A^\top \bm{b}]$$
  * 즉, $$ \begin{bmatrix} 3&6 \\ 6&14 \end{bmatrix} \hat{\bm{x}}=\begin{bmatrix}5\\11\end{bmatrix}$$: Normal equation! 
  * **\(1\)에서의 연립방정식과 같다!** 
* elimination + back-substitution으로 해를 구하면: 
  * $$\hat\bm{x}=\begin{bmatrix}\hat{x}_1\\\hat{x}_2\end{bmatrix}=\begin{bmatrix}2/3\\1/2\end{bmatrix}$$ 

### 구한 $$\hat{\bm{x}}$$을 기준으로 그림을 완성해보자. 

![\[Fig. 5\]](../../.gitbook/assets/image%20%28146%29.png)

#### 앞서 구한 해 $$\hat{\bm{x}}$$가 의미하는 바는?

* 왼쪽 그림에서의 직선을 표현하는 변수 $$\hat{x}_1, \hat{x}_2$$
  * 오른쪽 그림에서 $$\bm{p}$$를 만드는 선형조합 $$\hat{\bm{x}}$$

#### $$\bm{p}$$를 구해보자.

* 왼쪽 그림의 구한 직선 $$y=2/3+1/2t$$ 위의 점들의 집합
  * 오른쪽 그림에서의  $$A\hat\bm{x}=\bm{p}$$

#### $$\bm{e}$$를 구해보자. 

* 직선 위의 점들과 기존  주어진 점들의 차이들의 집합  
  * 오른쪽 그림에서의 $$\bm{b}-\bm{p}=\bm{e}$$

#### 확인해보자. 

* $$\bm{p}$$와 $$\bm{e}$$가 오른쪽 그림과 같이 수직을 이루는가?
  *  ****$$\bm{p}\cdot\bm{e}=\begin{bmatrix} 7/6\\10/6\\13/6\end{bmatrix}\cdot\begin{bmatrix} -1/6\\2/6\\-1/6\end{bmatrix}= \dfrac{-7+20-13}{6}=0$$\(**YES!**\)
* 확인해보면 $$\mathcal{C}(A)$$의 다른 벡터들도 마찬가지로 수직을 이룬다. \(생략\) 

## 다음을 증명해보자.

Lec 15.에서 약속했던 다음에 대한 증명을 해보자.

> 만약 $$A$$가 선형독립인 column을 가지면 $$A^\top A$$의 역행렬이 존재한다.

#### 행렬 $$A$$가 무엇을 만족함을 증명해야 하는가?

* 행렬 $$A$$는 선형독립인 column을 갖는다고 **가정**하자. 
* $$A^\top A$$의 역행렬이 존재하려면, $$A^\top A\bm{x}=\bm{0}$$의 해는 $$\bm{x}=\bm{0}$$이 유일해야 한다. 

#### Trick: $$A^\top A\bm{x}=\bm{0}$$의 양변에 $$\bm{x}$$와의 dot product를 취해보자.

* $$\bm{x}^\top A^\top A \bm{x}=(A\bm{x})^\top(A\bm{x})=\bm{x}^\top\bm{0}=0$$

#### $$(A\bm{x})^\top(A\bm{x})=0$$의 의미는?

* 벡터 $$A\bm{x}$$의 자기 자신과의 dot product가 0이다. 
* 자기 자신과의 dot product는 벡터길이의 제곱이다. \($$\bm{x}^\top\bm{x}=\Vert \bm{x} \Vert$$\)
* 벡터길이의 제곱이 0인 벡터는 영벡터가 유일하다.
* **그러므로,** $$A\bm{x}=\bm{0}$$\*\*\*\*

#### 처음의 가정에 의하면\(행렬 $$A$$는 선형독립인 column을 갖는다\):

* $$A$$의 nullspace에는 영벡터가 유일하다.
* $$ \bm{x}=\bm{0}$$ **\(증명완료\)**



