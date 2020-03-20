# Change of basis\(E13\)

## \(이 챕터는 수정요망\)

## E13. Change of basis

### Introduction

#### 표준적인\(standard\) 벡터의 좌표를 서술하는 방법

* 좌표는 기준 벡터가 **암묵적으로**\(implicitly\) 전제되어 있다.
* 좌표의 숫자들은 그 벡터들에 대응하는 scalar.
* 2차원벡터를 예로 들어보자.
  * **첫번째 좌표** : vector $$\hat{\bm{i}}$$에 대한 scalar 
  * **두번째 좌표** : vector$$\hat{\bm{j}}$$에 대한 scalar

#### 좌표계, 그리고 기저벡터

* 좌표\(숫자 집합\)와 실제 벡터공간의 객체간 translation이 바로 **좌표계**\(coordinate system\)이다. 
* 좌표계에서 사용되는 scaling의 기준이 되는 벡터를 **기저벡터**\(basis vector\)라고 한다. 
* 우리가 기본적으로 사용하는 좌표계를 **표준좌표계**\(standard coordinate system\)라고 한다. 
* 표준좌표계에서 사용되는 기저벡터\(e.g. $$\hat{\bm{i}}$$, $$\hat{\bm{j}}$$\)를 **표준기저벡터**라고 한다. 

#### 이 에피소드의 관심사: 좌표계간 translation

* 다른 기저벡터\(basis vector\)는 다른 좌표계\(coordinate system\)를 구현한다. 
* 다른 좌표계를 사용한다는 것은 다른 언어\(language\)를 사용한다는 의미이다. 
* **Change of basis를 통해서 좌표계간 translation이 가능할까?**
  * 강의에서의 translation은 '번역'으로 번역하겠다. 
  * **change of language** = language translation
  * **change of basis** = coordinate system translation

### 선형변환은, 사실, translation이였다

#### 다음 선형변환을 살펴보자. 

* $$\underbrace{\begin{bmatrix} 2 & -1 \\ 1 & 1 \end{bmatrix}}_{(1)} \ \ \underbrace{\begin{bmatrix} -1 \\ 2 \end{bmatrix}}_{(2)} = \underbrace{\begin{bmatrix} -4 \\ 1 \end{bmatrix} }_{(3)}$$
* 이 식은 **구좌표계**$$\left( \begin{bmatrix} 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 0 \\ 1 \end{bmatrix} \right)$$에서 **신좌표계** $$\left( \begin{bmatrix} 2 \\ 1 \end{bmatrix}, \begin{bmatrix} -1 \\ 1 \end{bmatrix} \right)$$ 로의 선형변환을 의미한다. 
* 여기서 구\(old\)와 신\(new\)은 EP 3.에서 배운 선형변환의 방향을 기준으로 붙인 수식어이다.  
  * 설명을 위한 기준점일 뿐, 변화의 방향성에 대한 해석적 편향\(e.g. 구$$\rightarrow$$신\)을 의미하지는 않음.  
* **행렬 \(1\)**의 column들$$\left( \begin{bmatrix} 2 \\ 1 \end{bmatrix}, \begin{bmatrix} -1 \\ 1 \end{bmatrix} \right)$$은 신좌표계의 bases이지만, 구좌표계의 언어로 기술되어 있다. 
* **벡터 \(3\)**도 구좌표계의 언어로 기술되어 있다.
* **벡터 \(2\)**가 유일하게 신좌표계의 언어로 기술되어 있다. 
* 우리가 공유하고 있던 기존의 방향성과 대비하여 새로운 관점\(반대 방향\)을 이야기해보자. 
  * **우리가 알고 있던**: 좌표계 **변환** \(구 $$\rightarrow$$신\) 
  * **새롭게 알게 될**: 좌표계 **번역** \(신 $$\rightarrow$$구\)
* Note: 본 에피소드의 설명방식은 임의대로 만들어낸 부분이 있음.  \(실제 강의 내용과 다를 수 있음.\) 

#### 기하학적 변환\(Geometrical transformation\)의 관점 

* 우리가 EP 3.에서 배웠던 선형변환의 기하학적 이해와 같은 내용이다. 
* 이 관점에서는 형렬 \(1\)이 기존의 공간을 기준점으로 전체 공간에 대한 선형적 왜곡을 일으킨다. 
* 행렬 \(1\)이 포함하는 숫자들 자체가 이미 이러한 선형적 왜곡에 대한 정의를 내포하고 있다.   
* 신좌표계로 공간을 변환한 후에 좌표 \(2\)를 따라가면 변환 결과를 얻을 수 있다. 
* 변환의 방향성은 **\(구좌표계** $$\rightarrow$$ **신좌표계\)**로 인식된다. \(bases로 만들어낸 grid의 변화\) 
* $$\text{old bases}\left( \begin{bmatrix} 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 0 \\ 1 \end{bmatrix} \right) \xRightarrow [Transformation] {(1) \ (\text{old}\rightarrow \text{new}) \ \text{coord. system}} \ \text{new bases}\left( \begin{bmatrix} 2 \\ 1 \end{bmatrix}, \begin{bmatrix} -1 \\ 1 \end{bmatrix} \right)$$
* 이 과정에서 구좌표계를 기준으로한 우리의 misconception이 새로운 좌표계의 좌표로써 변환된다.  
* $$(2) \  \begin{bmatrix} -1 \\ 2 \end{bmatrix} \text{w.r.t. old system}  \xRightarrow[Translation]{(1) \ (\text{old} \rightarrow \ \text{new}) \ \text{coord. system}}  (2) \  \begin{bmatrix} -1 \\ 2 \end{bmatrix} \text{w.r.t. new system}  $$ 

#### 수치적 번역\(Numerical translation\)의 관점 

* 그러나, 실제로 행렬곱을 수치적으로 계산하는 과정의 결과는 벡터 \(2\)가 아니라, 벡터\(3\)이다. 
* 기하학적 변환의 결과는 결국 구좌표계의 좌표로써 읽어진다. 
* 변역의 관점에서는 동일한 벡터를 두고, 그 것을 읽는 언어가 바뀌는 것이다: 좌표 \(2\) $$\rightarrow$$좌표 \(3\) 
* 즉, 행렬 \(1\)은 신좌표로의 변환을 암시하지만, 동시에 구좌표로의 해독을 의미한다.  
* 번역의 방향성은 **\(신좌표계** $$\rightarrow$$ **구좌표계\)**로 인식된다.  \(vector를 읽는 language의 변화\) 
* $$(2) \ \text{new coord.}  \begin{bmatrix} -1 \\ 2 \end{bmatrix} \text{} \xRightarrow[Translation]{(1) \ (\text{new} \rightarrow \ \text{old}) \ \text{coord. system}}  (3) \ \text{old coord.} \begin{bmatrix} -4 \\ 1 \end{bmatrix}$$ 

#### 두 관점의 관계 

* 이러한 변환, 변역의 과정은 실제 계산 과정에서는 전후관계를 가진 것처럼 보인다.  
  * 행렬 \(1\)을 기술하는 행위 자체가 어떤 기하학적 변환을 의미
  * 그 후, 행렬의 벡터 \(2\)와의 행렬곱을 통해 벡터 \(3\)을 계산하는 과정은 수치적 번역의 과정 
* 그러나, 선형번환은 이 두 가지의 관점이 동시에 일어나는 것이라고 볼 수 있을 것이다. 
  * 신좌표계를 향해서 점들의 기하학적 변환이 일어나는 동시에, 
  * 이러한 과정이 구좌표계의 언어로\(원래의 기준점\)으로 해석되는 것. 

#### 역행렬의 재해석

* $$\begin{bmatrix} 2 & -1 \\ 1 & 1 \end{bmatrix}$$ 의 역행렬은 $$\begin{bmatrix} 1/3 & 1/3 \\ -1/3 & 2/3 \end{bmatrix}$$ 이다. 
* 원래 행렬의 변환을 기저벡터의 변환 과정으로 표현하면 다음과 같았다:
  * $$\left( \begin{bmatrix} 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 0 \\ 1 \end{bmatrix} \right) \Rightarrow  \left( \begin{bmatrix} 2 \\ 1 \end{bmatrix}, \begin{bmatrix} -1 \\ 1 \end{bmatrix} \right)$$ 
* 그러나 역행렬은 다음과 같이 단순히 그 역방향으로 나타나지 않는다: 
  * $$ \left( \begin{bmatrix} 2 \\ 1 \end{bmatrix}, \begin{bmatrix} -1 \\ 1 \end{bmatrix} \right) \Rightarrow \left( \begin{bmatrix} 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 0 \\ 1 \end{bmatrix} \right) $$ 
* 역행렬은 자기 자신을 표준\(기저벡터\)으로 삼아서, 변환 전 기저벡터를 다시 서술한다: 
  * $$\left( \begin{bmatrix} 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 0 \\ 1 \end{bmatrix} \right) \Rightarrow  \left( \begin{bmatrix} 1/3 \\ 1/3 \end{bmatrix}, \begin{bmatrix} -1/3 \\ 2/3 \end{bmatrix} \right)$$ 
* 다음 사항들을 유의하자. 
  * 행렬은 항상 **변환 직전의 상태를 표준\(standard\)**으로 전제하 변환을 수행한다. 
  * 행렬은 항상 오른쪽에서 입력 벡터를 받는다: \[행렬\] x \[입력벡터\] = \[출력벡터\] 
  * 그러므로, 행렬의 오른편에 오는 **입력벡터**\(좌표\)가 해당 **행렬**\(좌표계\)**와의 대응을 확인**해야 한다. 
  * 이때는 변환의 관점보다 **번역의 관점에서 행렬을 해석하는 것이 편리**하다. 
* 다음 예시를 살펴보자. 
  * \($$M_{(n)\leftarrow (m)}$$은 좌표계 $$m \rightarrow n$$방향의 번역행렬이고, 그 역행렬이 $$M_{(m)\leftarrow (n)}$$\)
  * \(좌표계$$i$$에 살고 있는 입력 벡터를 $$\vec{x}_{i}$$, 좌표계 $$j$$에 살고 있는 출력벡터를 $$\vec{v}_{j}$$로 표기\)
  * $$M_{(1) \leftarrow (2)} \underbrace{ M_{(2) \leftarrow (3)} \underbrace{M_{(3) \leftarrow (4)}\vec{x}_{(4)}}_{\vec{x}_{(3)}} }_{\vec{x}_{(2)}} =\vec{v}_{(1)}$$
  * 우측에서부터 점진적으로 벡터 입력을 계산해나갈때 **좌표**와 **좌표계의 언어**가 **일치해야 한다**.  
  * 행렬과 벡터의 좌표언어는 명시적으로 드러나지 않으므로, 만든 사람이 잘 기억하고 활용해야함. 

### 행렬도 번역할 수 있다 

* 번역할 수 있는 것은 좌표 뿐만이 아니다. 행렬도 번역할 수 있다. 
* 설명의 편의를 위해, 위의 _구좌표계_를 '**우리의 언어**', _신좌표계_를 '**Jennifer의 언어**'라고 해보자.
* 이제, '우리의 언어'로 기술된 행렬을 'Jennifer의 언어'로 **번역**해보겠다. 

#### 번역할 행렬은 다음과 같다. 

* $$\begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$$: 이는 반시계방향으로 90도 회전시키는 회전행렬이다. 
* 그러나 이 행렬은 '우리의 언어'를 기준으로 기록된 것이다. 
  * \(90도 회전이라는 것도 우리 언어, 우리의 시점일 뿐이다.\) 
* 동일한 기하학적 변환이 'Jennifer의 언어'로는 다르게 표현될 것이다. 

#### 다음의 절차를 통해 행렬의 번역과정을 이해해보자. 

1. 'Jennifer의 언어'로 쓰여진 어떤 벡터에서 출발: $$\begin{bmatrix}-1 \\ 2 \end{bmatrix}$$
   * 최종목표: 벡터를 90도 회전\(in '우리의 언어'\) 시키기  
2. 이 벡터를 '우리의 언어'로 먼저 번역:  $$\begin{bmatrix} 2&-1\\1&1 \end{bmatrix}\begin{bmatrix}-1 \\ 2 \end{bmatrix}$$
   * 이 행렬을 Change of basis matrix라고 한다. 
3. 90도 회전\(in '우리의 언어'\) 수행: $$\begin{bmatrix} 0&-1\\1&0 \end{bmatrix}\begin{bmatrix} 2&-1\\1&1 \end{bmatrix}\begin{bmatrix}-1 \\ 2 \end{bmatrix}$$ 
4. 다시 'Jennifer의 언어'로 번역: $$ \begin{bmatrix} 2&-1\\1&1 \end{bmatrix}^{-1}\begin{bmatrix} 0&-1\\1&0 \end{bmatrix}\begin{bmatrix} 2&-1\\1&1 \end{bmatrix}\begin{bmatrix}-1 \\ 2 \end{bmatrix}$$ 

* 다음 행렬이 'Jennifer의 언어'로 쓰여진 \('우리의 언어'로 90도 회전행렬과\) 동일한 변환 행렬이다:
  * $$\begin{bmatrix} 2&-1\\1&1 \end{bmatrix}^{-1}\begin{bmatrix} 0&-1\\1&0 \end{bmatrix}\begin{bmatrix} 2&-1\\1&1 \end{bmatrix}=\begin{bmatrix} 1/3 & -2/3 \\ 5/3 & -1/3 \end{bmatrix}$$ 

### 다음과 같은 표현의 의미: $$A^{-1}MA$$

* 강의에서는 Mathematical sort of empathy\(수학적 종류의 공감?\)이라고 표현하고 있다. 
* 무슨 다른 관용적 표현에 해당하는지는 잘 모르겠지만, 대충 의미를 짐작해볼 수 있다.  
* **Empathy**: the ability to share another person's feelings and emotions as if they were your own.
* **감정적 공감**: \[다른 사람의 감정 $$\leftarrow$$ 나의 감점\] \[나의 감정\] \[나의 감정 $$\leftarrow$$ 다른 사람의 감정\]
* **수학적 공감**: 어떤 변환\($$M$$\)을  다른 사람이 보았을때의 시각으로 나타내주는\($$A^{-1} \square A$$\) 것. 

### 이러한 좌표계 변환\(Change of basis\)을 어떻게 활용하는지 궁금한가? 

* 다음 에피소드\(Eigenvectors and eigenvalues\)에서 eigenbasis에 바로 활용되니 기대하시라. 

