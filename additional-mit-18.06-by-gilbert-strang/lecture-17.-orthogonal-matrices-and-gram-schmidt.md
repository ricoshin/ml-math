# Lecture 17-1. Orthogonal Matrices and Gram-Schmidt

## Introduction 

### Orthogonal vectors 

* 벡터의 집합 $$\bm{q}_1, \ \cdots, \ \bm{q}_n$$이 있을때, 다음을 만족하면 orthogonal하다고 한다: 
  * $$\bm{q}_i^\top\cdot \bm{q}_j\begin{cases}0\quad  \text{if} \ \ i\neq j \\1 \quad \text{if} \ \ i= j \end{cases}$$
  * 즉, 모든 벡터가 **다른 모든 벡터에 대해 수직**.
* 한 단계를 더해서, 그 **크기를 모두 1로**\(unit vector\) 만들어주면 **orthonormal**하다고 한다.
* Column들이 orthonormal vector들로 이루어진 경우 반드시 선형독립이다. 
* 이러한 orthonormal basis를 갖는 행렬이 이번 lecture의 주제이다.  

### Orthogonal matrix\(직교행렬\) 

#### 모든 column이 orthonormal vector로 이루어진 행렬을 $$Q$$라고 하자. 

* $$Q=\begin{bmatrix} | & & | \\ \bm{q}_1&\cdots&\bm{q}_n\\|&&|\end{bmatrix}$$
* 이제부터 알파벳 q/Q는 항상 orthonormal 벡터 혹은 그들로 이루어진 행렬을 의미.
  * Rectangular matrix도 포함! 
* $$Q^\top Q=\begin{bmatrix} \text{---} \ \bm{q}_1^\top \ \text{---} \\ \vdots \\ \text{---} \ \bm{q}_n^\top \ \text{---} \end{bmatrix}\begin{bmatrix} | & & | \\ \bm{q}_1&\cdots&\bm{q}_n\\|&&|\end{bmatrix} =\begin{bmatrix}1&0&\cdots\\0&1&\cdots\\\vdots&\vdots&\ddots \end{bmatrix}=I_{n\times n}$$

#### Orthogonal matrix는 _square_인 $$Q$$에게만 붙일 수 있는 이름이다. 

* Square이면, $$Q$$의 inverse가 존재할 수 있다: $$Q^\top Q = I \ \Rightarrow Q^\top=Q^{-1}$$
* Inverse는 left inverse이면서 right inverse이므로: $$QQ^\top=QQ^{-1}=Q^{-1}Q=Q^\top Q=I$$
* \(TODO\) square가 아닐땐 left inverse? 
  * $$Q^\top Q=I$$ but, $$QQ^\top\neq I$$

{% hint style="info" %}
#### Rectangular\(but tall\) matrix $$Q_{m\times n}$$\($$m\geq n$$\)

* $$Q^\top Q=I$$

#### Square matrix $$Q_{m\times n}$$\($$m = n$$\)

* $$Q^\top=Q^{-1}$$
* $$QQ^\top=I$$

#### Rectangular\(but wide\) matrix $$Q_{m\times n}$$ \($$m \lt n$$\)

* 존재하지 않음. 
* column space의 차원보다 많은 수의 orthogonal basis를 찾을 수 없음. 
{% endhint %}

#### 직교행렬의 example

* **Permutation matrix:**$$Q^\top Q=\begin{bmatrix}0&0&1\\1&0&0\\0&1&0\end{bmatrix}\begin{bmatrix}0&1&0\\0&0&1\\1&0&0\end{bmatrix}=I$$
* **Rotation matrix:**$$Q=\begin{bmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{bmatrix}$$
  * 각 column의 dot product는 1이고 column끼리의 dot product는 0이다. 
* **Hadarmard matrix** $$H$$**를** $$\sqrt n$$**으로 나눈 행렬:**
  * **Hadarmard matrix:** +1과 -1만을 원소로 가지며 모든 행과 열이 서로 orthogonal한 행렬. 
  * $$\dfrac{1}{\sqrt 2}H_2=\dfrac{1}{\sqrt 2}\begin{bmatrix} 1&1\\1&-1\end{bmatrix}$$
  * $$\dfrac{1}{\sqrt 4}H_4=\dfrac{1}{ 2}\begin{bmatrix} H_2&H_2\\H_2&-H_2\end{bmatrix}=\dfrac{1}{2}\begin{bmatrix} 1&1&1&1\\1&-1&1&-1\\1&1&-1&-1\\1&-1&-1&1\end{bmatrix}$$ 

## Orthogonal column을 가지면 왜 좋은 걸까? 

#### 우리가 기존에 알던 formula들의 행렬들이 orthogonal basis를 가진다면? 

* 계산 자체가 매우 간결해진다. 
  * 특히 $$Q^\top Q(=I)$$형태가 포함된 계산. 
* 같은 계산이라도 계산 정밀도에 더 좋다. 
  * overflow/underflow가 발생하지 않는다. 

### 간단한 projection matrix

#### Lec. 16.에서 배운 projection matrix를 살펴보자. 

* $$A$$가 $$Q$$였다면 다음과 같게 된다. 

$$
P=Q(Q^\top Q)^{-1}Q^\top=QQ^\top(=I, \ \text{if} \ Q \text{  is square matrix) }
$$

* $$Q$$가 rectangular matrix이면, $$P=QQ^\top$$
  * $$Q^\top Q=I$$의 특성을 활용하면 식이 매우 간단해짐을 알 수 있다. 
* $$Q$$가 square matrix이면, $$P=I$$
  * $$\mathcal{C}(Q)$$는 전체공간이고, 전체공간으로의 projection은 입력벡터 자신이다. 

{% hint style="info" %}
#### Rectangular\(but tall\) matrix $$Q_{m\times n}$$\($$m\geq n$$\)

* $$P=QQ^\top$$

#### Square matrix $$Q_{m\times n}$$\($$m = n$$\)

* $$P=I$$
{% endhint %}

#### Projection의 실제 결과\( $$\bm{p}$$ \)는 어떻게 될까? 

![\[Fig. 1\] Q&#xC758; basis vector\(&#xC8FC;&#xD669;\)&#xB4E4;&#xC740; &#xD06C;&#xAE30;&#xAC00; 1&#xC774;&#xB2E4;. &#xAC1C;&#xBCC4; projection\(&#xBE68;&#xAC15;\)&#xB4E4;&#xBCF4;&#xB2E4; &#xB354; &#xC791;&#xC740; &#xD06C;&#xAE30;&#xC77C; &#xC218;&#xB3C4; &#xC788;&#xB2E4;.](../.gitbook/assets/image%20%28127%29.png)

![\[Fig. 2\] Orthonormality&#xAC00; &#xAE68;&#xC9C0;&#xBA74; &#xB354;&#xC774;&#xC0C1; &#xAC1C;&#xBCC4; projection&#xC758; &#xD569;&#xACFC; &#xC77C;&#xCE58;&#xD558;&#xC9C0; &#xC54A;&#xB294;&#xB2E4;.](../.gitbook/assets/image%20%28138%29.png)

* $$Q$$가 rectangular matrix이면, $$\bm{p}=P\bm{b}=QQ^\top\bm{b}$$ 
  *  **\[Fig. 1\] 좌측**
  * $$\bm{p}=\begin{bmatrix} | & & | \\ \bm{q}_1&\cdots&\bm{q}_n\\|&&|\end{bmatrix}\begin{bmatrix}\bm{q}_1^\top\bm{b}  \\ \vdots \\  \bm{q}_n^\top\bm{b}  \end{bmatrix}=\bm{q}_1(\bm{q}_1^\top\bm{b})+\cdots+\bm{q}_n(\bm{q}_n^\top\bm{b})$$: 괄호 안은 숫자. 
  * 즉, projection은 각각의 orthonormal basis에 대한 개별 projection의 벡터합과 같다. 
  * **이는 orthogonality나 unit length 둘 중 하나라도 만족하지 않으면 이는 성립하지 않음.** \[Fig. 2\]
* $$Q$$가 square matrix이면, $$\bm{p}=P\bm{b}=I\bm{b}=\bm{b}$$
  * **\[Fig. 1\] 우측** 
  * Rectangular 케이스에 포함되지만, $$Q$$가 운좋게 전체 차원을 span할 경우이다. 
  * $$\mathcal{C}(Q)$$는 전체공간이고, 전체공간으로의 projection은 입력벡터 자신이다. 
  * 즉, 개별 projection의 벡터합이 입력벡터 자신이 된다. 
  * **이 꼴을 이용하면, 벡터나 함수들을 수직 성분들로 분해할 수 있다.** e.g. Fourier series 

#### Projection matrix의 두가지 특징을 확인해보자. 

1. $$P=P^\top$$: $$(QQ^\top)^\top=QQ^\top$$\(symmetric\) 
2. $$P=P^2$$ : $$(QQ^\top)(QQ^\top)=Q(\underbrace{Q^\top Q}_I)Q^\top=QQ^\top$$

### 간단한 normal equation

* Normal equation: $$A^\top A\hat{\bm{x}}=A^\top\bm{b}$$
* $$A=Q$$이면: $$Q^\top Q\hat{\bm{x}}=Q^\top\bm{b}$$
  * $$\hat{\bm{x}}=Q^\top\bm{b}$$ 
  * $$\hat{\bm{x}}_i=q_i^\top\bm{b}$$ 
* **\[Fig. 1\]**에서 $$Q$$의 basis로 구성된 좌표계를 기준으로 입력벡터의 좌표를 기술한 것과 같다. 
* \*\*\*\*$$Q^\top$$**와의 곱은 각각의 orthonormal basis와의 dot product, 즉,** $$\mathcal{C}(Q)$$**로의 projection을 의미한다.**  
* 출력 벡터는 projection의 크기가 되며, $$Q$$**행렬이** $$\bm{b}$$**의 projection을 만들어내는 선형조합**을 의미한다.  

{% hint style="info" %}
**Normal equation when** $$A=Q$$\*\*\*\*

* $$\hat{\bm{x}}=Q^\top\bm{b}$$ 
{% endhint %}

### 실제 상황? 

* 실제 상황에서 주어지는 행렬이 $$Q$$의 형태일 경우는 거의 없다.
* 그러므로, 아래 배울 $$QR$$decomposition을 통해 $$Q$$를 직접 만들어주는 방법을 사용한다. 

## Gram-Schmidt Process 

* 보통 우리가 만나는 행렬은 orthogonal basis를 갖지 않는다.
* 다행히 선형독립 column들을 orthonormal로 만들 수  있는 방법이 있다. 
  * 그람-슈미트 과정 또는 단위직교화! 

![\[Fig. 3\] &#xD30C;&#xC120;&#xC73C;&#xB85C; &#xB41C; &#xC0AC;&#xB2E4;&#xB9AC;&#xAF34;\(orange\)&#xC740; a, b&#xAC00; &#xACF5;&#xC720;&#xD558;&#xB294; &#xD3C9;&#xBA74;&#xC744; &#xC758;&#xBBF8;&#xD55C;&#xB2E4;. \(c&#xB294; &#xC624;&#xC9C1; &#xD55C;&#xC810;&#xC5D0;&#xC11C; &#xAD50;&#xCC28;\)](../.gitbook/assets/image%20%28170%29.png)

#### 선형독립인 $$ \bm{a}, \bm{b}, \bm{c}$$를 먼저 orthogonal vector들로 $$\bm{A}, \bm{B}, \bm{C}$$로 바꿔보자. 

\(1\)$$\bm{a}\rightarrow\bm{A}$$ 

* 처음은 기준벡터로 고정해준다. 
* **결과:** $$\bm{A}=\bm{a}$$

\(2\) $$\bm{b}\rightarrow\bm{B}$$ 

* $$\bm{b}$$에 존재하는 $$\bm{A}$$성분\($$\bm{b}$$의 $$\bm{A}$$에 대한 projection; $$P_\bm{A}\bm{b}$$\)을 제거해준다.
* $$\bm{B}=\bm{b}-P_\bm{A}\bm{b}=\bm{b}-P_\bm{A}\bm{b}=\bm{b}-\dfrac{\bm{A}\bm{A}^\top}{\bm{A}^\top\bm{A}}\bm{b}=\bm{b}-\bm{A}\dfrac{\bm{A}^\top\bm{b}}{\bm{A}^\top\bm{A}}$$
* **결과:** $$\bm{B}=\bm{b}-{\color{blue}\dfrac{\bm{A}^\top\bm{b}}{\bm{A}^\top\bm{A}}}\bm{A}$$ \(blue: 숫자\) 

\(2\) $$\bm{c}\rightarrow\bm{C}$$ 

* $$\bm{c}$$에 존재하는 $$\bm{A}$$와 $$\bm{B}$$성분\($$P_\bm{A}\bm{c}$$와 $$P_\bm{B}\bm{c}$$\)을 제거해준다.
* $$\bm{C}=\bm{c}-P_\bm{A}\bm{c}-P_\bm{A}\bm{c}=\bm{c}-\dfrac{\bm{A}^\top\bm{c}}{\bm{A}^\top\bm{A}}\bm{A}-\dfrac{\bm{B}^\top\bm{c}}{\bm{B}^\top\bm{B}}\bm{B}$$
* **결과:** $$\bm{C}=\bm{c}-{\color{blue}\dfrac{\bm{A}^\top\bm{c}}{\bm{A}^\top\bm{A}}}\bm{A}-{\color{blue}\dfrac{\bm{B}^\top\bm{c}}{\bm{B}^\top\bm{B}}}\bm{B}$$ \(blue: 숫자\) 

#### Orthogonal vector$$\bm{A}, \bm{B}, \bm{C}$$를 orthonormal vector $$\bm{q}_1, \bm{q}_2, \bm{q}_3$$으로 만들어주자. 

* 각각의 길이로 나누어주면 unit vector들이 된다.
* **결과:** $$\bm{q}_1=\dfrac{\bm{A}}{\Vert\bm{A}\Vert}, \ \bm{q}_2=\dfrac{\bm{B}}{\Vert\bm{B}\Vert},  \ \bm{q}_3=\dfrac{\bm{C}}{\Vert\bm{C}\Vert}$$

