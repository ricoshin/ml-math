# Lecture 4: Factorization into A=LU

### **Inverse of** $$AB$$**,** $$A^\top$$**.**

* $$(AB)^{-1}=B^{-1} A^{-1}$$
  * $$ (AB)(B^{-1}A^{-1})=A(BB^{-1})A^{-1}=AA^{-1}=I $$
* $$ (A^\top)^{-1}=(A^{-1})^\top$$ 
  * $$AA^{-1}=I$$  의 양변에 transpose를 하면,
  * $$( AA^{-1})^\top= I^\top=(A^{-1})^\top A^\top=I$$  

### 행렬의 **factorization / decomposition**이란?

* 해가 더 쉽게 드러나도록 하기 위해 방정식을 factorize하는 것과 같다.
* $$x^2-x-12=(x+3)(x-4)$$로 인수분해하면:
  * 계산이 편하다. \(해를 거의 공짜로 구할 수 있다.\)
  * 분석하기 편하다. \(그래프를 그릴 수 있다.\)
* 행렬을 decomposition하는 것도 같은 이유이다. 
* LU decomposition은 다른 많은 분해법\(QR, SVD, etc.\) 중의 하나. 

### **LU decomposition \(LU 분해법\)**

#### Lecture 2의 **Gaussian elimination과 사실상 같은 방법**이다.

* LU 분해하는 과정에서 결국 Gauss elimination이 사용되기 때문이다. 

#### \($$3\times 3$$\) 행렬의 Gaussian elimination을 완료한 상태에서 출발해보자. 

* $$E_{32}E_{31}E_{21}A=U$$

#### 여기서 전체 elementary transformation의 역행렬이$$L$$이 된다.

* $$A=(E_{32}E_{31}E_{21})^{-1}U=E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}U=LU$$
  * $$L=E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}$$

#### **LU분해가 끝나버렸다.** \(허무\) 

* 가우스소거법의 elementary 변환과정에 역행렬을 취해 우변으로 넘기면 끝! 

#### LU분해의 모양을 살펴보자. 

* $$A=LU$$\($$L$$: Lower triangular matrix / $$U$$: Upper triangular matrix\)
* 예시: $$\begin{bmatrix} 2 & 1 \\ 8 & 7 \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 4 & 1 \end{bmatrix}\begin{bmatrix} 2 & 1 \\ 0 & 3 \end{bmatrix}$$
* $$U$$는 elimination의 과정에서 모든 pivot이 존재할 경우 **상삼각**행렬이 됨.
* $$L$$는 row operation이 윗 행의 상수배를 아래 행에 더하기 때문에 **하삼각**행렬이 됨.

#### **굳이 역행렬을 취해서** $$L$$**을 우변에 둘 필요가 있을까? \(** $$L=E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}$$ **\)**

* $$E_{32}E_{31}E_{21}$$: 모두 곱하면 row operation의 **중첩효과**\(10\) 발생. 
  * ![](../../.gitbook/assets/image%20%28105%29.png)
  * **-2**를 곱해서 만든 원소에 다시 **-5**를 곱하면 총 **10**을 곱한 것과 같은 중첩발생. 
  * 전에 있었던 일이 후에 영향을 미침. 
* $$E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}$$ : 모두 곱해도 중첩효과 없음.
  * ![](../../.gitbook/assets/image%20%28167%29.png)
  * 중첩효과의 발생방향의 역순으로 접근.
  * 후에 있었던 일은 전에 있었던 일에 영향을 미치지 않음. 
* 즉, 역행렬을 다루게 되면 multiplier를 그대로 _제자리에 갖다놓기만_ 하면 됨. 

#### 참고사항

* Row exchange가 필요한 경우는 기본 LU분해는 failed! 
  * 곧 배울 PLU 형태로 나타내야함.
* 모든 pivot이 존재하는 경우만 배웠지만, pivot이 없어도 LU분해 자체는 계속 진행 가능. 
* square matrix에 대해서만 배웠지만, non-square\(rectangular\) matrix에도 일반화 가능. 

#### 여기서 좀 더 나아갈 수 있다. 

* LU 분해에서 그치지 않고 더 진행하는 확장판들이 있다.
  * LDU 분해법 \(대각행렬 추가분해\) 
  * PLU 분해법 \(행교환 추가고려\) 
* 다음에서 이 둘에 대해 알아보겠다. 

### LDU Decomposition \(LDU 분해법\) 

* $$A=LDU$$의 형태 \($$D$$: Diagonal matrix\)
* 예시: $$\begin{bmatrix} 2 & 1 \\ 8 & 7 \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 4 & 1 \end{bmatrix}\begin{bmatrix} 2 & 0 \\ 0 & 3 \end{bmatrix}\begin{bmatrix} 1 & 1/2 \\ 0 & 1 \end{bmatrix}$$ 
* \*\*\*\*$$D$$**구하는 법:** LU분해 상태에서 $$U$$의 대각 원소들을 copy. 
* $$U$$**구하는 법:** 기존 $$U$$에서 대각 원소로 같은 열의 원소들을 나눠줌. 

### PLU Decomposition \(PLU 분해법\) 

* LUP 분해라고도 한다. \(LU decomposition with partial pivoting\)
* Elimination  과정 중에 행교환이 필요한 경우에 사용  
* 이러한 행교환을 나타내는 matrix를 **permutation matrix**라고 한다. 

#### 다음과 같은 상황에서는 행교환\(row exchange\)이 필요하다! 

* **zero pivo**t: pivot: 더이상 소거를 진행할 수 없으므로 교환
* **almost zero pivot**: 계산 오차가 커지므로\(numerically bad \) 교환 

#### 우리는 permutation matrix $$P$$를 이용해서 이 또한 표현할 수 있다. 

* identity matrix의 row들의 순서를 바꿔주면 됨.
* $$P = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ 1 & 0 & 0 \end{bmatrix}:  [R_1, R_2, R_3]^\top \Rightarrow [R_2, R_3, R_1] ^\top$$
* $$P^{-1} =  \begin{bmatrix} 0 & 0 & 1 \\ 1 & 0 & 0 \\ 0 & 1 & 0 \end{bmatrix}=P^\top:  [R_1, R_2, R_3]^\top \Leftarrow [R_2, R_3, R_1] ^\top$$
* 역행렬이 transpose와 같다 \($$P^{-1}=P^\top $$\)
  * 이같은 성질을 갖는 다른 행렬들을 나중에 배울 것. **\(특수한 성질\)** 
  * \(스포\) orthogonal matrix\(column들이 서로 수직이고 크기가 1\)의 특징이다. 
* \($$ n \times n $$\) 행렬에서의 가능한 **permutation 경우의 수**: $$n!$$

#### Permutation까지 고려할 경우, PLU 분해가 된다: 

* $$PA=LU$$ 
* $$A=P^\top LU$$_\*\*\*\*_

### _**\(Additional\)**_  **LU 분해법의 활용: 그래서 어디다 쓰냐?** 

* Strang 교수님은 설명 안해주고 넘어가신다.. 
  * Big picture를 그리는 데는 덜 중요한 듯. \(가우스 소거법 자체가 더 중요\)

#### **LU분해를 사용하여\#\#\# Linear system** $$A\bm{x}=\bm{b}$$**의 해를 구할 수 있다.**

* $$A\bm{x}=P^\top LU\bm{x}=\bm{b}$$ 
* $$LU\bm{x} = P\bm{b}$$
* $$U\bm{x}=\bm{y}$$로 놓으면, $$L\bm{y}=P\bm{b}$$

#### 해를 구하는 과정\(2-stage\) 

1. **Forward substitution**\(전진대입\): $$L\bm{y}=P\bm{b}$$를 $$\bm{y}$$에 대해서 푼다. 
2. **Backward substitution**\(후진대입\): $$U\bm{x}=\bm{y}$$를 $$\bm{x}$$에 대해서 푼다.

* $$L$$/ $$U$$는 상삼각/하삼각 행렬이므로 전진/후진대입으로 쉽게 해를 구할 수 있음. 

#### 그러나 여전히 의문은 남는다.

* 어차피 LU분해하는 과정 자체에서 가우스 소거법이 사용된다.
* 가우스 소거법으로도 해를 구할 수 있는데 **굳이 2-stage로 구하는 이유**는?  

#### 그 답은 다음과 같다. 

* 가우스 소거법으로 linear system의 해를 구할때는 augmented matrix를 사용한다. 
  * 즉, $$\bm{b}$$가 elimination 과정에 포함되어 있다.
  * 만약 $$\bm{b}$$가 달라지게 되면 매번 새로운 과정을 반복해야 한다. 
* 그러나, LU분해는 $$\bm{b}$$가 달라져도 걱정이 없다!
  * 일단 한번 분해만 해놓으면 전진/후진 대입만으로 쉽게 해를 구할 수 있다.  

#### LU 분해를  또 다른 목적으로 사용할 수 있을까? 

* inverse와 determinant를 구하는데도 LU분해를 활용할 수 있다. 
* 여기서 이 부분까지 다루기에는 투머치인 듯하다. 
* 다음 기회에 알아보자. 

