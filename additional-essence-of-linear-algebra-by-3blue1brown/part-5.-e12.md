# Cramer's rule\(E12\)

## E12. Cramer's rule, explained geometrically

### 도입

* 이전 에피소드에서는 linear system을 푸는 실제 계산 방법에 대해서는 논하지 않았다.
* 그러나 계산을 실제로 해보는 것은 뭐가 어떻게 돌아가는지에 대한 이해를 심화시켜준다.
* 이번 에피소드에서는 **실제 솔루션을 구하는 방식 중 하나인 크래머 공식**을 살펴본다. 
  * 크래머 공식이 가장 좋은 방법이 아님을 유의. Gaussian elimination이 항상 더 빠름.  
  * 서로 다른 개념들이 어떻게 서로 관계하는지 체험해보고 이해를 심화하는데 의의를 두자. 

### **백그라운드**

* determinant
* dot products
* linear system of equations

### 방법1: Dot product 이용하기 \(feat. Rotation Matrix\)

* 먼저 크래머 공식과 직접적인 관련은 없지만, **해를 구할 수 있는 다른 방법을 먼저 생각해보자.**
  * dot product\(projection\)를 이용하는 방법이다. 
  * 이 방법은 일반적이지 않으며, 아주 특수한\(orthogonal\) 선형변환에서만 적용가능할 것이다.  
  * 그러나 크래머 공식을 이해하는 과정에 도움이 되므로 일단 따라가 보자. 

#### **다음 선형방정식계를 살펴보자. \[Fig. 1\]**

* \[Fig. 1\]의 파란색 grid로 표현되는 좌표계는 다음 선형 변환 후의 상황을 나타낸 것이다. 
  * $$\begin{bmatrix} 3 & 2 \\ -1 & 2 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} -4 \\ 2 \end{bmatrix}$$ 
* 행렬의 column\(초록, 노랑\)들은 선형 변환 후에 standard basis vector들의 이동 위치를 나타낸다. 
* 선형계의 솔루션은 $$\begin{bmatrix} -4 \\ -2 \end{bmatrix}$$를 만들어내는 column들의 linear combination이다. 

#### 각 행렬과 벡터들이 어떤 좌표계를 기준으로 기술되고 있을까?

* $$\begin{bmatrix} x \\ y \end{bmatrix}$$는 column space의 선형변환 후 좌표계\(진한 파란색 그리드\)의 좌표를 의미한다. 
* 행렬의 column들과 $$\begin{bmatrix} -4 \\ -2 \end{bmatrix}$$은  선형변환 전 좌표계\(연한 회색 그리드\) 기준으로 표현되고 있다. 

![\[Fig. 1\] &#xB2E4;&#xC74C; &#xC120;&#xD615;&#xBC29;&#xC815;&#xC2DD;&#xACC4;&#xB97C; &#xD480;&#xC5B4;&#xBCF4;&#xC790;](../.gitbook/assets/image%20%2859%29.png)

#### **Dot product를 이용해서 입력벡터** $$\begin{bmatrix} x \\ y \end{bmatrix}$$**의 좌표\(i.e. 솔루션, 해\)를 구할 수 있을까?**  

* 테이프를 거꾸로 돌려서 어떤 벡터가 변환 후에 $$\begin{bmatrix} -4 \\ -2 \end{bmatrix}$$ 위치로 옮겨졌는지 확인해보자. 
  * standard basis vector으로 복구시키면, **분홍색 벡터가 솔루션**임을 알 수 있다. **\[Fig. 2\]**
  * 이녀석을 선형변환 시킨 것이 노란 벡터가 되었던 것이다.  

![\[Fig. 2\] dot product&#xB97C; &#xC774;&#xC6A9;&#xD558;&#xC5EC; &#xC785;&#xB825; &#xBCA1;&#xD130;&#xC758; &#xC88C;&#xD45C; &#xAD6C;&#xD558;&#xAE30;](../.gitbook/assets/image%20%2889%29.png)

#### unit vector에 dot product를 하면 해당 벡터의 projection을 바로 구할 수 있다.

* standard basis 벡터와 입력 벡터 사이의 내적을 취한다. 
* 기대하는 결과는 구좌표계를 기준으로 한 입력벡터의 좌표이다. 
* 분홍색 벡터의 $$x$$축으로의 projection: $$\begin{bmatrix} x \\ y \end{bmatrix}\cdot \begin{bmatrix} 1 \\ 0 \end{bmatrix}=x$$
* 분홍색 벡터의 $$y$$축으로의 projection: $$\begin{bmatrix} x \\ y \end{bmatrix}\cdot \begin{bmatrix} 0 \\ 1 \end{bmatrix}=y$$
* 미지수로 미지수를 구하는게 부질없어 보이긴 하지만 설명을 위한 과정이다. 

#### **그렇다면, 선형 변환\(**$$T$$**\) 후에 똑같이 dot product를 이용해서 해를 구해보면 어떨까? \[Fig. 3\]**

* 이번에는 변환된 basis벡터와 출력벡터 사이의 내적을 취한다. 
* 기대하는 결과는 **신좌표계를 기준**으로 한 출력 벡터의 좌표\(신좌표\)이다.  
* $$T\left(\begin{bmatrix} x \\ y \end{bmatrix}\right)\cdot T\left( \begin{bmatrix} 1 \\ 0 \end{bmatrix} \right)=\begin{bmatrix} -4 \\ -2 \end{bmatrix} \cdot \begin{bmatrix} 3 \\ -1 \end{bmatrix} \stackrel{?}{=} x$$
* $$T\left(\begin{bmatrix} x \\ y \end{bmatrix}\right)\cdot T\left( \begin{bmatrix} 0 \\ 1 \end{bmatrix} \right)=\begin{bmatrix} -4 \\ -2 \end{bmatrix} \cdot \begin{bmatrix} 2 \\ 2 \end{bmatrix} \stackrel{?}{=} y$$ 

#### 그러나 선형 변환 후에는 좌표계가 왜곡되어 더이상 등식이 성립하지 않는다!  \(두 가지 이유\) 

* \(1\) basis vector들이 더이상 서로 수직이 아니다. 
  * basis vector들로의 orthogonal projection이 파란색 grid line과 평행하지 않다.   
* \(2\) basis vector들이 더이상 길이가 1이 아니다. 
  * 정사영 길이를 신좌표계 기준으로 알아야 신좌표계 나온다.
  * 그러나 실제 계산되는 값은 구좌표계 기준이 된다.  
* 사실 이 방법이 먹혔다면 굳이 힘들게 elimination을 하거나 역행렬을 구하지도 않았을 것이다. 

![\[Fig. 3\] &#xC120;&#xD615; &#xBCC0;&#xD658; &#xD6C4;&#xC5D0;&#xB3C4; dot product&#xB85C; &#xCD9C;&#xB825; &#xBCA1;&#xD130;&#xC758; &#xC88C;&#xD45C;&#xB97C; &#xAD6C;&#xD560; &#xC218; &#xC788;&#xC744;&#xAE4C;? \(No.\)](../.gitbook/assets/image%20%2855%29.png)

#### 물론 이러한 방법이 적용가능한 선형변환도 존재한다: **직교행렬**\(**orthogonal** matrix\)! 

* 즉, 모든 $$\vec{v}$$와 $$\vec{w}$$에 대해서 $$ T(\vec{v}) \cdot T(\vec{w}) = \vec{v} \cdot \vec{w} $$인 $$T$$를 orthogonal하다고 한다. 
* 이 행렬의 모든 column은 \(1\) 서로 직교하는 \(2\)  크기가 1인 단위 벡터들이다. \(orthogonal unit vectors\)     
  * 이 특성 때문에 basis vector들이 가지고 있던 위의 두가지 문제가 해소된다. 
* 이러한 벡터\(orthogonal unit vectors\)를 하나의 용어로  _**orthonormal**_ vectors라고 부른다. 
  * 때문에 orthonormal matrix이름이 더 자연스럽게 느껴지지만, 정식용어는 아니다. 
  * \(상당히 헷갈리게 하는 terminology로써, 강의 영상에서도 실수가 나온다.\)  

#### **직교행렬의 예시: Rotation matrix**

* 아래 애니메이션과 같이 왜곡이나 확대/축소가 없는 **rotation** 행렬! **\[Fig. 4\]**
* **\[Fig. 5\]**는 dot product를 이용하여 실제 솔루션을 바로 구하는 예시이다.  ****
  * \(correction\) 위에서 이야기 했듯이 orthogonal을 계속 orthonormal로 잘못 표기한다. 
* 영상에는 나오지 않지만, orthogonal matrix의 역행렬은 transpose이다. 
  * 즉, 양변에 역행렬을 곱하면: $$\begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} \text{cos} (30^\circ) & -\text{sin} (30^\circ) \\\text{sin} (30^\circ) & \text{cos} (30^\circ) \end{bmatrix}^\top \begin{bmatrix} 1 \\ 2 \end{bmatrix}$$  
  * dot product를 이용해 좌표를 구하는 계산\(\[Fig. 5\] 우상단\)과 동일하다. 
* 어떤 경우든 orthogonal matrix의 경우 **테이프를 거꾸로 돌리는 비용이 저렴**하다! 

![\[Fig. 4\] Rotation matrix in 2D &amp; 3D](../.gitbook/assets/orthogonal_trans.gif)

![\[Fig. 5\] orthogonal matrix&#xB294; dot product&#xB97C; &#xC774;&#xC6A9;&#xD558;&#xC5EC; &#xD574;&#xB97C; &#xC27D;&#xAC8C; &#xAD6C;&#xD560; &#xC218; &#xC788;&#xB2E4;.](../.gitbook/assets/image%20%281%29.png)

#### 어쨌든 전혀 범용적이지 않은 **이 방법에 대해 굳이 이야기한 이유**는? 

* 선형방정식계의 해를 구하는 방법에 대한 기하학적 해석에 대한 힌트를 얻기 위해서!   
* 그러나 이 방법 경우, 특수한 경우를 제외하고 기하학적 특징이 변환 후에 바뀌어버렸다.  
* 선형 변환 후에도 바뀌지 않고 유지되는 다른 기하학적 특징을 이용해 해를 구할 수 있을까? 

### 방법2: Determinant를 이용하기 \(Cramer's Rule\)

#### **보다 더 범용적인 입력 벡터의 기하학적 해석을 생각해보자.** 

* **\[Fig. 6\]**와 같이 입력 벡터의 좌표를 기하학적으로 해석할 수 있다. 

![\[Fig. 6\] &#xC784;&#xC758;&#xC758; &#xBCA1;&#xD130;\(pink\)&#xC758; &#xC88C;&#xD45C;&#xB97C; &#xAE30;&#xD558;&#xD559;&#xC801;&#xC73C;&#xB85C; &#xD45C;&#xD604;&#xD558;&#xB294; &#xB610;&#xB2E4;&#xB978; &#xBC29;&#xBC95; \(for Cramer&apos;s rule\)](../.gitbook/assets/image%20%28142%29.png)

#### 쉽게 말해 \(좌표\)를 \(면적 or 부피\)로 전환해서 해석하는 방법! 

* **2차원**\(상단 그림\)
  * $$x$$**좌표** : $$\hat{\bm{j}}$$과 입력벡터로 만들어진 parallelogram의 넓이 \($$1\times x=x$$\)
    * $$\text{det}\left( \begin{bmatrix} x & 0 \\ y & 1 \end{bmatrix}\right)=x$$
  * $$y$$**좌표** : $$\hat{\bm{i}}$$과 입력벡터로 만들어진 parallelogram의 넓이 \($$1\times y=y$$\)
    * $$\text{det}\left( \begin{bmatrix} 1 & x \\ 0 & y \end{bmatrix}\right)=y$$ 
* **3차원**\(하단 그림\)
  * $$z$$**좌표** : $$\hat{\bm{i}}, \ \hat{\bm{j}}$$와 입력벡터로 만들어진 parallelepiped의 부피
    * $$\text{det}\left( \begin{bmatrix} 1 & 0 & x \\ 0 & 1 &  y \\ 0 & 0 & z \end{bmatrix}\right)=z$$ 
* \(주의\) 해당 좌표가 음수일 경우 부피에 minus sign이 붙는다. 
  * signed volume이라는 것을 염두해두라는 것 뿐이다.
  * 실제 숫자를 넣고 계산하면 알아서 반영된다. 
* 이렇게 각 좌표값\(벡터의 성분\)을 의미하는 면적/부피를 **성분면적\(Component area\)**이라고 하겠다. 
  * 공식적인 용어가 아니라 설명을 위해 **개인적으로 도입**하는 단어이다. 

#### 성분면적\(with 표준기저벡터\)을 더 일반적으로 표현해보자. 

* 관심벡터의 각 성분은 다음을 만족하는 column을 가지는 행렬의 determinant가 된다: 
  * **해당 성분에 대응되는 column:** 관심벡터  
  * **그 외의 column들:** 해당되는 standard basis vectors  

#### **이렇게 면적/부피를 이용하여 좌표를 표현하는 것이 왜 범용적일까?** 

* 행렬 $$A$$에 의한 선형 변환 후, 벡터공간 안의 모든 면적/부피도 역시 변화한다. 
* 단,$$\text{det}(A)$$에 의해 **일정한 실수배만큼 scale**된다!
  *  **\[Fig. 7\]**에서 면적이 _늘어나는_ 방향으로의 변환. \(선형 변환\) 

#### 다시말해, 면적/부피가 변화하기는 하지만, 그 변화율을 계산할 수 있다는 것이다. 

* 선형 변환 후, 변화한 면적을 $$\text{det}(A)$$로 다시 나누어주면 변환 전의 성분면적을 역계산할 수 있음.  
  *  **\[Fig. 7\]**에서 면적이 _줄어드는_ 방향으로의 변환. \(역 변환\) 
* 선형변환 전의 성분면적은 곧 좌표였다는 사실을 기억하자.  
  * 선형 변환 전의 성분면적을 복원한다 = 좌표\(벡터성분\)를 복원한다 = 시스템의 해를 구한다 
* 역행렬과 유사한 역할을 determinant를 이용하여 면적/부피의 레벨에서 수행하는 것. **\[Fig. 8\]**
  * 이러한 방법으로 해를 구하는 것을 **Cramer's rule**이라고 한다! 

![\[Fig. 7\] &#xC120;&#xD615; &#xBCC0;&#xD658;&#xACFC; &#xADF8; &#xC5ED; &#xBCC0;&#xD658;&#xC5D0; &#xB530;&#xB978; y&#xC88C;&#xD45C;&#xB97C; &#xC758;&#xBBF8;&#xD558;&#xB294; &#xBA74;&#xC801;&#xC758; scaling up/down](../.gitbook/assets/cramers_rule2.gif)

![\[Fig. 8\]  Cramer&apos;s Rule: &#xC5ED;&#xD589;&#xB82C;&#xC758; &#xACF1;\(&#xBE68;&#xAC04; &#xD30C;&#xC120;\)&#xC744; &#xBA74;&#xC801;&#xC758; &#xC5ED;&#xBCC0;&#xD658; &#xACFC;&#xC815;\(&#xBE68;&#xAC04; &#xC2E4;&#xC120;\)&#xC73C;&#xB85C; &#xB300;&#xCCB4;&#xD558;&#xB294; &#xBC29;&#xBC95;](../.gitbook/assets/image%20%2854%29.png)

#### 선형변환 이후의 성분면적은 어떻게 구할까? 

* 선형변환 전의 표준기저벡터 기준 성분면적을 구할때와 같은 원리를 그대로 적용. 
* 다음을 만족하는 column을 가지는 행렬의 determinant를 구하면 된다: 
  * **해당 성분에 대응되는 column:** \(선형변환 후의\) 관심벡터  
  * **그 외의 column들:** 해당되는 \(선형변환 후의\) basis vectors  
* 다시 말해서, **벡터의** $$i$$**번째 성분면적**은 **행렬의** $$i$$**번째 열을 해당 벡터로 교체한 행렬식**과 같다. 

#### **예를 들어보자. \(본격 크래머 공식\)**  

* 다음과 같은 선형계\($$A\bm{x}=\bm{b}$$\)가 있다: $$\begin{bmatrix} 2 & -1 \\ 0 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} 4 \\ 2 \end{bmatrix}$$ 
* 선형 변환 전에 위에서 배운 방법대로 좌표 $$x, \ y$$에 대응되는 면적을 상정한다. 
* 선형 변환 후에 변화된\(scaled\) 면적도 조금 전에 알아봤듯이, 똑같은 방법으로 구할 수 있다! 
  * 좌표 $$x$$를 나타내던 면적의 선형 변환 후의 값: $$\text{det} \left( \begin{bmatrix} 4 & -1 \\ 2 & 1 \end{bmatrix} \right)$$ 

  * 좌표 $$y$$를 나타내던 면적의 선형 변환 후의 값: $$\text{det} \left( \begin{bmatrix} 2 & 4 \\ 0 & 2 \end{bmatrix} \right)$$ 
  * 변환 후의 벡터\($$\bm{b}$$\)는 우리가 알고 있으므로, 이번에는 미지수가 아닌 실제 숫자를 구할 수 있다.  
* 이제 scaled된 값만큼 다시 나누어서 선형 변환 전의 부피\(=좌표\)를 회복시켜보자.
  * 선형 변환 후에 생기는 면적의 scaling factor는: $$\text{det}(A) = \text{det} \left( \begin{bmatrix} 2 & -1 \\ 0 & 1 \end{bmatrix} \right)$$
  * $$x=\dfrac{\text{Component area after transformation}}{\text{Scaling factor, det}(A)}=\dfrac{\text{det} \left( \begin{bmatrix} 4 & -1 \\ 2 & 1 \end{bmatrix} \right)}{\text{det} \left( \begin{bmatrix} 2 & -1 \\ 0 & 1 \end{bmatrix} \right)}$$
  * $$y=\dfrac{\text{Component area after transformation}}{\text{Scaling factor, det}(A)}=\dfrac{\text{det} \left( \begin{bmatrix} 2 & 4 \\ 0 & 2 \end{bmatrix} \right)}{\text{det} \left( \begin{bmatrix} 2 & -1 \\ 0 & 1 \end{bmatrix} \right)}$$ 
  * 해를 구했다! 

