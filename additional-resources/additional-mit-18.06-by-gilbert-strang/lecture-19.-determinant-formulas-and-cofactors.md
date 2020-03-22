# Lecture 19. Determinant Formulas and Cofactors

## Introduction

* **이 강의의 목표:** 행렬식을 구하는 공식에 대해 배우기 
* 지난 강의에서 행렬식은 elimination을 수행한 다음, pivot을 모두 곱해주면 구할 수 있다고 배웠다.
* 이 강의에서는 동일한 절차를 표현하는 또 다른 방법, 즉, **다음 두 종류의 공식**에 대해 알아보자.  
  * **Big formula** \(Prof. Strang께서 부르시는 이름이다\)
  * **Cofactor formula** \(위 식과 동일하지만 좀 더 편리하게 계산 및 표현 가능\)
* 소거를 통해서 구하는 방법이 algorithm이라면, 공식을 통해서 구하는 방법은 algebra이다. 

## Formula for $$\det A$$ 

### \(2 x 2\) 행렬에서부터 출발해보자.  

#### \(2 x 2\) 행렬의 행렬식은 지난 강의에서 배운 property들에 의해 다음과 같이 분해될 수 있다. 

* Property \(3\)의 각 row별 덧셈에 대한 선형성을 이용하여 여러개의 행렬식으로 분해한다.
* Property \(6\) + \(10\)에 의하여 분해된 상당수의 행렬식\(zero column을 갖는\)은 0이 된다.
* Property \(2\)를 이용하여 열교환을 통해 diagonal하게 만들어준다. \(부호도 잘 바꾸어 준다.\) 
* Property \(7\)을 이용해 대각원소의 곱을 사용하여 determinant를 구해준다. 

$$\begin{aligned}\det A=\begin{vmatrix} a&b\\c&d\end{vmatrix} &\stackrel{(3)}{=}{\begin{vmatrix}  a&0\\c&d\end{vmatrix}}+\begin{vmatrix} 0&b\\c&d\end{vmatrix}\\&\stackrel{(3)}{=}\cancel{\begin{vmatrix} a&0\\c&0\end{vmatrix}}+\begin{vmatrix} a&0\\0&d\end{vmatrix}+\begin{vmatrix} 0&b\\c&0\end{vmatrix}+\cancel{\begin{vmatrix} 0&b\\0&d\end{vmatrix}} \\&\stackrel{(2)}{=}\begin{vmatrix} a&0\\0&d\end{vmatrix}-\begin{vmatrix} c&0\\0&b\end{vmatrix}\stackrel{(7)}{=}ad-bc\end{aligned}$$

* 총 4개의 행렬식으로 분해되었고 그 중에 2개가 non-zero이다. 
* 최종적으로 다음과 같이 일반화될 것이다: 
  * $$n^n$$개의 행렬식으로 분해되었고, 그 중에 $$n!$$개가 non-zero이다. 
  * 위의 예시는 $$n=2$$\(행/열의 개수\)일때에 해당한다. 

#### 분해과정을를 일반화하면 다음과 같다:

* 1개의 행렬식의 첫번째 row를 $$n$$개로 분리: $$n$$개의 행렬식
* $$n$$개의 행렬식의 두번째 row를$$n$$개로 분리: $$n^2$$개의 행렬식 
* $$n^2$$개의 행렬식의 세번째 row를 $$n$$개로 분리: $$n^3$$개의 행렬식
*                                                  ...
* $$n^n$$개의 행렬식의 $$n-1$$번째 row를 $$n$$개로 분리: $$n^n$$개의 행렬식 

#### 분해결과는 다음과 같은 특징이 있다: 

* $$n^n$$개의 행렬식은 각 행에서 하나씩 총$$n$$개의 non-zero element를 갖는다. 
* $$n^n$$개의 행렬식 중의 같은 행이나 열이 모두 0인 경우는 그 값이 0이다.

### \(3 x 3\) 행렬의 경우로 확장해보자. 

#### 위의 관찰결과를 기반으로 \(3 x 3\)행렬을 가지고 좀 더 formalize해보자. 

* 이번에는 0이 되는 항은 어차피 소거될 것이므로 미리 배제해보자.
* 나머지는 \(2 x 2\) 행렬과 같은 절차를 따르면 된다. 

$$\begin{aligned} \det A=\begin{vmatrix} a_{11}&a_{12}&a_{13}\\a_{21}&a_{22}&a_{23}\\a_{31}&a_{32}&a_{33}\end{vmatrix} &=\begin{vmatrix} a_{11}&0&0\\0&a_{22}&0\\0&0&a_{33}\end{vmatrix}+\begin{vmatrix} a_{11}&0&0\\0&0&a_{23}\\0&a_{32}&0\end{vmatrix}+\begin{vmatrix} 0&a_{12}&0\\a_{21}&0&0\\0&0&a_{33}\end{vmatrix} \\  & \quad+ \begin{vmatrix} 0&a_{12}&0\\0&0&a_{23}\\a_{31}&0&0\end{vmatrix} +\begin{vmatrix} 0&0&a_{13}\\a_{21}&0&0\\0&a_{32}&0\end{vmatrix} +\begin{vmatrix} 0&0&a_{13}\\0&a_{22}&0\\a_{31}&0&0\end{vmatrix} \\&=a_{11}a_{22}a_{33}-a_{11}a_{23}a_{32}-a_{12}a_{21}a_{33} \\ & \quad +a_{12}a_{23}a_{31}+a_{13}a_{21}a_{32}-a_{13}a_{22}a_{31}\end{aligned}$$

* 0이 되는 항을 제외하기 위하여 각 행에서 각기 다른 열을 선택하였다. 
  * 3개의 행에서 하나라도 중복되는 열을 선택하면 바로 zero column이 생긴다. 
* diagonal에 원소를 배치하기위한 열교환의 개수를 고려하여 각 항의 부호를 결정한다.

### \(n x n\) 행렬의 경우로 일반화한 공식: Big formula!

* 위의 예시들을 임의의 크기의 정방행렬에 대하여 일반화해보자. 
* 이 공식을 Strang 교수님은 _Big formula_라고 부르신다. \(단어 Big을 참 좋아하시는 듯.\)  

{% hint style="info" %}
**Big formula for determinant A**

* \*\*\*\*$$\det A=\sum_{(\alpha, \beta, \gamma, \cdots ,\omega)} \pm a_{1\alpha}a_{2\beta}a_{3\gamma}\cdots a_{n\omega}$$
  * $$(\alpha, \beta, \gamma, \cdots ,\omega)=\text{Permutation of }(1,2,3,\cdots ,n)$$
  * 즉, 총 term의 개수는 permutation\(순열\)의 경우의 수인 $$n!$$이다. 
  * term의 부호는 대각행렬을 만들기 위해 필요한 행교환의 횟수가 $$k$$일때: $$(-1)^k$$
* \*\*\*\*$$n!$$**개의 항으로 분해한 다음, 행교환을 통해 대각원소의 곱으로써 개별 행렬식을 구한다.** 
{% endhint %}

## Cofactor로 표현하는 방법을 알아보자. 

#### Big formula를 전개한 다음, 최상단 row로 묶어보자. 

* $$\det A={\color{red}a_{11}}\underbrace{\color{blue}(a_{22}a_{33}-a_{23}a_{32})}_{\text{cofactor of }a_{11}}+{\color{red}a_{12}}\underbrace{\color{blue}(-a_{21}a_{33}+a_{23}a_{31})}_{\text{cofactor of }a_{12}}+{\color{red}a_{13}}\underbrace{\color{blue}(a_{21}a_{32}-a_{22}a_{31})}_{\text{cofactor of }a_{13}}$$
*  Underbrace로 표시한바대로, 괄호 안의 숫자를 $${\color{red} a_{11}}, {\color{red}a_{12}},{\color{red}a_{13}}$$의 **cofactor\(여인수\)**라고 부른다. 
* 여기서 어떤 인수로 묶느냐에 따라, 다른 식으로도 표현될 수 있었음을 기억하자. 
  * 두번째, 세번째 row의 원소들이 괄호 앞에 올 수도 있었다. 

#### Cofactor는 원래 행렬에 포함된 한 사이즈 작은 부분행렬\(submatrix\)의 행렬식과 같다. 

* Big formula를 만들때 최상단 row의 원소를 선택하면 동일 행과 열은 더이상 선택하지 않았다. 
* 이때 남은 원소들로 구성된 부분행렬식에서 부호만 잘 맞추어주면 cofactor를 만들 수 있다.  
* $$\begin{vmatrix} {\color{red}a_{11}} & \text{---} & \text{---}\\|&\color{blue}a_{22}&\color{blue}a_{23}\\|&\color{blue}a_{32}&\color{blue}a_{33}\end{vmatrix}-\begin{vmatrix}  \text{---} & {\color{red}a_{11}} & \text{---}\\  \color{blue}a_{21}&|&\color{blue}a_{23}\\\color{blue}a_{31}&|&\color{blue}a_{33}\end{vmatrix}+\begin{vmatrix}  \text{---}  & \text{---}& {\color{red}a_{13}}\\  \color{blue}a_{21}&\color{blue}a_{22}&|\\\color{blue}a_{31}&\color{blue}a_{32}&|\end{vmatrix}$$
* 두번째 cofactor는 음수화를 시켜주어야 big formula와 일치함을 주목하자 \(일반 규칙은 아래에서\) 
* cofactor는 꼭 첫번째 row에 대해서 구할 필요는 없다. \(어떻게 묶던 전개한 결과는 동일\)

#### 정리해보자. 

* $$a_{ij}$$의 cofactor $$C_{ij}$$는 row $$i$$행과 $$j$$열을 지운 행렬의 determinant!
* $$C_{ij}$$의 부호는 $$i+j$$가 짝수이면 양수, 홀수이면 음수. 
  * $$\begin{vmatrix}  \color{red}+&\color{blue}-&\color{red}+&\color{blue}-&\cdots\\\color{blue} -&\color{red}+&\color{blue}-&\color{red}+&\cdots\\ \color{red}+&\color{blue}-&\color{red}+&\color{blue}-&\cdots\\ \vdots&\vdots&\vdots&\vdots&\ddots  \end{vmatrix}$$
* \[참고\] 부호를 붙여주기 전의 cofactor를 **minor\(소행렬식\)**라고 부른다. 

#### Cofactor formula \(along row 1\)

* $$\det A={\color{red}a_{11}}{\color{blue}C_{11}}+{\color{red}a_{12}}{\color{blue}C_{12}}+\cdots+{\color{red}a_{1n}}{\color{blue}C_{1n}}$$ 
* Cofactor의 부호는 그 값 자체에 built-in되어있는 것으로 식에서는 드러나지 않는다. 
* 수식적으로는 big formula를 다시 쓴 것에 불과하다.
* 그러나, 소행렬식의 개념이 들어감으로써 보다 systematic한 계산을 도와준다. 

{% hint style="info" %}
**Cofactor formula \(along row** $$i$$\)

* $$\det A={\color{red}a_{i1}}{\color{blue}C_{i1}}+{\color{red}a_{i2}}{\color{blue}C_{i2}}+\cdots +{\color{red}a_{in}}{\color{blue}C_{in}}$$
* 어떤 row나 column을 기준으로 표현해도 결과는 동일. 
  * 0이 많은 row/column을 선택하면 계산이 편리. 
{% endhint %}

#### 이러한 cofactor formula를 반복 적용하면 한단계씩 sub-determinant의 사이즈를 줄여갈 수 있다.

* 결국 $$n\times n$$행렬식은 $$1\times 1$$행렬식으로 분해되어 표현가능 하다. 
* 가장 작은 cofactor formula는 $$2\times 2$$행렬식에 대한 것이다.
  * $$\begin{vmatrix}a&b\\c&d\end{vmatrix}={\color{red}a}({\color{blue}+|d|})+{\color{red}b}({\color{blue}-|c|})=ad-bc$$

## Tridiagonal matrix의 determinant를 구해보자. 

* Diagonal을 중심으로 총 3개의 원소가 1인 tridiagonal matrix\(3중대각행렬\)의 행렬식을 알아보자. 
* 지금 이 행렬 자체가 중요하다기 보단,  formula를 적용해볼 수 있는 **하나의 예시**로 생각하자.  

#### 차원을 늘려가며 행렬식의 규칙을 찾아보자. 

* $$A_1=\begin{bmatrix} 1\end{bmatrix}, A_2=\begin{bmatrix} 1&1\\1&1\end{bmatrix},A_3=\begin{bmatrix} 1&1&0\\1&1&1\\0&1&1\end{bmatrix},A_4=\begin{bmatrix} 1&1&0&0\\1&1&1&0\\0&1&1&1\\0&0&1&1\end{bmatrix}$$
* $$|A_1|=1, |A_2|=0, |A_3|=-1$$
* $$|A_4|=\underbrace{{\color{red}1}\cdot {\color{blue} |A_3|}}_{(1)}-\underbrace{{\color{red}1}\cdot{\color{green}|A_2|}}_{(2)}$$
  * \(1\) $$\begin{bmatrix} \color{red}\fbox1&1&0&0\\1&\color{blue}1&\color{blue}1&\color{blue}0\\0&\color{blue}1&\color{blue}1&\color{blue}1\\0&\color{blue}0&\color{blue}1&\color{blue}1\end{bmatrix}$$ \(2\) $$\begin{bmatrix} 1&\color{red}\fbox1&0&0\\ \color{blue}1&1&\color{blue}1&\color{blue}0\\\color{blue}0&1&\color{blue}1&\color{blue}1\\\color{blue}0&0&\color{blue}1&\color{blue}1\end{bmatrix}\rightarrow \begin{bmatrix}  \color{red}\fbox1&\color{blue}1&\color{blue}0\\\color{blue}0&\color{green}1&\color{green}1\\\color{blue}0&\color{green}1&\color{green}1\end{bmatrix}$$ 
  * \(2\)에서 2중 sub-determinant를 구할때는 **첫번째 열을 기준**으로 한다. \(0이 더 많아서 계산 용이\)  

#### 계속 차원을 늘려나가도 tridiagonal의 형태는 같으므로 계속 다음 식을 만족하는 것을 알 수 있다. 

* $$|A_n|=|A_{n-1}|-|A_{n-2}|$$

#### 계속 차원을 늘려가며 행렬식을 구하면 6의 주기를 가지고 그 값이 반복됨을 알 수 있다. 

* $$|A_1|=\red1, |A_2|=\red0, |A_3|=\red{-1},|A_4|=\red{-1},|A_5|=\red0,|A_6|=\red1,$$ 
* $$|A_7|=\red1, |A_8|=\red0, |A_9|=\red{-1},|A_10|=\red{-1},|A_{11}|=\red0,|A_{12}|=\red1,\cdots$$ 

