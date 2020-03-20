# Linear transformation\(E1-E6\)

## E1. Vectors, what even are they?

### 벡터란 무엇인가?

#### 학과에 따라 다른 관점을 갖는다.  

* **Physics 관점**: 크기와 방향을 갖는 화살표. 공간 안에서 어디로 움직이더라도 같은 벡터. 
* **Computer Science 관점**: 순서가 정해져있는 숫자들의 리스트. 
* **Mathematician 관점**: 위의 두 시각을 일반화하고자 함. 

#### 다음 두 가지개념만 존재한다면 어떤 것이든 벡터가 될 수 있음. 

1. 두 벡터를 더하기 \(_**vector addition**_\)
2. 벡터에 숫자를 곱하기 \(_**scalar multiplication**_\)
   * 벡터를 scaling\(크기조정; 비례 확대/축소\)하는 number를 **scalar**라고 부름. 

* **선형대수의 모든 주제는 위 두 개의 operation을 둘러싸고 이루어짐.** 
* 선형대수에서 논하는 거의 대부분의 벡터는 **tail이 원점에 고정**되어 있음\(Physics 관점과 다름\). 
* **선형대수의 유용함**: Physics관점\(geometric\)와 CS관점\(numerical\)을 오가면서 이해할 수 있음. 

## E2. Linear combinations, span, and basis vectors

### Basis vector \(기저벡터\)

#### 2차원$$xy$$좌표계에는 다음 두 개의 단위벡터\(unit vector\)가 존재한다. 

*  $$x$$축 방향으로 크기가 1인 벡터\($$\hat{i} $$\) 
*  $$y$$축 방향으로 크기가 1인 벡터\($$\hat{j}$$\)

$$\hat{i}$$와 $$\hat{j}$$를 $$xy$$좌표계의 _**basis vectors**_\(기저벡터\)라고 부른다. 

### Coordinate \(좌표\)

* 좌표\(coordinate\)는 대응되는 기저벡터들을 scaling하는 scalar로 볼 수 있다.

#### 다른 basis vector들을 사용해서 좌표계를 나타낼 수도 있었을 것이다! 

* 같은 점이 완전히 다른 좌표로 표현될 수도 있다는 이야기다. 
* 벡터를 수치적으로 표현할때는 **반드시 어떤 basis의 선택이 암묵적으로 전제**되어 있다. 

### **Linear combination** \(선형조합\)

* 특정 \(basis\) vector들을 scaling하고 더하는 것을 **linear combination**이라고 한다.
* _**linear**_**인 이유?** 하나의 벡터를 고정하고 나머지만 scaling하면 _line_이 된다. 

![](../.gitbook/assets/image%20%2815%29.png)

#### Span이란? \(2차원 공간에서\)  

* span의 일반 사전적 의미: 
  * n. 지속되는 시간, 포괄하는 범위.
  * v. 얼마의 기간에/어떤 범위에 걸치다. 
* 두 벡터의 모든 linear combination으로 만들 수 있는 범위를 '_**두 벡터의 span'**_이라고 함.  \(명사\)
* 어떤 vector space를을 basis vector들이 **'**_**span한다**_'라고 표현한다.  \(동사\) 
* 대부분의 경우는 2D **평면** 전체가 될 것이다. 
* 만약 두 벡터가 같은 line에 있으면 **선**, 두 벡터가 모두 영벡터이면 **점**.

![](../.gitbook/assets/image%20%2865%29.png)

#### 3차원 공간에서 3개 기저벡터의 span

*  2개의 기저벡터가 만든 평면이 나머지 1개의 벡터에 의해 평행이동으로 표현가능
* 즉, 3차원 전체 공간을 span한다. 

![](../.gitbook/assets/image%20%2812%29.png)

### **Linear dependence** \(선형 독립\)

* 예를 들어, 두 개의 벡터가 같은 직선 위에 놓여있다면?
  * linear combination의 관점에서 아무런 contribution이 없음. \(추가적 자유도가 발생x\) 
  * 이런 경우, 두 개의 벡터는 _**linearly dependent**_하다고 한다. 
  * 반대의 경우\($$\vec{w}\neq a\vec{v}, a\in \mathbb{R})$$, _**linearly independent**_하다고 한다. 
* 선형 독립을 이용한 basis의 재정의 
  * The basis of a vector space is a set of linearly independent vectors that span the full space.
  * **벡터 공간의 basis는 그 공간 전체를 span하는** _**선형독립**_ **벡터들의 집합이다.** 
  * 즉, linearly dependent한 놈이 섞여있으면 basis가 아니다.  

## E3. Linear transformations and matrices

### Introduction 

#### **행렬을 공간의 선형변환으로 이해해보자.**     

* 이는 다른 선형대수 개념에 앞서 _선행되어야할 단 하나의 토픽_을 꼽으라면 바로 **선형변환**! 
* 대부분의 학생들이 이 개념을 잘 모르고 선형대수를 공부한다. 
* **Sanderson\(컨텐츠 제작자\)이 가장 중요하다고 생각하는 에피소드!** 

### Linear transformation \(선형변환\)

* Linear + transformation

#### Transformation \(변환\)

* function과 유사하다. 숫자를 입력받아 다른 숫자를 출력으로 내밷는 것. 
* 선형대수에서의 transformation은 벡터를 받아서 벡터를 내받는 것. 
* 벡터의 'movement'라는 뉘앙스를 담고 있는 용어. 

#### Linearity \(선형성\)

* 변환은 변환인데 '선형'변환이다!
* 선형\(linear\)이라는 말은 무엇을 의미하는가?
* 공간의 모든 점들이 선형적으로 움직이는 변환을 상상해보자. 

#### **Linear transformation의 두 가지 특성**

1. 공간의 모든 직선은 변환 후에도 직선
2. 원점은 변환 후에도 원점에 고정 

#### Linear transformation은 grid line의 변화로써 표현 가능 

* _remains **parallel** and **evenly-spaced**_
* 선형 변환 후에 모든 선들이 **일정한 간격**으로 **평행**을 유지 
  * 이는 직관적인 설명이며, 공식적인 정의는 E15에서 배울 것임.

#### **선형 변환을 어떻게 수치적으로 나타낼 수 있을까?** \(2D case\)  

* 두 개의 basis vector들이 선형변환 후에 **각각 어디에 떨어질\(land\) 것인지**를 기록하면 된다. 
* \(선형변환 전인\) 모든 벡터는 standard basis vector의 선형조합으로 표현할 수 있음. 
* 선형변환 후의 벡터를을 새로운  basis vector에 대한 **동일한 scaling factor**\(좌표\)로 표현 가능하다. 
  * **변환 전**: $$\vec{v}={\color{red}-1} \hat{i}+{\color{red}2}\hat{j}$$
  * **변환 후**: $$\text{Transformed} \ \vec{v} = {\color{red}-1}(\text{Transformed} \ \hat{i}) +{\color{red}2}(\text{Transformed} \ \hat{j})$$
* **즉, basis vector의 변환만 고려하면 나머지 모든 전체 점들에 대한 이동을 기술할 수 있게 됨.** 
  * 이 모든 것이 선형성 때문에 얻을 수 있는 혜택  
  * 즉, 그리드 라인이 일정한 간격으로 평행을 유지하기 때문

#### 예를 들어보자.

* 변환 후에 다음과 같이 basis vector의 선형 변환\($$L$$\)이 일어났다고 가정해보자.
  * $$\hat{i} = \begin{bmatrix} 1 \\ 0 \end{bmatrix} \xrightarrow{L} \begin{bmatrix} 3 \\ -2 \end{bmatrix},   \ \hat{j} = \begin{bmatrix} 0 \\ 1 \end{bmatrix} \xrightarrow{L} \begin{bmatrix} 2 \\ 1 \end{bmatrix}$$
* $$\begin{bmatrix} x \\ y \end{bmatrix}$$는 선형 변환 후 다음의 위치로 움직일 것이다.  
  * $$L\left(\begin{bmatrix} x \\ y \end{bmatrix}\right)=x\begin{bmatrix} 3 \\ -2 \end{bmatrix}+y\begin{bmatrix} 2 \\ 1 \end{bmatrix}=\begin{bmatrix} 3x+2y \\-2x + y \end{bmatrix}$$
  * 변환된\(transformed\) 기저벡터를 기준으로 동일한 좌표 $$\begin{bmatrix} x \\ y \end{bmatrix}$$ 를 표현. 

#### 이 과정은 우리가 알고 있는 Matrix multiplication\(행렬곱\)과 같다.

* 재밌는 것은 _이러한 선형변환을 **matrix multiplication**으로 나타낼 수 있다_는 것이다. ****
  * \(변환된 basis vector들을를 column으로 하는 행렬\) $$\times$$\(좌표 벡터\)
  * $$\begin{bmatrix} 3 & 2 \\ -2 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix}=x\begin{bmatrix} 3 \\ -2 \end{bmatrix}+y\begin{bmatrix} 2 \\ 1 \end{bmatrix}=\begin{bmatrix} 3x+2y \\-2x + y \end{bmatrix}$$ 
  * 이를 일반화된 식으로 써보면 고등학교 과정에서 배운 행렬곱 공식과 같음을 알 수 있다. 

#### 우리가 야생에서 행렬을 마주쳤을때 가져야하는 시각:

* 이 행렬의 행렬곱을 이용하면 어떤 벡터든지 **linear transformation** 시킬 수 있다.
* 이 행렬의 각 **column**들은 각 standard basis vector들의 transformed 후의 위치를 나타낸다. 
* 행렬곱의 결과는 transformed된 basis vector들의 \(기존과 동일한\) linear combination이다.
  * **같은 좌표값**이지만 선형변환된 **다른 좌표계**로 표현 

#### 간단한 선형변환을 하는 행렬을 만들고 싶을때: 

* 각각의 standard basis들이 변환 후 어디로 랜딩하게 하고 싶은지를 행렬의 column에 적는다.   

#### 2x2 행렬의 column이 linearly dependent할 때:

* 2D 공간\(평면\)이 1D 공간\(선\)으로 짜부러\(?\)진다. 
  * Sanderson이 자주 사용하는 '_**squished**_' 라는 표현은 _짜부러지다/찌부러지다_로 번역하겠다.
  * 나중에는 '_**squishification**_'이라는 신조어까지 만들어낸다. 
* 예를 들어 아래 그림과 같은 선형변환의 경우, 두 벡터의 선형결합은 직선 위에 갇힌다. 
  * 전체 공간을 span할 수 없다. 
* 여기서 짜부러지는 차원이 어디로 사라지는지는 이후에 배울 nullspace 개념에서 나온다. 

![](../.gitbook/assets/image%20%28164%29.png)

## E4. Matrix multiplication as composition

#### 두 개의 선형 변환을 순서대로 진행한 결과는 **'새로운' 하나의 선형 변환**으로 볼 수 있다.

* **rotation**\($$M_1$$\)과 **sheer**\($$M_2$$\)는 각각 독립적 선형변환
* 이 둘을 순차적으로 진행한 선형변환 결과\(**composition**\) 새로운 하나의 선형변환 
* 즉, 새로운 행렬\($$M_2M_1$$; **왼쪽에서 오른쪽 순서로 진행**\)로 나타낼 수 있다는 얘기.  

#### 두 행렬의 곱, 수치적으로 어떻게 계산할까?

* $$M_2M_1=\begin{bmatrix} 0 & 2 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} 1 & -2 \\ 1 & 0 \end{bmatrix}$$
* 각각의 standard basis vector들이 변환 후에 어디로 이동할 것인지 생각해보자.
* $$\hat{i}$$: $$\begin{bmatrix} 1 \\ 0 \end{bmatrix} \xrightarrow{M_1} \begin{bmatrix} 1 \\ 1 \end{bmatrix} \xrightarrow{M_2} \begin{bmatrix} 0 & 2 \\ 1 & 0 \end{bmatrix}  \begin{bmatrix} 1 \\ 1 \end{bmatrix}=1\begin{bmatrix} 0 \\ 1 \end{bmatrix} + 1\begin{bmatrix} 2 \\ 0 \end{bmatrix} =\begin{bmatrix} 2 \\ 1\end{bmatrix} $$
* $$\hat{j}$$: $$\begin{bmatrix} 0 \\ 1 \end{bmatrix} \xrightarrow{M_1} \begin{bmatrix} -2 \\ 0 \end{bmatrix} \xrightarrow{M_2} \begin{bmatrix} 0 & 2 \\ 1 & 0 \end{bmatrix}  \begin{bmatrix} -2 \\ 0 \end{bmatrix}=-2\begin{bmatrix} 0 \\ 1 \end{bmatrix} + 0\begin{bmatrix} 2 \\ 0 \end{bmatrix} =\begin{bmatrix} 0 \\ -2\end{bmatrix} $$ 
* E3에서 배웠듯이, basis vector가 떨어지는 위치를 결과 행렬의 column에 써주면 된다. 
* $$M_2M_1=\begin{bmatrix} 0 & 2 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} 1 & -2 \\ 1 & 0 \end{bmatrix}=\begin{bmatrix} 2 & 1 \\ 0 & -2 \end{bmatrix}$$ 
* 이를 일반화된 식으로 써보면 고등학교 과정에서 배운 행렬곱 공식과 같음을 알 수 있다.  

#### 우리가 두 행렬의 곱을 야생에서 마주쳤을때 가져야하는 시각:

* 오른쪽부터 왼쪽 순서대로 선형변환을 차례로 적용하는 과정을 나타낸다. 

#### 이러한 intuition을 가지고 보면 다음 규칙들이 자연스러움을 알 수 있다. 

* **Commutativity**:$$M_1M_2 \neq M_2M_1$$
* **Associativity**: $$(AB)C=A(BC)$$

## E5. Three-dimensional linear transformations

#### 2차원에서의 원리를 3차원에서도 그대로 확장하여 적용할 수 있다. 

* 3개의 standard basis vectors가 어디로 움직일지만 기록하면 전체 transformation을 기술 가능. 
* $$z$$축을 따라 **새롭게 제 3의 basis vector** $$\hat{k}$$**를 도입**하기만 하면 끝. 

#### 3차원 선형변환은 Computer graphics나 Robotics에서 활용된다. 

* 복잡한 선형변환을 _더 이해하기 쉬운_ 여러 개의 선형 변환들의 composition으로써 이해 가능. 

## E6. The determinant

### **Determinant of a transformation**

#### CASE 1. $$det(A)>0$$인 경우?

선형변환을 거치면서 **단위 면적/부피**가 **몇배로 늘어나는가**에 대한 **scaling factor**. 

* **2D**:  $$\hat{i}$$와 $$\hat{j}$$가 밑변과 높이를 이루는 **unit square의 면적**을 기준으로. \($$\rightarrow$$parallelogram\) 
* **3D**:  $$\hat{i}$$, $$\hat{j}$$, $$\hat{k}$$에 모서리에 얹혀있는 **unit cube의 부피**를 기준으로.  \($$\rightarrow$$parallelepiped\)
* **일반화**: Standard basis vector들이 만들어내는 **unit hypercube의 부피**를 기준으로.  

#### CASE 2. $$det(A)<0$$인 경우? 

* determinant의 크기 자체는 여전히 부피에 대한 scaling factor. \(CASE 1과 동일\) 
* **but, 공간의 방향이 뒤집히는** 느낌적인 느낌 \(Feels like flipping space\).  
* e.g. 2차원의 경우 unit square의 앞뒤가 뒤집히는 경우\($$\hat{i}$$가 $$\hat{j}$$보다 **반시계방향**에 위치\). 
* e.g. 3차원의 경우 standard basis vector들이 **왼손의 법칙**을 따라는 경우. 

#### CASE 3. $$det(A)=0$$인 경우?

* 전체 공간보다 **더 작은 차원의 subspace로 짜부러지는**\(squished\) 경우. 
* 예를 들어, **3차원** 전체공간에서 **평면**, **직선**, 또는 **점**으로 선형변환되는 경우.  
* 즉, 행렬 $$A$$의 column들이 **linearly dependent**한 경우. 

![determinant&#xB97C; &#xACC4;&#xC0B0;&#xD558;&#xB294; &#xC2DD; &#xC790;&#xCCB4;&#xAC00; &#xC911;&#xC694;&#xD55C; &#xAC83;&#xC740; &#xC544;&#xB2C8;&#xB2E4;.](../.gitbook/assets/image%20%28121%29.png)

#### determinant의 intuitive한 의미를 이해하고 나면, 다음을 받아들일 수 있다. 

* $$det(M_1M_2)=det(M_1)det(M_2)$$
* \($$M_1M_2$$에 의한 scaling factor\) = \($$M_1$$에 의한 scaling factor\) x \($$M_2$$에 의한 scaling factor\) 
* 면적/부피를 2배로 늘린 후 4배로 늘린 합성선형변환의 총 면적/부피 변화 스케일: 2 x 4 = 8!   

