# Eigen-things\(E14\)

## E14. Eigenvectors and eigenvalues

### Introduction: 고유벡터\(Eigenvectors\)와 고유값\(Eigenvalues\)

* 교과서에서 다음과 같은 식으로 고유값을 구한다고 배운다:
  * $$ \text{det} \left( \begin{bmatrix} a-\lambda & b \\ c & d- \lambda \end{bmatrix} \right) = 0 $$
* 이 에피소드에서는 다음 질문들에 대답하기 위한 과정이다:
  * 그런데 이 짓을 왜 하는 걸까? 
  * 이 계산이 진짜 의미하는게 뭘까?
* 고유벡터와 고유값은 사실 여타 교재들에서 잘 설명되고 있는 토픽 중 하나이다.
* 다음 기하학적 이해에 대한 선행지식들이 탄탄하다면, 이들을 연결하는 자체는 어렵지 않다. 
  * Linear transformation
  * Determinants
  * Linear systems 
  * Change of basis

### 고유벡터와 고유값의 기하학적 이해 

* 행렬 $$\begin{bmatrix} 3 & 1 \\ 0 & 2 \end{bmatrix}$$의 고유값과 고유벡터의 기하학적 의미를 살펴보자. 

#### 아래 애니메이션\[Fig. 1\]으로 설명 끝이다.

* 선형변환을 했을때, 대부분의 벡터\(purple\)는 변환 전에 span하던 line에서 벗어나게\(knocked off\) 된다. 
* 그러나, 선형변환 후에도 같은 line 위에서 scale만 변하는 '독특한' 벡터들\(green & yellow\)이 존재한다.
  * 이 특별한 벡터들을 **고유벡터**라고 부르고, 변화하는 scaling factor를 **고유값**이라고 한다. 
    * 반대 방향으로 scaled될 경우는 고유값이 음수. 

![\[Fig. 1\]](../../.gitbook/assets/eigenthings.gif)

### 고유벡터의 중요성을 보여주는 간단한 예시

#### 3차원 회전행렬의 경우 

* **회전축**이 곧 고유벡터이고, 고유값은 **1**\(no scaling\)이다. **\[Fig. 2\]**
* 해당 선형변환을 \(3x3\)행렬로 나타내는 것은 상대적으로 어려우며, 직관적이지 못한 표현방법이다. 
* **고유벡터를 기준으로 몇 도\(degree\) 회전하였는지 나타내는 것**이 훨씬 이해하기 쉽고 간편하다. 

![\[Fig. 2\]](../../.gitbook/assets/3d_rotation.gif)

#### 좀  일반화해보자. 

* 행렬의 basis vector들이 어떻게 움직이는지를 직접 읽어보면 그 선형변환에 대해 이해할 수 있다. 
* 그러나 이 방법은 이해의 범위를 '**우리의 기준 좌표계**'에 **지나치게 종속**되게 만든다. 
* 예를 들어, 위의 예시에서는, basis vector의 이동보다는 '**회전축**'이 **훨씬 더 직관적인 설명력**을 가진다. 
* 즉, **때로는 선형변환을 고유벡터와 고유값으로 설명하는 것이 더 좋은 방법**일 수 있다! 

### 이제 고유벡터와 교유값의 계산 방법에 대해 알아보자

* 디테일을 다루지는 않겠지만 개념적 이해를 돕는 부분에 한정하여 알아보자. 
* 아주 잘 알려진 교유벡터 & 고유값을 설명하는 식은 다음과 같다: 
  * $$A\vec{v}=\lambda\vec{v}$$ \(행렬 $$A$$의 **고유벡터**는 $$\vec{v}$$, **고유값**은 $$\lambda$$\)
* 즉, 선형 변환 후에도 변환 전 벡터에서 scale만 달라져야 한다\(혹은 scale만 달라진 놈과 같다\).
* 고유벡터와 고유값을 구하는 일은, 위 식을 만족하는 $$\vec{v}$$와 $$\lambda$$를 구하는 것과 같다. 

#### 본격적으로 계산해보자.  

* 위 식을 그대로 가져오자. 
  * $$A\vec{v}=\lambda\vec{v}$$ 
* 좌우변에서 $$\vec{v}$$에 곱해진 인자의 종류가 다르다. \(좌: 행렬/우: 스칼라\)
* 양변을 행렬로 통일하기 위해, $$\bm{v}$$를 $$\lambda$$로 scaling하는 것과 같은 효과를 가지고 오는 행렬을 찾아보자. 
* 그 것은 표준 기저벡터들을 모두 $$\lambda$$만큼 scaling\(모든 방향으로 똑같이 확장\)한 것이 된다: $$\lambda I$$
  * $$A\vec{v}=(\lambda I)\vec{v}$$
* 우변을 양변에 빼주고, 분배법칙으로 묶어주자.  
  * $$A\vec{v}-(\lambda I)\vec{v}=\vec{0}$$ 
  * $$(A-\lambda I)\vec{v}=\vec{0}$$ $$\cdots $$ \(1\)
    * $$A-\lambda I$$는 대각원소들에서 $$\lambda$$를 뺀 형태: $$e.g. \scriptsize \begin{bmatrix} a-\lambda & b \\ c & d- \lambda \end{bmatrix}$$ 
* 식 \(1\)을 만족하는$$\vec{0}$$이 아닌 $$\vec{v}$$\(nullspace\)가 존재하려면, 어떤 선형변환이어야 하는가? 
* 선형변환$$(A-\lambda I)$$이 전체 공간을 더 낮은 차원으로 짜부라뜨려\(squish\)야한다. 
* 그래야 줄어드는 차원\(nullspace\)만큼이 $$\vec{0}$$으로 빨려들어갈 수 있다. 
* 이는 determinant로 측정되는 면적/부피의 scaling factor가 0이어야 함을 의미한다.
  * $$\text{det} ( A- \lambda I) =0$$ $$\cdots$$ \(2\)
  * 잘 알려진 공식이 나왔다.  
* 이제 식 \(2\)를 통해 먼저 $$\lambda$$들을 찾은 후에, 이를 식 \(1\)에 대입하여 $$\vec{v}$$들을 구할 것이다.

#### 최종식을 만족하는 $$\lambda$$\(고유값\)를 찾아보자. 

* 위에서 예로 들었던 행렬을 식 \(1\)의 형태로 써보면:
  * $$ \text{det} \left( \begin{bmatrix} 3-\lambda & 1 \\ 0 & 2- \lambda \end{bmatrix} \right) = (3- \lambda )(2-\lambda )-1\cdot 0 $$ 
* 2차 방정식의 해를 구하면: 
  * $$\lambda=2 \ \text{or} \ \lambda=3$$
* 다음 애니메이션은 determinant가 0이 되는 $$\lambda$$값을 기하학적으로 설명하고 있다.  

![\[Fig. 3\]](../../.gitbook/assets/finding_lambda2.gif)

#### $$\lambda=2$$일때의 $$\vec{v}$$\(고유벡터\)를 찾아보자. 

* 식 \(2\)에 $$\lambda=2$$를 대입해보자\($$\lambda=3$$ 인 경우는 생략\) :
  * $$\begin{bmatrix} 3-2 & 1 \\ 0 & 2-2 \end{bmatrix}\begin{bmatrix} v_1 \\ v_2 \end{bmatrix}=\begin{bmatrix} 1 & 1 \\ 0 & 0 \end{bmatrix}\begin{bmatrix} v_1 \\ v_2 \end{bmatrix}=\begin{bmatrix} 0 \\ 0 \end{bmatrix}$$
* 이 선형방정식계의 해\(=nullspace\), 즉 $$\vec{v}$$를 구해보면:
  *  $$\begin{bmatrix} v_1 \\ v_2\end{bmatrix}=c\begin{bmatrix} -1 \\ 1 \end{bmatrix}$$

#### $$\vec{v}$$는 행렬 $$ \begin{bmatrix} 1 & 1 \\ 0 & 0 \end{bmatrix}$$ 의 nullspace임과 동시에 $$ \begin{bmatrix} 3& 1 \\ 0 & 2 \end{bmatrix}$$의 고유벡터이다. 

* 즉, subspace $$\bm{v}$$\(노란색 벡터의 집합\)는 두 행렬의 관점에서 다르게 해석된다. **\[Fig. 4\]**
  1. **원래\(unaltered\) 행렬의 관점** : 고유벡터들\(고유값이 2일때\)!
  2. **대각원소에서 고유값 2를 뺀\(altered\) 행렬의 관점** : nullspace!

![\[Fig. 4\] \(&#xC804;\) &#xACE0;&#xC720;&#xAC12;2&#xB97C; &#xB300;&#xAC01;&#xC131;&#xBD84;&#xC5D0; &#xBE7C;&#xC900; &#xD589;&#xB82C;&#xC758; nullspace \(&#xD6C4;\) &#xC6D0;&#xB798; &#xD589;&#xB82C;&#xC758; &#xACE0;&#xC720;&#xAC12; 2&#xC5D0; &#xB300;&#xD55C; &#xACE0;&#xC720;&#xBCA1;&#xD130;](../../.gitbook/assets/altered_n_unaltered2.gif)

### 고유벡터와 고유값에 관한 다른 이야기들

#### 고유벡터는 존재하지 않을 수도 있다\(e.g. 회전행렬\). 

* 이 경우에는 고유값이 허수가 나온다. 
* \(참고\) 회전과 허수 고유값간의 모종의 관계가 존재.

#### 고유벡터가 전체 공간을 span하지 않을 수도 있다. 

* 예를 들면, 2x2행렬의 행렬식이 2차 함수로 표현될때, 해당 함수가 중근을 갖는 경우다.  
* 이 경우, 고유값은 하나만 존재하고, 고유벡터들은 하나의 line 위에 있다. 
* 즉, 전체 공간\(2d\)을 span하지 못한다. 

#### 고유값이 하나 존재하더라도, 고유벡터들이 span하는 line은 여러 개일 수 있다. 

* 예를 들어, $$\begin{bmatrix} 2 & 0 \\ 0 & 2 \end{bmatrix}$$의 경우, 고유값은 2 하나지만, 모든 벡터가 고유벡터이다. 

### 마지막 고지: 고유기저\(Eigenbasis\) 

* 절대다수의 vector는 고유벡터가 아니다. 
* 그런데 만약, **행렬의 basis vector가 \(운좋게\) 고유벡터인 경우라면** 어떨까? 
* 이런 기저를 **고유기저\(eigenbasis\)**라고 한다. 

#### 그 좋은 예시가 대각행렬이다. 

* 대각행렬의 **모든 basis vector**는 고유벡터이고, **해당 대각 원소**가 고유값이다. 
* **대각행렬의 장점**: n번 행렬곱했을때 대각 원소만 n제곱 
  * $$\underbrace{\begin{bmatrix} 3&0\\0&2\end{bmatrix}\begin{bmatrix} 3&0\\0&2\end{bmatrix}\begin{bmatrix} 3&0\\0&2\end{bmatrix}\cdots \begin{bmatrix} 3&0\\0&2\end{bmatrix}}_{100 \ \text{times}} = \begin{bmatrix} 3^{\tiny 100}&0\\0&2^{\tiny100}\end{bmatrix}$$
* 그러나 이러한 편의를 누리려면 엄청나게 운이 좋아야 한다. 
* 대부분 우리가 처한 상황은 다음과 같다: 
  * $$\underbrace{\begin{bmatrix} 3&1\\0&2\end{bmatrix}\begin{bmatrix} 3&1\\0&2\end{bmatrix}\begin{bmatrix} 3&1\\0&2\end{bmatrix}\cdots \begin{bmatrix} 3&1\\0&2\end{bmatrix}}_{100 \ \text{times}} =  \ ?!$$ 

#### 다행히도, 운을 직접 만들어낼 수 있는 방법이 있다. 

* 이전 에피소드에서 배운 **change of basis**를 이용하여, **직접 eigenbasis로 만드는** 것이다. 
  * $$\begin{bmatrix} \color{ForestGreen} 1& \color{Goldenrod}-1 \\ \color{ForestGreen}0 & \color{Goldenrod} 1 \end{bmatrix}^{-1} \begin{bmatrix} 3 & 1 \\ 0 & 2 \end{bmatrix} \begin{bmatrix} \color{ForestGreen} 1& \color{Goldenrod}-1 \\ \color{ForestGreen}0 & \color{Goldenrod} 1 \end{bmatrix}= \begin{bmatrix} 3 & 0 \\ 0 & 2 \end{bmatrix}$$
  * $$\begin{bmatrix} \color{ForestGreen} 1 \\ \color{ForestGreen}0   \end{bmatrix} , \ \begin{bmatrix}  \color{Goldenrod}-1 \\  \color{Goldenrod} 1 \end{bmatrix}$$ : Eigenvectors, $$\begin{bmatrix} \color{ForestGreen} 1& \color{Goldenrod}-1 \\ \color{ForestGreen}0 & \color{Goldenrod} 1 \end{bmatrix}$$ : Change of basis matrix 
* 만약 $$\begin{bmatrix} 3&1\\0&2\end{bmatrix}^{100}$$ \(행렬곱 100번\)을 계산해야 한다고 하면? 
  * $$\begin{align} \begin{bmatrix} 3&1\\0&2\end{bmatrix}^{100}&=\begin{bmatrix} \color{ForestGreen} 1& \color{Goldenrod} {-1} \\ \color{ForestGreen}0 & \color{Goldenrod} 1 \end{bmatrix}\begin{bmatrix} 3&0\\0&2\end{bmatrix}^{100} \begin{bmatrix} \color{ForestGreen} 1& \color{Goldenrod}{-1} \\ \color{ForestGreen}0 & \color{Goldenrod} 1 \end{bmatrix}^{-1} \\ &=\begin{bmatrix} \color{ForestGreen} 1& \color{Goldenrod}{-1} \\ \color{ForestGreen}0 & \color{Goldenrod} 1 \end{bmatrix}\begin{bmatrix} 3^{ 100}&0\\0&2^{100}\end{bmatrix} \begin{bmatrix} \color{ForestGreen} 1& \color{Goldenrod}{-1} \\  \color{ForestGreen}0 & \color{Goldenrod} 1 \end{bmatrix}^{-1} \end{align}$$ 
  * 즉, eigenbasis로 변환 후, 그 시스템에서 100번을 곱하고, 다시 standard basis로 돌아오면 되는 것.

#### Change of basis의 방향이 헷갈릴땐? 

* 실제로 적용하려고 보면, 전 에피스도의 변환과 번역의 개념 사이에서 방향성이 혼동될 수 있다. 
* Counter-intuitive한 개념을 굳이 체감하려 하지말고, 절차적 증거를 확보했다면 받아들여 보자. 
* 우리가 기하학적 변환에서 생각하는 방향과 반대라고 생각해도 좋다. 
* 기본적으로 행렬곱은 왼쪽에서 오른쪽으로 진행된다는 것은 당연히 잊지 말아야 한다. 
* eigenbasis sytem으로 바꾸고 싶을땐 **'오히려 반대로**'  역행렬을 곱해줘야 한다. 
* 기본적으로 모든 행렬은 그 specific basis를 standard basis로 바꾸는\(translate\) 기능을 한다. 
  * **원래 행렬**: specific basis $$\rightarrow$$ standard basis
  * e.g. $$\begin{bmatrix} \color{ForestGreen} 1& \color{Goldenrod} {-1} \\ \color{ForestGreen}0 & \color{Goldenrod} 1 \end{bmatrix}$$ 의 변환 방향은 **eigenbasis**\(specific basis\) $$\rightarrow$$ **standard basis** 
* 현 시점\(standard basis\)에서 specific basis로 보내려면 반대방향이므로 역행렬을 먼저 취해야 한다. 
  * **역행렬**: standard basis $$\rightarrow$$ specific basis 
  * e.g. $$\begin{bmatrix} \color{ForestGreen} 1& \color{Goldenrod} {-1} \\ \color{ForestGreen}0 & \color{Goldenrod} 1 \end{bmatrix}^{-1}$$ 의 변환 방향은  **standard basis** $$\rightarrow$$ **eigenbasis**\(specific basis\) 
  * 여기서는 우리 시점을 기준으로 standard라고 지칭한 것. \(어떤 '기준'의 반대로서 인식하므로\) 
  * 모든 행렬 스스로의 시점에서는 항상 변환 직전을 standard로 기준한다. 
  * e.g. $$\begin{bmatrix} \color{ForestGreen} 1& \color{Goldenrod} {-1} \\ \color{ForestGreen}0 & \color{Goldenrod} 1 \end{bmatrix}^{-1} = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$$ 일 때, change of basis: $$\left( \begin{bmatrix} 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 0 \\ 1 \end{bmatrix} \right) \Rightarrow  \left( \begin{bmatrix} 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 1 \\ 1 \end{bmatrix} \right)$$ 

### 



