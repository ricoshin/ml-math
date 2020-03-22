# Cross products\(E10-E11\)

## E10. Cross products

### **Cross product \(**$$\times$$**\)란?**

* **vector product**\(결과가 스칼라가 아닌 벡터\), 또는 directed area product라고도 불림. 
* dot product와는 달리 오직 **3차원에서만 정의**된다! \(영상에서 직접적으로 언급되지 않는다.\)  
* 2개의 3차원 벡터를 받아서 하나의 3차원 벡터를 출력하는 연산. 
* 계산 방법은 아래에서 알아보자.  

### **Cross product의 기하학적 의미** 

#### 다음 길이와 방향을 갖는 3차원 벡터 

* **길이**: 2개의 3차원 벡터가 이루는 평행사변형\(parallelogram\)의 넓이 
* **방향**: 2개의 벡터가 이루는 평행사변형에 수직 / [오른손의 법칙](https://en.wikipedia.org/wiki/Right-hand_rule)을 이용했을때 엄지의 방향. 

#### 아래 그림을 살펴보자. 

* $$\bm{p}=\bm{v}\times\bm{w}$$ 
* **입력**: $$\bm{v}, \bm{w}$$\(주황, 보라\)
* **출력**: $$\bm{p}$$ \(빨강\)
* 이 빨간색 벡터가 에피소드의 주인공이다! 

![Cross product&#xC758; &#xAE30;&#xD558;&#xD559;&#xC801; &#xC758;&#xBBF8;](../../.gitbook/assets/image%20%2835%29.png)

#### 계산방법 

* **\(길이\)만 구하기** 
  * \(2개의 입력 벡터가 2차원 평면에 놓여있다고 가정\) 
  * 2개의 입력 벡터를 column으로 하는 행렬\(2x2\)의 determinant와 같다. 
  * determinant는 선형변환 후에 standard basis vector가 이루는 parallelogram의 넓이. 
  * 오른손 법칙을 사용해서 평면을 뚫고 나오는 방향이면 positive / 반대는 negative. 
  * 엄밀히 말하면 이 것은 cross product가 아니다. \(3차원 벡터를 구하지 않았음\) 
  * 입력 벡터들이 xy-평면 위에 존재할때 z축은 무시하고 출력벡터의 길이만을 구해본 것.  
* **\(길이 + 방향\) 모두 구하기**
  * 이 놈이 제대로된 계산 방법이다. 
  * 다음과 같은 식이 되는 이유는 다음 에피소드에서 알아본다. 
  * $$\bm{v}\times\bm{w}=\begin{bmatrix} v_1\\v_2\\v_3\end{bmatrix}\times\begin{bmatrix} w_1\\w_2\\w_3\end{bmatrix}=\text{det}\left( \begin{bmatrix} \bm{\hat{i}}&v_1&w_1\\   \bm{\hat{j}}&v_2&w_2\\ \bm{\hat{k}}&v_3&w_3\end{bmatrix} \right) \\ =\bm{\hat{i}}(v_2w_3-v_3w_2)+\bm{\hat{j}}(v_3w_1-v_1w_3)+\bm{\hat{k}}(v_1w_2-v_2w_1)$$

#### 생각해볼만한 특징 

* 두 입력 벡터의 크기가 같을 때는 서로 이루는 각이 직각일 수록 cross product의 크기도 크다. 
  * 평행사변형의 한쪽 각을 90도 보다 늘리면 도형이 길쭉해지면서 면적이 작아진다.  
* 두 벡터 중에 하나를 고정하고 나머지 하나를 실수배하면, 전체 product의 크기도 같은 실수배.
  * 평행사변형의 높이를 고정하고 너비만 늘린다고 상상해보자. 

## E11. Cross products in the light of linear transformation

### **이번 에피소드의 목표**  

* cross product의 **계산 공식**과 그 **기하학적 의미** 사이의 관계를 알아보는 것. 

### **계획**: E9.에서 배운 **duality를 사용**해서 둘 사이의 관계를 구명해보자. 

1. Define a 3d-to-1d linear transformation in terms of $$\bm{v}$$and $$\bm{w}$$
   * $$\bm{v}$$와 $$\bm{w}$$를 사용하여, 어떤 3d-to-1d 선형 변환을 정의한다.  
2. Find its dual vector
   * 이 선형 변환과 대응되는\(dual\) 벡터를 찾는다. 
3. Show that this dual is $$\bm{v}\times\bm{w}$$
   * 이 벡터가 $$\bm{v}\times\bm{w}$$임을 보인다. 

* 이 방법은 cross product의 기하학적 해석을 더 잘 이해할 수 있도록 도와줄 것. 

### **계획\(재해석\)**:  무슨 말인지 좀 더 풀어서 설명해보자.  

* 외적의 결과벡터를 $$\bm{p}$$라고 하자. 

1. 어떤 **미지의 선형변환**에서 시작한다. 
   * 최종적으로는 이 선형변환이 $$\bm{p}$$와 dual 관계에 있음이 밝혀진다. 
   * 그러나 처음에는 그 사실을 모른다. \(Sanderson이 좋아하는 설명방식\)  
   * 변환행렬이 정확히 어떻게 생겼는지는 아직 모른다. 
2. 그 선형변환을 **dual vector와의 dot product로써 해석**한다.  
   * 단순히 행렬을 transpose하면 dual vector가 될 것이다. 
   * 변환행렬을 모르니까 당연히 transpose인 dual vector도 아직 모른다.
3. dual vector가 사실 **cross product** $$\bm{p}$$**와 같았다**는 것을 확인한다. 
   * 수식적으로 동치임을 밝힌다. \(연결점 확보\) 
   * 이제 dual vector에 대해 알게 되면, cross product도 알게 된다. 
4. dot product를 만족할 수 있는 $$\bm{p}$$를 찾고, 그 기하학적 특징을 밝힌다. 
   * 이 과정에 E10에서의 기하학적 해석과 동일한 결론을 얻게 된다. 

### **선행단계: 일단 cross product의 계산 식을 살펴보자.** 

* cross product의 결과벡터를 $$\bm{p}$$\(우리의 최종 관심사\)라고 하자. 
* $$\bm{p}=\bm{v}\times\bm{w}=\begin{bmatrix} v_1\\v_2\\v_3\end{bmatrix}\times\begin{bmatrix} w_1\\w_2\\w_3\end{bmatrix}=\text{det}\left( \begin{bmatrix} \bm{\hat{i}}&v_1&w_1\\   \bm{\hat{j}}&v_2&w_2\\ \bm{\hat{k}}&v_3&w_3\end{bmatrix} \right) \\ =\bm{\hat{i}}(v_2w_3-v_3w_2)+\bm{\hat{j}}(v_3w_1-v_1w_3)+\bm{\hat{k}}(v_1w_2-v_2w_1)$$**\[Eq. A\]**
  * 왜 3차원 행렬의 determinant를 이렇게 계산하는가는 이 lecture에서 다루지 않음. 
* $$\bm{\hat{i}}, \ \bm{\hat{j}}, \ \bm{\hat{k}}$$를 행렬 안의 숫자처럼 취급하고 있지만, 사실 이들은 벡터이다. 
  * 계산을 편하게 하기위한 trick일 뿐, **실제로는 넌센스**이다.  
* $$\bm{\hat{i}},  \bm{\hat{j}},  \bm{\hat{k}}$$가 첫번째 column에 배치하는 것의 의미가 무엇일까? 
  * 그 **계수**들이 결과벡터 $$\bm{p}$$**의 좌표로 해석**된다는 의미이다. 
  * 즉, $$\bm{v}\times\bm{w}=\begin{bmatrix} w_2w_3-v_3w_2 \\ v_3w_1-v_1w_3 \\ v_1w_2-v_2w_1 \end{bmatrix} = \bm{p}$$ 

### **시작: 이제부터 우리의 목표는?**

*  이렇게 이상한 방식으로 계산된 $$\bm{p}$$가 **왜 그러한 기하학적 해석을 갖느냐**를 알아내는 것. 
  * 왜 $$\bm{p}$$의 길이는 "$$\bm{v}$$와 $$\bm{w}$$가 만드는 평면"의 넓이일까? 
  * 왜 $$\bm{p}$$는 그 평면에 수직 방향일까? 
  * 저 랜덤하게 보이는 $$\bm{p}$$의 좌표가 왜 이러한 기하학적 의미를 부여할까? 

### **이제 조금은 뜬금없는 함수\(**$$f$$**\)를 하나 살펴보자.** 

* $$f\left( \begin{bmatrix} x \\ y \\ z \end{bmatrix} \right)  = \text{det}\left( \begin{bmatrix} x&v_1&w_1\\   y&v_2&w_2\\ z&v_3&w_3\end{bmatrix} \right) $$ 
  * $$\bm{v}$$와 $$\bm{w}$$는 constant. $$[x \ \ y \ \ z]^\top$$는 variable. 
* **입력**:  3차원 벡터 $$[x \ \ y \ \ z]^\top$$
* **출력**: 3개의 column으로 이루어진 parallelepiped의 부피. \(숫자\) 
* 아래 그림 **\[Fig. A\]** 참조. 

![\[Fig. A\] &#xB450;&#xBC88;&#xC9F8;, &#xC138;&#xBC88;&#xC9F8; column&#xC740; &#xACE0;&#xC815;&#xB41C; &#xC0C1;&#xD0DC;&#xC5D0;&#xC11C;, &#xCCAB;&#xBC88;&#xC9F8; column&#xB9CC; &#xC790;&#xC720;&#xB86D;&#xAC8C; &#xC6C0;&#xC9C1;&#xC774;&#xACE0; &#xC788;&#xB2E4;.](../../.gitbook/assets/cross_product.gif)

### **함수** $$f$$**는 linear하다. 왜 그런지 살펴보자.** 

#### 이러한 선형성에 대한 조건은 다음의 질문에 답함으로써 확인할 수 있다.   

* $$[x  \ \ y \ \   z]^\top$$를 선형으로 변화시킬때 **부피**도 선형으로 변화하는가?
  * \(parallelepiped의 부피\) = \(밑면의 넓이\) x \(높이\) 
  * 밑면의 넓이는 상수이므로 신경쓸 필요가 없다. \(높이만 고려하면 됨\) 
  * 이제 이렇게 질문을 바꿀 수 있다. 
* $$[x  \ \ y \ \   z]^\top$$를 선형으로 변화시킬때 **높이**도 선형으로 변화하는가?
  * 높이는 $$[x  \ \ y \ \   z]^\top$$로부터 밑면까지의 최단거리이다. 
  * $$[x  \ \ y \ \   z]^\top$$가 선형으로 움직이면  임의의 평면과의 최단거리도 선형으로 변화한다.
    * 직관으로 충분히 확인 가능하다. 
* **결론**: $$f$$는 선형 변환이다!  

### **그러므로, 함수** $$f$$**는 선형 변환으로 나타낼 수 있다.**  

* \(3차원 $$\rightarrow$$ 1차원\)의 선형변환이므로, \(1 x 3\)행렬과의 multiplication로써 기술할 수 있다. 
* $$f\left( \begin{bmatrix} x \\ y \\ z \end{bmatrix} \right) = [? \ \ ? \ \ ?] \begin{bmatrix} x \\ y \\ z \end{bmatrix} $$

### **그리고, 그 선형 변환은 dot product로 나타낼 수 있다. \(duality\)**

* 즉,  $$ [? \ \ ? \ \ ?] \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} ? \\ ? \\ ? \end{bmatrix} \cdot \begin{bmatrix} x \\ y \\ z \end{bmatrix}$$
* 이때 선형변환의 dual이 되는 **미지의 벡터** $$\begin{bmatrix} ? \\ ? \\ ? \end{bmatrix}$$ **를** $$\bm{p}$$**라고 하자**.  
  * \(스포\) 이 벡터는 위에 선행단계에서의 $$\bm{p}$$와 결국 같게 된다. 

### **이제 다음과 같이 쓸 수 있다.** 

* $$f\left( \begin{bmatrix} x \\ y \\ z \end{bmatrix} \right) = \begin{bmatrix} p_1 \\ p_2 \\ p_3 \end{bmatrix} \cdot \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \text{det}\left( \begin{bmatrix} x&v_1&w_1\\   y&v_2&w_2\\ z&v_3&w_3\end{bmatrix} \right) $$ **\[Eq. B\]**
* duality로부터 얻을 수 있는 이같은 viewpoint에서 새로운 기하학적 해석이 가능해진다. 
* 본격적으로 기하학적 의미를 살피기 전에 이 식의 **계산적 의미**를 좀 더 짚고 넘어가자. 

#### 사실 미지의 벡터는 cross product와 계산상으로 동일하다! \(~~짜잔~~\)

* **\[Eq. B\]**에서 dot product와 determinant를 풀어보면 다음과 같다.  
  * $$p_1x + p_2y + p_3z = x(v_2 w_3-v_3 w_2 ) +  y(v_3 w_1-v_1 w_3 ) + z(v_1 w_2-v_2 w_1 )$$
* 변수에 곱해진 좌우변의 상수들을 매칭하면 다음과 같다. 
  * $$\begin{cases} p_1=v_2w_3-v_3w_2 \\ p_2=v_3w_1-v_1w_3 \\  p_3=v_1w_2-v_2w_1  \end{cases}$$
* 어디서 많이 본 것 같다. 이 결과는 좀전의 **선행단계**에서 살펴봤던 $$\bm{p}$$와 **완전히 동일**하다! 
  * **\[Eq. A\]**를 만족하는 $$\bm{p}$$는 **\[Eq. B\]**도 만족한다! 
* 그런데 이건 이미 확인한 수식이 아닌가? 결국 똑같다면 왜 이런 짓을 하는가? 
  * 같은 현상을 다른 관점으로 해석하기 위해서이다. 

### **Dot product와의 연관성은 우리에게 기하학적 해석의 단초를 제공한다!** 

* 우리는 이제 $$\bm{p}$$를 해석할 수 있는 다른 perspective\(**\[Eq. B\]**\)를 가지게 된 것이다. 
* 다음 식의 의미를 다시 분석해보자. 
  *  $$\begin{bmatrix} p_1 \\ p_2 \\ p_3 \end{bmatrix} \cdot \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \text{det}\left( \begin{bmatrix} x&v_1&w_1\\   y&v_2&w_2\\ z&v_3&w_3\end{bmatrix} \right) $$ 

#### **우변의 의미는 이미 알고있다.**

* \[Fig. A\]와 정확히 같은 상황. 
* 3개의 column이 만들어내는 **parallelepiped의 부피**이다. 
* 단, $$[x \ \ y \ \ z]^\top$$는 variable\(흰색\) /$$\bm{v}$$\(주황\)와 $$\bm{w}$$\(분홍\)는 constant. **\[Fig. B\]**
* 부피값은 basis vector들이 오른손 법칙을 따르지 않을 경우, 음수임도 잊지말자. 

![\[Fig. B\]](../../.gitbook/assets/cross_product2.gif)

#### **새로운 것은 좌변이다.** 

* 좌변에 새롭게 $$\bm{p}$$가 등장했다. 
* 우변에 해당하는 값을 dot product를 통해 재해석하고 있다. 
  * $$\bm{p}$$는 constant이며, 우리가 구하고자 하는 특정 벡터이다. 
* **우변과 같아지기 위한** $$\bm{p}$$**\(빨간\)의 성질:**  
  * $$[x \ \ y \ \ z]^\top$$\(흰색\)와의 dot product가 **parallelepiped의 부피**를 나타내야 함.  

#### **이러한 성질을 만족하는** $$\bm{p}$$**는 무엇일까?**

* 바로 parallelepiped의 **밑변에 대해 수직인 벡터**\(빨강\)이다!  
  * ![](../../.gitbook/assets/image%20%28123%29.png)
* **\(좌변의 dot product\)** = \(1. $$\bm{p}$$의 길이\)$$\times$$\(2. $$\bm{p}$$에 대한 $$[x  \ \ y \ \   z]^\top$$의 정사영의 길이\) 
* **\(우변의 determinant\)** = \(1. parallelepiped의 밑변 넓이\) $$\times$$\(2. parallelepiped의 높이\) 
* 좌우변의 1, 2를 매칭시키면: 
  1. \($$\bm{p}$$의 길이\) = \(parallelepiped의 밑변 넓이\)  $$\cdots \raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {1}}} $$
  2. \($$\bm{p}$$에 대한 $$[x  \ \ y \ \   z]^\top$$의 정사영의 길이\) = \(parallelepiped의 높이\) 
* $$\bm{p}$$에 대한 정사영이 항상 도형의 높이가 되려면? 
  *  $$\bm{p}$$는 밑면\($$\bm{v}$$와 $$\bm{w}$$가 이루는 평면\)과 수직이어야 함.  $$\cdots \raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {2}}} $$ 
* \($$\raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {1}}}  + \raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {2}}} $$\) : 우리가 처음에 배웠던 기하학적 설명과 일치한다!  **\(완료\)**

### 간단히 소화시켜 이해해보자.

cross product를 왜 3차원 determinant의 형식으로 구할까?

#### 두 벡터와 또 다른 자유벡터가 이루는 parallelepied의 부피를 생각해보자.

* 부피 = \(두 벡터가 이루는 고정된 밑면 넓이\) x \(자유벡터에 의해 변화하는 높이\) 

#### 이를 자유벡터와의 dot product로 표현할 수 있는 특정벡터를 찾아보자. 

* 두 벡터간 cross product가 유일하다! 
  * 두 벡터가 이루는 면적을 길이로 하고, 수직 방향으로 뻗은 벡터 
* \(dot product\) = \(자유벡터에서 cross product로의 정사영\) x \(cross product의 길이\) 
  * \(자유벡터와 cross product간의 정사영\) = \(parallelepiped의 높이\)
  * \(cross product의 길이\) = \(parallelepiped의 밑면 넓이\) 

#### 특정벡터를 직관적으로 이야기하면?

* 내적으로 부피를 구할 수 있도록 하는 높이측정의 기준벡터. 
  * 키를 잴때 반듯이 측정하도록 도와주는 벽같은 존재. \(지면과 수직\) 

#### 즉, 다음 등식이 성립한다. 

* \(자유벡터와의 **dot product**\) = \(두벡터와 제유벡터가 이루는 **parallelepiped의 부피**\)

**이 등식을 만족시키는 유일한 솔루션이 cross product!**

* cross product를 구하는 과정이 **3차원 부피**와 관련이 있게 되는 이유.
* 두 벡터의 성분 조합으로 표현되는 cross product의 좌표가 나옴.
* 이 좌표를 바로 읽기 편하도록 trick을 쓴 것이 우리가 배우는 공식.

