# Dot products\(E9\)

## E9. Dot products and duality

### **지금 dot product를 배우는 이유?**

* 보통은 선형대수 초반에 'dot product\(내적\)'을 배우는게 일반적이다. 
* 그러나, 내적의 수학적 역할은 **linear transformation을 통해 이해**하는 것이 효과적이다!

### **dot product\(**$$\cdot$$\)**란?**  

* **scalar product**\(결과가 벡터가 아닌 스칼라\)라고도 불림. 
* 카르테시안 좌표계에서의 dot product를 특히 다음과 같이 부름.
  * **inner product** \(혹은 드물게 **projection product**\)  
  * inner product와 dot product의 엄밀한 구분은 MML책에서 알아보자. 
* 같은 크기의 column vector의 같은 원소끼리 각각 곱한 값을 모두 더한 것! 
  * 쉬우니까 수학적 정의는 생략. 

### **dot product의 기하학적 해석?**

* **\(dot product\) = \(벡터1의 길이\) x \(벡터2를 벡터1에 정사영한 길이\)** 
* 두 벡터가 같은 방향이면 양수, 수직이면 0, 다른 방향이면 음수. 
* 다시 이야기하면 어떤 벡터에 **projection**하고 그 벡터의 크기만큼 **scaling**하는 것!  
  * **project-then-scale**

#### 좀 더 수학적으로 적어보면:

* \(벡터2를 벡터1에 정사영한 길이\) = \(벡터 2의 길이\) x \(벡터1과 2가 이루는 각의 sine함수 값\)
* \(dot product\) = \(벡터1의 길이\) x \(벡터2의 길이\) x \(벡터1과 2가 이루는 각의 sine함수 값\) 

#### 수학적으로 벡터 1과 벡터 2의 순서는 바뀌어도 같은 결과! 

* 즉, 벡터1에서 벡터2로 정사영하나, 벡터2에서 벡터1로 정사영하나 결과는 같다. 
* 사실 수학적으로 보면 간단하다. 
  * $$ \bm{a}  \cdot \bm{b} = \Vert a \Vert \Vert b \Vert \text{cos}\theta = \Vert b \Vert \Vert a \Vert \text{cos}\theta = \bm{b}  \cdot \bm{a}$$

#### 기하학적으로도 생각해보자. 

* 두 벡터가 대칭이면 일단 교환법칙 성립. 
* 이 상태에서 벡터 1을 2배로 스케일링 해보자. 
* **벡터1을 벡터2로 정사영**: 그림자의 길이가 2배이므로 dot product값도 2배
* **벡터2를 벡터1로 정사영**: 투사받는 벡터가 2배이므로 dot product값도 2배 
* 즉, 두 벡터의 길이를 나타내는 scaling factor는 어느 순서로 연산하든 결국 서로 곱해진다.  
* 두 벡터의 각도가 이 scaling factor를 조정하며, 각도는 연산 순서와는 관계가 없다. 

![](../../.gitbook/assets/image%20%2871%29.png)

![&#xAC19;&#xC740; &#xBC29;&#xD5A5;&#xC774;&#xBA74; &#xC591;&#xC218;, &#xC218;&#xC9C1;&#xC774;&#xBA74; 0, &#xB2E4;&#xB978; &#xBC29;&#xD5A5;&#xC774;&#xBA74; &#xC74C;&#xC218;](../../.gitbook/assets/image%20%2843%29.png)

### **dot product의 유용성**

* 벡터가 같은 방향을 가리키고 있는지 아닌지를 테스트할 수 있음. 
* _**projection**_에 대한 이해를 도와줌. 

### **왜 dot product는 projection과 관련이 있을까?** 

* 두 벡터의 같은 위치의 숫자를 곱해서 더하는 계산이 projection과 대체 무슨 관계일까? 
* dot product와 projection 사이의 관계는 _**duality**_로 설명할 수 있다.  

### **수학에서의 일반적 duality란?**  

* Natural-but-surprising correspondence between 2 types of mathematical thing.
* 두 타입의 수학적 개념 사이에 존재하는 **필연적이지만 직관적으로 파악하기 어려운 관련성**. 

### **지금 이야기하는 duality?** 

* **Dot product**  $$\Leftrightarrow$$  **Matrix-vector multiplication** 
* **\(다차원 공간에 존재하는 벡터와의 내적\)**  $$\Leftrightarrow$$ **\(다차원 공간에서 1차원으로의 선형변환\)** 
  * 양자가 각각 서로에 대한 'dual'이다. \(아래 그림\)
* 일단 계산결과가 동일한 것으로 둘이 동치인 것은 쉽게 증명이 된다.  
  * $$\begin{bmatrix} 2 \\ 3 \end{bmatrix} \cdot \begin{bmatrix} x \\ y \end{bmatrix} =2x+3y \ \ \Leftrightarrow \ \ \begin{bmatrix} 2 & 3 \end{bmatrix}  \begin{bmatrix} x \\ y \end{bmatrix}  = 2x+3y$$
* 직관적이지 않은 이 관계를, 의미적으로 받아들이는 것이 중요하다.  

#### Duality는 다음의 질문에 답할 수 있도록 도와준다. 

> dot product의 계산방법\(원소간의 곱\)은 왜 이러한 기하학적 의미\(project-then-scale\)를 갖는 것일까?

* 우리가 이미 배운 지식의 전이\(knowledge transfer\)를 활용해보자.  
* 행렬의 곱의 계산방법이 어떤 기하학적 의미와 연결되는지는 선형변환을 통해 이미 배웠다. 
* 그리고 dot product의 계산방법은 행렬의 곱과 일치한다. 
* 뭔가 알아낼 수 있을 것 같지 않은가? 
* **duality는 이러한 지식의 전이의 연결점이 되어준다.** 

![\(&#xC88C;\) &#xB2E4;&#xCC28;&#xC6D0; &#xACF5;&#xAC04;&#xC5D0; &#xC874;&#xC7AC;&#xD558;&#xB294; &#xBCA1;&#xD130; / \(&#xC6B0;\) &#xB2E4;&#xCC28;&#xC6D0; &#xACF5;&#xAC04;&#xC5D0;&#xC11C; 1&#xCC28;&#xC6D0;&#xC73C;&#xB85C;&#xC758; &#xC120;&#xD615;&#xBCC0;&#xD658;](../../.gitbook/assets/image%20%28102%29.png)

### **어떤 의미인지 예를 통해서 자세히 알아보자.**  

* dot product가 원래 projection과 관련이 있었다는 사실을 우리가 모른다고 가정해보자.  
  * 계산 방법만 알고, 기하학적 의미는 모른고 가정. 
* **그 상태에서 역방향으로 접근**: projection으로부터 시작하여 dot product의 꼴을 만들어보자. 
  * 어떤\(사실은 의도된\) projection을 행렬로 나타내본다. 
  * 그 행렬을 통한 선형변환이 결국 dot product의 계산과 같음을 보인다. 
  * 이제 dot product는 \(우연히 발견한 ~~척 하는~~\) projection의 기하학적의미와 연결된다. 
* \(이런 **역방향의 논리 전개**가 주는 이점은 잘 모르겠다.\) 
* \(우연에서 필연으로 가는 구조가 설명하는데 편할 것 같긴한데, 이해하는 입장에선 별로인 것 같다.\) 
* \(어차피 duality의 가장 근원적 연결고리는 계산 form이 동일하다는 것. 그 이상의 직관은 나오지 않음.\)  
* \(**고차원** $$\rightarrow$$ **저차원의 선형변환이 projection으로 일대일 대응 가능하다는 것이 포인트!**\) 

### **일단 unit vector를 가지고 실험해보자.** 

####  **\[Fig. A\]과 같은 linear transformation, 즉, projection matrix를 구해보자.** 

* 이 projection은 다분히 의도된\(dot product와 강한 관련이 있는\) 것이지만 모른척하고 가보자. 
* projection은 선형변환이 맞다. \(증거: evenly spaced dot들이 변환 후에도 등간격 유지.\)
* 즉, 행렬로 나타낼 수 있다. 
  * **입력**: 2차원 벡터\(보라색 점\)
  * **출력**: 1차원 숫자 하나\(파란색 좌표\)

![\[Fig. A\]](../../.gitbook/assets/image.png)

#### 우리가 projection하고자 하는 파란선와 overlay되어있는 **unit vector**를 $$\bm{\hat{u}}$$라고 하자.

* $$\bm{\hat{u}}$$ 의 좌표는 $$(\bm{\hat{u}}_x , \ \bm{\hat{u}}_y )$$이라고 하자.  

#### 선형변환 행렬은 standard basis vector $$\bm{\hat{i}}, \bm{\hat{j}}$$가 어디에 랜딩하는지만 기록하면 된다. 

* basis vectors의 projection을 column으로 하는 행렬이 우리가 원하는 선형변환\(projection\) 행렬이다. 
* **\[Fig. B\]**에서의 대칭성을 이용하면, $$\hat{\bm{i}}\rightarrow \bm{\hat{u}}_x$$, $$\hat{\bm{j}}\rightarrow \bm{\hat{u}}_y$$로 이동\(투사\)함을 알 수 있다.  
* 그러므로, **projection matrix**: $$\begin{bmatrix} \bm{\hat{u}}_x \ \ \bm{\hat{u}}_y \end{bmatrix}$$

![\[Fig. B\]](../../.gitbook/assets/image%20%28145%29.png)

#### 이제 행렬 $$\begin{bmatrix} \bm{\hat{u}}_x \ \ \bm{\hat{u}}_y \end{bmatrix}$$만 왼쪽에서 곱해주면 어떤 벡터도 파란 직선으로 정사영 시킬 수 있다. 

* 그런데 이 연산은 unit vector$$\begin{bmatrix} \bm{\hat{u}}_x \\ \bm{\hat{u}}_y \end{bmatrix}$$와의 dot product의 계산방법과 정확히 일치한다.  
  * 놀랍지 않은가? \(~~발연기~~\)  

#### 이를 통해 dot product는 이 행렬의 기하학적 의미를 자신의 것으로 가질 수 있다.  

* 어떤 벡터와 단위벡터 $$\bm{\hat{u}}$$와의 dot product의 의미?
  * 어떤 벡터를 $$\bm{\hat{u}}$$가 span하는 직선으로 정사영 한뒤, 그 길이\(1차원 숫자\)를 취하는 것! 

#### 위에서 그냥 받아들였던 설명과 비교해보자.  

* \(벡터1의 길이\) x \(벡터2를 벡터1에 정사영한 길이\) 
* unit vector는 크기가 1이므로 관심 벡터의 정사영의 길이만 고려하면 된다. \(일치\) 

### **이제 non-unit vector\(**$$\bm{\hat{v}}=c\bm{\hat{u}}, \ c\in\mathbb{R}$$**\)로 논의를 확장해보자.** 

dot product는 unit vector만 가지고 하는 것이 아니다. 일반 벡터 ****$$\vec{\bm{v}}$$ 와의 dot product에 대해 알아보자. 

#### 행렬에 실수배를 취해보자: $$\begin{bmatrix} \bm{\hat{v}}_x \ \ \bm{\hat{v}}_y   \end{bmatrix}=\begin{bmatrix} c\bm{\hat{u}}_x \ \ c\bm{\hat{u}}_y   \end{bmatrix}$$ 

* 이 행렬의 이름을 굳이 붙이자면, **project-then-scale matrix**이다. 
* 이 행렬이 의미하는 선형 변환: projection을 한 뒤, $$c$$**만큼 scaling**.  

#### 이전에 했던 것처럼, 이 행렬을 통해 얻을 수 있는 기하학적 의미를 생각해보자.   

* 어떤 벡터와 벡터 $$\bm{\hat{v}}$$와의 dot product의 의미?
  * 어떤 벡터를 $$\bm{\hat{v}}$$로 projection 시킨 뒤, $$\bm{\hat{v}}$$의 크기만큼 **scaling한 길이**를 취하는 것! **\[Fig. C\]** 

#### **따져보면 역시 실제 dot product의 정의와 일치한다.**   

### **좀 더  쉬운 이해?** 

* 위의 설명방식에서는 계산 방법의 우연한 일치가 duality의 가장 핵심적 요인이다. 
* 굳이 빙빙돌려 설명하는게 아닌가 싶기도 하다. 
* 좀 더 쉽게 이해해볼 수 있을까?

#### **벡터**$$[2, 1]^\top$$**가 span하는 직선 위로** $$\bm{\hat{i}}, \bm{\hat{j}}$$**를 projection\(**$$\mathcal{L}$$**\)을 하는 것을 상상해보자.**  

#### 이미 이들의 길이 비율은 $$\Vert \mathcal{L}(\bm{\hat{i}})\Vert: \Vert\mathcal{L}(\bm{\hat{j}})\Vert=2:1$$이다. \(삼각형의 닮은꼴\) 

* 벡터의 좌표와 선형변환 행렬의 성분의 비례가 같다는 것. 
* 벌써 벡터와 projection\(선형변환\)의 관계가 보인다! 
* 비율은 이미 맞으니, scaling만 잘하면 되겠다는 느낌이 온다. 

#### Projection을 나타내는 선형변환 행렬로 정확히 표현하면: $$\begin{bmatrix} 2/\sqrt{5} & 1/\sqrt{5}\end{bmatrix}$$

* 이 행렬을 잘 관찰하면 벡터의 '길이'로 나누어져 있음을 알 수 있다. 
*  '길이\($$\sqrt{5}$$\)'만 곱해주면 처음 주어진 벡터의 transpose와 같게 만들 수 있다! 
* 그리고 이 행위는 $$\bm{\hat{i}}, \bm{\hat{j}}$$를 projection한 뒤, 똑같이 $$\sqrt{5}$$만큼 곱해주는 것과 같다. 

#### 결론적으로, 다음 두 행위는 동치이다.  

* 어떤 벡터를 $$[2, 1]^\top$$ 위로 projection하고 $$\sqrt{5}$$만큼 scaling하는 것. \(내적\) 
* 어떤 벡터를 행렬 $$\begin{bmatrix} 2 & 1\end{bmatrix}$$로 왼쪽에서 곱해주는 것. \(선형변환\) 

#### 요약하면:

1. 특정 벡터 위로 정사영을 하는 것을 선형변환으로 나타내면 그 성분의 비가 같다. 
2. 비율 뿐 아니라 실제 값까지 같도록 하고 싶다면, 벡터 크기만큼 스케일링을 해줘야 한다. 
3. 1번\(projection\)과 2번\(scaling\)을 차례로 수행한 선형변환이 곧 dot product이다.  

#### **\[Fig. C\]**는 같은 개념의 다른 좌표들의 예시를 보여준다. \(projection이 음의 방향인 경우\)  

![\[Fig. C\]](../../.gitbook/assets/image%20%2862%29.png)

### **통찰 및 일반화**

#### **특정 벡터와의 dot product**

*  ****= \(그 벡터에 대한 projection\) + \(그 벡터의 크기로 scaling\) 
*  = the composition of those two
*  = matrix\(그 벡터의 transpose\) multiplication

#### **span of vector\(s\)** $$\rightarrow$$ **linear transformation**

* 벡터는 단순한 공간 안의 화살표가 아닌, 선형변환의 물리적 구현체로 이해될 수 있음.
* 어떤 벡터들을 basis로 하는 subspace를 보았을때의 insight:
  * subspace 위로 projection + scaling하는 일련의 행위는 하나의 특별한 행렬로 표현가능. 
  * 이 행렬은 vector를 transpose한 모양?
    * \(나중에 projection 제대로 학습 후, 확인할 것!\) 
* 다차원에서 1차원\(span of vector가 직선\)으로의 선형변환일 때: 
  * linear transformation\(projection + scaling\)은 특별히 이름이 있다: _**dot product**_.
* \(나중에 좀 다듬어야할 듯!!!\)

#### **linear transformation** $$\rightarrow $$ **span of vector\(s\)**

* 특정 선형변환을 간단한 벡터로 표현하여 생각하는 것이 용이할 수 있음.  
* 이 개념은 고차원에서 저차원으로의 선형 변환을 이해할때 유용한 insight를 제공해준다. 
  * **\[Fig. C\]**의 오른쪽 선형 변환을 기준으로 왼쪽 벡터를 찾아낼 수 있다. 
*  어떤 선형변환 행렬\(고차원$$\rightarrow $$저차원\) 이 있다고 가정해보자. 
  * 이 것에 대응\(dual\)하는 고차원에 살고있는 저차원 subspace가 **반드시 존재**한다. 
  * 즉, 이 subspace에 대한 projection과 scaling으로 동일한 선형 변환을 수행할 수 있다. 
* \(일반화 가능한지 확인!!!\) 

### **Duality의 활용**

* 이 개념 자체가 어떤 문제에 직접적으로 활용될 수 있는 실용성이 있는지는 잘 모르겠다.   
* \(참고로 E11에서 cross product의 계산 방법과 기하학적 의미를 이해하는데 이 개념을 사용.\)

#### Sanderson은 이 개념을 통해 선형대수의 어떤 에센스를 전달하고 싶었던 걸까?  

* 이 과정을 통해 dot product와 선형변환의 개념자체가 더 명료해짐. 
* 고차원에서 저차원으로의 선형변환을 projection 관점에서 ???
* 서로 관련이 없어보이는 것들이 연결됨으로써 현상을 다른 관점으로 해석할 수 있다는 통찰. 
  * 이 것은 실제로 선형대수에서 아주 빈번이 일어나는 현상인 것 같다. 
  * 이런 것이 이 학문의 매력이고 beauty가 아닐까? 



