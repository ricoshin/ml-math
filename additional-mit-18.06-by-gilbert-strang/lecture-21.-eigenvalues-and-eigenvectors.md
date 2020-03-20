# Lecture 21. Eigenvalues and Eigenvectors

## Introduction 

* 선형대수의 **매주 중요한 부분**이 이제 시작된다! 
* 나머지 강의의 대부분을 차지하는 하나의 흐름이 시작되므로 마음을 새롭게 해보자. 
* 이번 주제에서도 행렬은 **무조건 정방형\(square\)**이다! 
* **Eigenvalue**\(고유값\)와 **Eigenvector**\(고유벡터\)가 **무엇인지** 알아보자.
  * 다음 강의에서는 어디에 사용하고 왜 필요한지를 알아 알아볼 것. 
* 기하학적 이해를 돕기 위해서 아래 페이지를 참조하자. 

{% page-ref page="../additional-essence-of-linear-algebra-by-3blue1brown/part-7.-e14.md" %}

## Eigenvalue와 Eigenvector는 무엇인가?

### 그 의미를 먼저 알아보자. 

* 행렬 $$A$$가 의미하는 선형변환의 입력은 벡터 $$\bm{x}$$이고 출력은 벡터 $$A\bm{x}$$이다. 
* 선형변환 후에도 그 방향이 바뀌지 않는 모든 입력벡터 $$\bm{x}$$를 **eigenvector**\(고유벡터\)라고 한다. 
  * 이 경우는 매우 **'특별한'** 입력의 부분공간에서만 허락되는 특성이다.
  * 고유벡터의 조건은 '방향'만 일치하면 만족한다. 벡터의 '길이'는 변할 수 있다. 
* 이때 출력벡터의 입력벡터에 대한 길이의 변화율 $$\lambda$$를 **eigenvalue**\(고유값\)이라고 한다! 
* 선형변환$$A$$ 후에도, 방향이 유지되면서 길이만 $$\lambda$$배만큼 변화하는 $$\bm{x}$$를 찾는 것이 우리 목표다!

### 이를 으로 나타나면 다음과 같다:

$$
A\bm{x}=\lambda\bm{x}
$$

* $$\bm{x}=\bm{0}$$는 모든 $$\lambda$$에 대해 위 시스템을 만족하므로, 흥미롭지 않은 trivial solution이다.  
  * 많은 책에서는 zero vector를 eigenvector의 정의에서 제외한다. \([포함하는 책도 있다고 한다.](https://math.stackexchange.com/questions/990016/can-the-zero-vector-be-an-eigenvector-for-a-matrix)\)
  * 우리도 eigenvector를 고려하는 동안 zero vector는 아예 배제하고 생각하도록 하자. 
* $$\lambda$$는 **0**이나 **음수**도 심지어 **허수**도 나올 수 있다.
* 만약, $$A$$가 singular matrix이면, $$\lambda=0$$은 eigenvalue에 포함된다. 
  * Nullspace에 존재하는 non-zero $$\bm{x}$$가 항상 존재하므로, $$\lambda=0$$일때 위 시스템을 만족한다. 
* 이 시스템을 어떻게 풀 수 있을까?
  * $$A\bm{x}=\bm{b}$$의 꼴이 아니므로 elimination을 사용할 수 없다. 
  * 게다가 미지수는 2개이다. 
  * 이 시스템을 풀기 위해서는 새로운 아이디어가 필요하다.  
    * 조금 뒤에 알아보자. 

### 수학적으로 풀기에 앞서 이미 배운 행렬들의 $$\bm{x}$$와 $$\lambda$$들에 대해 생각해보자.

![\[Fig. 1\]](../.gitbook/assets/image%20%28161%29.png)

**Projection matrix** $$P=A(A^\top A)^{-1}A^\top$$_- \[Fig. 1\] 왼쪽 그림_

* $$\bm{x}$$: projection 평면 위에 있는 모든 벡터\($$P\bm{x}=1\cdot \bm{x}$$\) / $$\lambda=1$$ _- 주황_
* $$\bm{x}$$: projection 평면과 수직인 모든 벡터\($$P\bm{x}=0\cdot \bm{x}$$\) / $$\lambda=0$$ _- 빨강_ 

**Permutation matrix** $$P=\begin{bmatrix}0&1\\1&0\end{bmatrix}$$ **** _- \[Fig. 1\] 오른쪽 그림_

* 이 행렬은 $$c\begin{bmatrix} 1 \\ 1 \end{bmatrix}$$를 축으로 대칭이동을 시키는 선형변환을 의미한다. 
* $$\bm{x}$$: 대칭축 위에 있는 모든 벡터\($$\bm{x}=c\begin{bmatrix} 1\\1 \end{bmatrix}$$\) / $$\lambda=1$$ _- 주황_
* $$\bm{x}$$: 대칭축과 수직인 모든 벡터\($$\bm{x}=d\begin{bmatrix} 1\\-1 \end{bmatrix}$$\) / $$\lambda=-1$$ _- 빨강_ 

#### 여기서 뜬금없이 등장하는 중요한 Fact가 있다. 

{% hint style="info" %}
**행렬** $$A$$**의 eigenvalue들의 합은 대각원소들의 합과 같다.** 

* 대각원소들의 합을 **trace**\(대각합\)라고 하고 $$\text {tr}(\cdot)$$로 표기한다. 
* $$\text{tr} (A)=a_{11}+a_{22}+\cdots+a_{nn}$$
{% endhint %}

* 위 permutation 행렬을 테스트해보면 사실임을 확인할 수 있다.
* 일단 당장은 여기까지만 알아두고 넘어가자. 

## Eigenvalue와 Eigenvector를 구하는 방법

#### 우리가 풀어야할 시스템:$$A\bm{x}=\lambda \bm{x}$$

* 다음 예시를 사용할 것이다: $$A=\begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}$$

#### Rewrite: $$(A-\lambda I)\bm{x}=\bm{0}$$

* $$\bm{x}$$를 찾는 일은 $$(A-\lambda I)$$의 nullspace를 구하는 일이다.
* 그러나, 그전에 $$\bm{0}$$이 아닌 nullspace가 존재할 조건을 만족해야한다. 
  * = $$(A-\lambda I)$$가 singular matrix이어야 한다. 
  * = determinant가 zero가 되야한다. 

#### $$\det (A-\lambda I)=0$$

* 이 식을 **characteristic equation** / **eigenvalue equation**이라고 부른다. 
* $$\bm{x}$$가 시스템에서 사라지면서 $$\lambda$$만 따로 풀 수 있게 되었다. 
* $$A$$가 $$n\times n$$행렬일때, 이 식의 해가 되는 $$\lambda$$는 $$n$$개 존재한다. 
  * 단, $$\lambda$$가 중복되는 해를 가질 수 있다. \(중근\) 

#### 방정식을 풀어서, $$\lambda$$를 구해보자! 

* $$\begin{aligned}\text{det }(A-\lambda I)&=\begin{vmatrix} 3-\lambda & 1 \\ 1& 3 -\lambda\end{vmatrix}=(3-\lambda)^2-1\\&=\lambda^2-{\color{red}6}\lambda+{\color{blue}8}=(\lambda-4)(\lambda -2)\end{aligned}$$
* 2차원 행렬이므로 2차방정식이 만들어짐에 따라, 2개의 eigenvalue가 나왔다. 
  * $$\lambda_1=4,  \ \lambda_2=2$$
* \[잠깐\] 여기서 중요한 사실이 또하나 드러났다!
  * **두 고유값의 합인** $$\color{red}6$$**은 trace**이다. \(위에서 이미 언급\) 
  * **두 고유값의 곱인** $$\color{blue}8$$**은 determinant**이다. 

{% hint style="info" %}
* 행렬의 **trace**는 고유값들의 **합**과 같다.
* 행렬의 **determinant**는 고유값들의 **곱**과 같다. 
{% endhint %}

#### 구한 $$\lambda$$를 위 식에 최초의 식에 하나씩 대입하여 nullspace를 구해보자. 

* $$\lambda_1=4$$일때:
  * $$(A-\lambda_1 I)\bm{x}_1=\begin{bmatrix} -1&1\\ 1&-1\end{bmatrix}\bm{x}_1=\bm{0}$$
  * $$\bm{x}_1=c_1\begin{bmatrix} 1 \\ 1 \end{bmatrix}$$
* $$\lambda_2=2$$일때:
  * $$(A-\lambda_2 I)\bm{x}_2=\begin{bmatrix} 1&1\\ 1&1\end{bmatrix}\bm{x}_2=\bm{0}$$
  * $$\bm{x}_2=c_2\begin{bmatrix} 1 \\ -1 \end{bmatrix}$$

## Eigenvalue와 Eigenvector가 우리에게 말해주는 것은? 

### 위에서 살펴본 예시 중 두개의 행렬의 고유값, 고유벡터를 비교해보자. 

|  | Matrix 1 | Matrix 2 |
| :---: | :---: | :---: |
| Matrix | $$A=\begin{bmatrix}0&1\\1&0\end{bmatrix}$$  | $$A'=\begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}$$  |
| Eigenvalues | $$\lambda_1 =1 ,  \quad \lambda_2 =-1$$ | $$\lambda'_1 =4 ,  \quad \lambda'_2 =2$$  |
| Eigenvectors | $$\bm{x}_1=\begin{bmatrix}1\\1\end{bmatrix}, \quad \bm{x}_2=\begin{bmatrix}-1\\1\end{bmatrix}$$ | $$\bm{x}'_1=\begin{bmatrix}1\\1\end{bmatrix}, \quad \bm{x}'_2=\begin{bmatrix}-1\\1\end{bmatrix}$$  |

#### 다음과 같은 사실을 발견할 수 있다:

* 두 행렬은 다음 관계를 갖는다: $$A'=A+3I$$\(대각원소들에 3을 더한 결과\)
* 두 행렬의 eigenvector는 똑같다. \($$\bm{x}=\bm{x}'$$\)
* 두 행렬의 eigenvalue는 다음 관계를 갖는다: $$\lambda'=\lambda+3$$
* **즉, 모든 대각원소에** $$c$$**를 더하면, 모든 고유값이** $$c$$**증가한다.** 
  * $$A'\bm{x}=(A+3I)\bm{x}=\lambda \bm{x}+3\bm{x}=(\red{\lambda +3})\bm{x}=\red{\lambda'}\bm{x}$$
* 위에서 언급했던 다음 사실에도 부합되는 명제이다. 
  * "행렬의 trace\(대각원소의 합\)는 고유값들의 합과 같다."
    * 즉, 대각원소의 합이 증가하면, 고유값들의 합도 증가한다. 

#### 그러나 일반적으로 다음은 성립하지 않음에 유의하자:

* $$A\bm{x}=\lambda\bm{x}, \ B\bm{x}''=\lambda''\bm{x}''$$일때, 
  * $$(A+B)\bm{x}\neq(\lambda+\lambda'')\bm{x}$$
* 성립하지 않는 이유?
  * 위 경우와는 달리 두 행렬의 eigenvector가 다르기 때문이다. \($$\bm{x}\neq\bm{x}''$$\)
* 당연히 다음도 성립하지 않는다.
  * $$AB\bm{x}\neq\lambda\lambda''\bm{x}$$ 

### 고유값이 허수를 갖는 경우를 알아보자. 

#### 90도 rotation 행렬의 고유값, 고유벡터를 구해보자. 

* $$A=\begin{bmatrix} \cos90^\circ & -\sin90^\circ\\\sin 90^\circ& \cos 90^\circ\end{bmatrix}=\begin{bmatrix} 0&-1 \\1 & 0 \end{bmatrix}$$
  * $$|A-\lambda I|=\begin{vmatrix} -\lambda & -1\\1 & -\lambda \end{vmatrix}=\lambda^2+1=0$$
  * $$\lambda=\pm i$$ : 고유값이 **허수**가 나왔다! 
* 고유값으로 complex conjugate\(켤레복소수\)나오는 경우는 어떤 의미일까?
  * **고유벡터가 존재하지 않는다**는 뜻이다. 
  * 90도 회전을 거치면 어떤 벡터도 원래 방향을 유지하지 못하기 때문이다. 

#### 행렬 $$A$$는 **anti-symmetric matrix**\(반대칭행렬\)이다.

* 반대칭행렬은 $$A^\top=-A$$의 특징을 갖기때문에, 대각원소로는 0만 가질 수 있다. 
* **항상 허수를 고유값으로 갖는다.** 
* \(TODO\) anti-symmetric과 rotation의 관계?

#### Symmetric matrix\(대칭행렬\)은 반대칭행렬의 반대 극단에 있다. 

* 대칭행렬은 $$A^\top=A$$의 특징을 갖는다.
* 항실 실수를 **고유값으로 갖으며**, **고유벡터는 서로 수직**이다.  
  * 위에서 살펴봤던 permutation matrix가 그 예이다. 
* 고유값은 **symmetric**에 가까워질 수록 **실수**에, **anti-symmetric**에 가까워질수록 **허수**에 가까워진다. 

### 고유값이 중복되는 경우를 알아보자. 

#### 다음과 같은 대각원소가 동일한 triangular matrix의 고유값, 고유벡터를 구해보자.

* $$A=\begin{bmatrix} 3&1 \\0&3 \end{bmatrix}$$
* $$ |A-\lambda I|=\begin{vmatrix} 3-\lambda & 1\\0 & 3-\lambda \end{vmatrix}=(3-\lambda)^2=0$$
  * $$\lambda=3$$: equation이 **중근**을 갖는다!
* **사실 triangular matrix의 대각원소는 eigenvalue이다.** 
  * 갑자기 새로운 사실 하나가 또 뜬금없이 등장했다. 
  * 결론은 위와 같이 방정식을 직접 풀지 않고도 삼각행렬 자체에서 바로 고유값을 읽을 수도 있었다. 
* 중요한 것은 이러한 경우에는 **eigenvector도 하나만 존재**한다는 것이다. 
* 고유벡터가 벡터공간 전체를 span하지 못하는 경우는 이 개념을 활용하는데 문제가 될 수 있다. 
  * 무슨 문제인지는 다음 강의들에서 알아보자. 

{% hint style="info" %}
**헷갈리기 시작한다. 모아서 비교해보자.**

* 모든 행렬의 **trace**는 고유값들의 **합**과 같다. 
* 모든 행렬의 **determinant**는 고유값들의 **곱**과 같다. 
* **삼각**행렬의 **대각원소**들 자신이 바로 **고유값**이다.
* **삼각**행렬의 **대각원소**들의 **곱**은 **determinant**이다. \(redundant\)
{% endhint %}

