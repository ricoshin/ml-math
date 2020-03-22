# Lecture 17-2. Orthogonal Matrices and Gram-Schmidt

## QR 분해법 \( $$A=QR$$ \)

* $$Q$$는 원래 행렬 $$A$$의 basis를 새롭게 선형조합한 것이다. 
* 즉, Gram-Schmidt 과정 자체를 행렬\($$R$$\)로써 표현할 수 있다.
  * $$A=QR$$의 형태로 최종 분해가능하다.  
  * $$ \begin{bmatrix} |&|&|\\\bm{a}&\bm{b}&\bm{c}\\|&|&|\end{bmatrix}=\begin{bmatrix} |&|&|\\\bm{q}_1&\bm{q}_2&\bm{q}_3\\|&|&|\end{bmatrix}R$$
  * Elimination 과정을 $$A=LU$$의 형태로 표현한 것과 유사. 

#### 행렬$$R$$을 구해보자.

* $$A=QR$$의 양변에 $$Q^\top$$를 곱해주면:
  * $$Q^\top A=\underbrace{Q^\top Q}_{I}R=R$$ 
  * 즉, $$R=Q^\top A$$
* $$R=\begin{bmatrix} \text{---} \ \bm{q}_1^\top \ \text{---} \\ \text{---} \ \bm{q}_2^\top \ \text{---} \\ \text{---} \ \bm{q}_3^\top \ \text{---}   \end{bmatrix}\begin{bmatrix} |&|&|\\\bm{a}&\bm{b}&\bm{c}\\|&|&|\end{bmatrix}=\begin{bmatrix} \bm{q}_1^\top\bm{a} & \bm{q}_1^\top\bm{b} & \bm{q}_1^\top\bm{c} \\ \bm{q}_2^\top\bm{a} & \bm{q}_2^\top\bm{b} & \bm{q}_2^\top\bm{c} \\ \bm{q}_3^\top\bm{a} & \bm{q}_3^\top\bm{b} & \bm{q}_3^\top\bm{c}  \end{bmatrix}$$

#### 행렬$$R$$의 기하학적 의미는?

* \*\*\*\*$$\bm{q}_1, \bm{q}_2, \bm{q}_3$$**를 새로운 좌표계로 했을때,** $$\bm{a},\bm{b},\bm{c}$$**의 좌표를 각각의 열에 나타낸 행렬.** 
  * unit vector와의 dot product는 그 방향으로의 성분을 의미하므로. 
* 이 좌표들\($$R$$\)로 $$\bm{q}_1, \bm{q}_2, \bm{q}_3$$을 선형 재조합하면? \($$QR$$\)  
  * 다시 벡터 $$\bm{a}, \bm{b},\bm{c}$$가 나온다.  \($$=A$$\) 

#### 입력벡터와 결과벡터의 수직관계를 알아보자. 

* 첫번째 벡터$$\bm{a}$$과 수직이 되는 $$\bm{q}$$벡터: $$\bm{q}_2, \bm{q}_3$$
* 두번째 벡터$$\bm{b}$$와 수직이 되는 $$\bm{q}$$벡터: $$\bm{q}_3$$
* 세번째 벡터 $$\bm{c}$$와 수직이 되는 $$\bm{q}$$벡터: 없음 
* 즉, $$\bm{q}_i$$벡터는 $$i-1$$번째까지의 입력벡터들에 대해서 모두 수직.

#### 그러므로, $$R$$의 대각원소 아래의 값들은 모두 0 $$\Rightarrow$$ Upper triangular matrix 

* $$R=\begin{bmatrix} \bm{q}_1^\top\bm{a} & \bm{q}_1^\top\bm{b} & \bm{q}_1^\top\bm{c} \\ 0 & \bm{q}_2^\top\bm{b} & \bm{q}_2^\top\bm{c} \\ 0 & 0 & \bm{q}_3^\top\bm{c}  \end{bmatrix}$$ 
* $$\bm{q}_1, \bm{q}_2, \bm{q}_3$$좌표계 기준 $$\bm{a},\bm{b},\bm{c}$$의 좌표가 그대로 나타나있다. \[Fig. 1\]
  * 각 벡터의 어떤 성분이 0인지 기하학적으로 확인해보자. 
  * 수직관계에 의한 위 행렬의 모습과 일치함을 알 수 있다.

![\[Fig. 1\]](../../../.gitbook/assets/image%20%2876%29.png)

#### 또한 대각원소들은 항상 positive이다. 

* 예를 들어, 세번째 벡터$$\bm{c}$$의 $$\bm{q}_3$$방향 성분은 $$\bm{C}$$이며, 이 셋은 항상 같은 방향이다. 
* 시작부터 선형독립 벡터에서 출발했으므로 projection은 영벡터가 될 수 없다.  
* 영벡터가 아닌 같은 방향의 벡터간 dot product는 항상 positive이다.   
* \[Fig. 1\]에서 $$i$$번째 벡터의 $$i$$번째 성분이 항상 양수임을 확인해보자.  

{% hint style="info" %}
#### QR decomposition\($$A=QR$$\)의 모양은 아래와 같다. 

* $$\begin{bmatrix} |&|&|\\\bm{a}&\bm{b}&\bm{c}\\|&|&|\end{bmatrix}_{m\times n}=\begin{bmatrix} |&|&|\\\bm{q}_1&\bm{q}_2&\bm{q}_3\\|&|&|\end{bmatrix}_{m\times n}\begin{bmatrix} \bm{q}_1^\top\bm{a} & \bm{q}_1^\top\bm{b} & \bm{q}_1^\top\bm{c} \\ 0 & \bm{q}_2^\top\bm{b} & \bm{q}_2^\top\bm{c} \\ 0 & 0 & \bm{q}_3^\top\bm{c}  \end{bmatrix}_{n\times n}$$ 
* $$R$$의 대각 원소는 positive.
{% endhint %}

## QR분해를 활용해 least squares를 쉽게 풀어보자. 

{% hint style="danger" %}
시작부터 $$Q$$의 형태에서 출발하는 경우와 QR분해를 통해 만들어가는 경우의 차이를 유의하자.
{% endhint %}

#### **Original least squares** 공식

* $$A^\top A\hat{\bm{x}}=A^\top\bm{b}$$

#### QR분해\($$A=QR$$\)를 대입해보자.  

* $$A^\top=(QR)^\top=R^\top Q^\top$$
* $$A^\top A=R^\top Q^\top QR=R^\top R$$
* **그러므로 new least squares:**
  * $$R^\top R\hat{\bm{x}}=R^\top Q^\top \bm{b} \quad \cdots (1)$$

#### $$R$$과 $$R^\top$$는 역행렬 존재 

* Upper triangular matrix는 대각 성분에 0이 없으면 역행렬 존재.
* Full column & row rank이기 때문.
* $$R$$의 대각 원소는 항상 positive\(non-zero\).
* $$r=n=m$$이므로 전치행렬도 역행렬 존재.

#### \(1\)의 양변에 $$({R^\top})^{-1}$$을 곱하면:

* $$R\hat{\bm{x}}=Q^\top\bm{b}\quad \cdots (2)$$

#### \(2\)의 양변에 $$R^{-1}$$을 곱하면: 

* $$\hat{\bm{x}}=R^{-1}Q^\top\bm{b}\quad \cdots (3)$$ 

{% hint style="info" %}
**Least squares \(with QR decomposition\)**

* \*\*\*\*$$R^\top R\hat{\bm{x}}=R^\top Q^\top \bm{b}$$ 
* $$R\hat{\bm{x}}=Q^\top\bm{b}$$ 
* $$\hat{\bm{x}}=R^{-1}Q^\top\bm{b}$$ 
{% endhint %}

#### 장점은?

* $$A^\top A\hat{\bm{x}}=A^\top\bm{b}$$ 를 구하려면 새로운 선형방정식계를 완전히 풀어야한다. \(소거법 사용\) 
* 그러나, QR분해를 해주기만 하면, $$R\hat{\bm{x}}=Q^\top\bm{b}$$ 의 꼴에서 바로 back-substitution이 가능해진다. 

## Modified Gram-Schmidt

Text book에 간략하게 소개되어 있는데 원래 Gram-Schmidt와 다음 두가지가 다르다. 

1. unit length로의 정규화를 마지막이 아닌 매번 해준다. 
2. 하나의 벡터를 직교화함에 있어 여러 성분을 한번에 빼주지 않고 하나씩 빼준다. 

이렇게 해주는 것이 수치적으로 더 안정적이라고 한다. 

### Lec. 17-1.의 동일한 예시를 수정된 버전으로 수행해보자. 

\(1\)$$\bm{a}\rightarrow\bm{A}$$ 

* \*\*\*\*$$\bm{q}_1=\dfrac{\bm{A}}{\Vert\bm{A}\Vert}$$

\(2\) $$\bm{b}\rightarrow\bm{B}$$ 

* $$\bm{b}$$에 존재하는 $$\bm{A}$$성분\($$\bm{b}$$의 $$\bm{A}$$에 대한 projection; $$P_\bm{A}\bm{b}$$\)을 제거해준다.
* $$\bm{B}=\bm{b}-P_{\bm{q}_1}\bm{b}=\bm{b}-\dfrac{\bm{q}_1^\top \bm{b}}{\bm{q}_1^\top \bm{q}_1}\bm{q}_1=\bm{b}-{\color{blue}(\bm{q}_1^\top\bm{b})}\bm{q}_1$$
  *  \($$\bm{q}_1^\top\bm{q}_1=1$$\) 이므로 분모계산 불필요. **\(다른점 1\)**
*  ****$$\bm{q}_2=\dfrac{\bm{B}}{\Vert\bm{B}\Vert}$$ 

\(2\) $$\bm{c}\rightarrow\bm{C}$$ 

* $$\bm{c^*}=\bm{c}-P_{\bm{q}_1}\bm{c}=\bm{c}-\dfrac{\bm{q}_1^\top \bm{c}}{\bm{q}_1^\top \bm{q}_1}\bm{q}_1=\bm{c}-{\color{blue}(\bm{q}_1^\top\bm{c})}\bm{q}_1$$ 
* $$\bm{C}=\bm{c^*}-P_{\bm{q}_2}\bm{c^*}=\bm{c^*}-\dfrac{\bm{q}_2^\top \bm{c^*}}{\bm{q}_2^\top \bm{q}_2}\bm{q}_2=\bm{c^*}-{\color{blue}(\bm{q}_2^\top\bm{c^*})}\bm{q}_2$$ 
  * 2개의 성분을 한번에 하나씩 제거. **\(다른점 2\)** 
* $$\bm{q}_3=\dfrac{\bm{C}}{\Vert\bm{C}\Vert}$$ 

## 고백: MATLAB 등은 QR분해시 Gram-Schmidt를 사용하지 않는다!

* 속았다. 실제론 Householder reflections 라는 더 진보된 방법을 사용한다고 한다. 
  * 결과는 같지만, 계산과정이 더 좋다. 
* Reflection matrix는 $$I-2\bm{u}\bm{u}^\top$$으로 표현할 수 있다. \(Chapter 9.에서 다룰 것이다.\)
* Gram-Schmidt는 실용성을 떠나 선형대수의 깊은 이해에 도움이 된다. 



