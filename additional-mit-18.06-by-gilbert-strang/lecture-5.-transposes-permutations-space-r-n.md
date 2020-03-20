# Lecture 5. Transposes, Permutations, Space R^n

### **Permutation**

* 대부분의 내용은 Lecture 4.에서 이미 설명하였다. \(행교환\)
* 추가적으로 **열교환\(column exchange\)** 행렬에 대해 알아보자.  
* **Row permutation**: 행렬의 왼쪽에서 행을 교환
  * ![](../.gitbook/assets/image%20%28140%29.png)
* **Column permutation**: 행렬의 오른쪽에서 열을 교환
  * ![](../.gitbook/assets/image%20%2831%29.png)
  * 그림 출처: [JUDIS.me](http://judis.me/wordpress/2015/09/30/%ec%84%a0%ed%98%95%eb%8c%80%ec%88%98-note-5-transposes-permutations-space-rn/)

### **Transpose** \(역행렬\)

* $$(A^\top)_{ij}=A_{ji}$$

### **Symmetric matrices** \(대칭행렬\)

* **Special, the best** matrices
* $$A^\top=A$$

#### \*\*\*\*$$R^\top R$$**은 항상 대칭행렬이다!**

* $$(R^\top R)^\top = R^\top R $$\*\*\*\*
* $$R^\top R$$의 $$i$$행, $$j$$열의 원소를 $$(R^\top R)_{ij}$$라고 표기하자. 
* **대각 원소**\($$i= j$$\)들은 해당 행의 원소들의 제곱합\(자신과의 dot product\).
* **비대각 원소**\($$i \neq j$$\)들은 $$i$$번째 행과 $$j$$번째 행의 dot product.
  * dot product는 순서에 관계없이 같은 결과: **대칭성** 
  *  $$(R^\top R)_{ij}=R_{i}^\top R_{j}=R_{j}^\top R_{i}=(R^\top R)_{ji}$$
  * $$\begin{bmatrix} \red a & \red c \\b & d \end{bmatrix}\begin{bmatrix} a & \red b \\ c & \red d \end{bmatrix} = \begin{bmatrix} a^2 + c^2 & \red {ab+cd} \\ba+dc & b^2+d^2 \end{bmatrix}$$
  * $$\begin{bmatrix} a & c \\ \green b & \green d \end{bmatrix}\begin{bmatrix} \green a & b \\ \green c & d \end{bmatrix} = \begin{bmatrix} a^2 + c^2 & ab+cd \\ \green{ba+dc} & b^2+d^2 \end{bmatrix}$$ 

### **Vector spaces** \(벡터공간\)

linear combination에 대해 닫혀있는\(closed\) 공간 

* **닫힘\(closure\)**: 공간의 어떤 요소끼리 위의 연산을 해도 다시 그 공간에  떨어짐. 
* 벡터공간의 벡터끼리 더하기 / 스칼라 곱하기의 결과도 여전히 같은 벡터공간의 원소. 
* \(심화\) 더 엄밀한 벡터공간에 대한 공리\(**Axioms of vector spaces**\)가 있음.

#### 벡터 공간의 예:  $$\mathbb{R}^2$$, $$\mathbb{R}^3$$ 

#### 벡터 공간이 아닌 예:

* $$\mathbb{R}^2$$에서 $$\bm{0}$$를 제외하면 벡터공간이 아니다. 
  * 0과의 스칼라곱에 대해 닫혀있지 않음. 
  * **벡터 공간은 무조건 원점\(**$$\bm{0}$$**; 영벡터\)을 포함해야 함.**
* $$\mathbb{R}^2$$의 1사분면은 벡터공간이 아니다. 
  * 음수 스칼라곱에 대해 닫혀있지 않음.
  * 1사분면의 벡터에 음수를 곱하면 다른 세 개의 사분면에 속함. 

### **Subspaces** \(부분공간\)

vector space 안에 존재하는 space \(부분집합; 자기자신 포함.\) 

#### $$\mathbb{R}^2$$의 subspaces

* **\(2차원\)** 전체 공간
* **\(1차원\)** $$\mathbb{0}$$를 통과하는 모든직선
* **\(0차원\)** $$\mathbb{0}$$ \(zero vector only\)

### Column space \(행공간\) 

* 행렬 $$A= \begin{bmatrix} 1 & 3 \\ 2 & 3 \\ 4 & 1 \end{bmatrix}$$의 **column들의 모든 선형조합**도 subspace의 한가지 예다. 
* 이 subspace는 특별히 이름을 갖는다: **column space**! 
* 그리고 이렇게 표기한다: $$\mathcal{C}(A)$$
* 3차원 공간 안에서 2개 벡터의 모든 linear combination이 이루는 평면을 상상해보라! 
  * $$\mathcal{C} \left( \begin{bmatrix} 1 \\ 2 \\ 4  \end{bmatrix}, \begin{bmatrix} 3 \\ 3 \\ 1  \end{bmatrix} \right)$$



