# Lecture 18. Properties of Determinants

## Introduction

* Determinant는 **정사각행렬에만 해당하는 개념**이다!
  * Determinant는 모든 square matrix가 가지는 **숫자**이다. 
  * 정사각행렬을 숫자로 매핑하는 함수라고 볼 수 있다. 
* 우리가 determinant를 필요로 하는 큰 이유는 eigenvalue 때문. 
  * 나중에 알아보도록 하자. 
* 하나의 숫자가 전체 행렬을 대표할 순 없지만 최대한 많은 정보를 함축하고 있다. 
  * determinant가 0이 아닐때만 invertible matrix이다.  
  * determinant가 0이면 singular matrix이다. 
* Determinant는 다음과 같이 표기한다: $$\text{det }A=\vert A \vert$$

#### 이번 lecture의 목표는 determinant의 10가지 특성에 대해 알아보는 것이다. 

* 처음 세가지 property \(1-3\)에 의해 나머지 property\(4-10\)들은 유도가능. 
  * 앞으로의 강의들에서 계속 활용되므로 어떤 녀석이 몇번인지 기억해놓으면 좋다.  
* 강의에는 당장 언급하지 않지만만, **면접/부피변화율로써의 관점**을 학습하는 것이 중요하다.
  * Lec. 20.에서 언급되지만, 지금 알아두는 것이 더 좋다고 생각한다.  
  * 아래에 링크된 페이지를 참조하자. \(페이지 가장 마지막 소제목\) 

{% page-ref page="../../additional-essence-of-linear-algebra-by-3blue1brown/additional-essence-of-linear-algebra-by-3blue1brown.md" %}

## 10 Properties of Determinants

### **\(1\) 항등행렬의 determinant는 1이다:** $$\text{det }I=1$$\*\*\*\*

* $$\begin{vmatrix} 1&0\\0&1\end{vmatrix}=1$$\*\*\*\*

### **\(2\) 행을 교환하면 determinant의 부호가 바뀐다.** 

* $$\text{det }P=\begin{cases} 1 \text{ when number of  permutation is even.} \\ -1 \text{ when number of  permutation is odd.}\end{cases}$$
* $$\begin{vmatrix} 0&1\\1&0\end{vmatrix}=-1$$

### **\(3\) 하나의 열에 대해서는 선형성을 갖는다.**

* \(a\)$$\begin{vmatrix} ta&tb\\c&d \end{vmatrix}=t\begin{vmatrix} a&b\\c&d \end{vmatrix}$$
* \(b\) $$\begin{vmatrix} a+a'&b+b'\\c&d \end{vmatrix}=\begin{vmatrix} a&b\\c&d \end{vmatrix}+\begin{vmatrix} a'&b'\\c&d \end{vmatrix}$$ 
* $$\text{det }(A+B) \neq \text{det }A + \text{det } B$$

#### 다음을 유의하라.

* $$\det 2A=2^n \det A $$\($$\neq 2\det A$$\)
* 모든 row에 대해서 2배를 하는 것과 같으므로, row개수만큼 제곱해줘야 한다.

#### 면적/부피 변화율로 생각해보자. 

* 3차원 상자의 한변을 일정 길이만큼 늘리면, 그만큼의 또 다른 상자를 stack한 부피와 같다. 
* 3차원 상자의 한변만 2배로 늘리면 부피는 $$2$$배 늘어난다. 
* 3차원 상자의 모든 변을 2배로 늘리면, 부피는 $$2^3$$배 늘어난다. 

### **\(4\) 두 개의 row가 같으면 determinant는 0이다.**  

* 그 두개의 row를 교환해도 같은 행렬이므로 determinant는 같아야 함.
* 그러나 동시에, \(2\)에 의해 determinant의 부호는 바뀌어야함.
* 부호가 바뀌어도 값이 변하지 않는 값은 0뿐이다. 
* 다른 설명: 정방행렬이 full rank를 갖지못하면 free variable이 존재한다. 
  * 찌부러지는 차원이 하나라도 있으면 determinant는 0이다. 

### **\(5\) Elimination step의 row operation은 determinant를 바꾸지 않는다.** 

* \(3\)과 \(4\)를 이용하면 증명가능 
  * $$\begin{vmatrix} a & b \\ c-la & d-lb\end{vmatrix}\stackrel{(3)}{=}\begin{vmatrix} a & b \\ c & d\end{vmatrix}-l\begin{vmatrix} a & b \\ a & b\end{vmatrix}\stackrel{(4)}{=}\begin{vmatrix} a & b \\ c & d\end{vmatrix}-l\cdot0=\begin{vmatrix} a & b \\ c & d\end{vmatrix}$$
* 결과적으로 elimination의 전체 과정은 determinant를 바꾸지 않는다. 
  * $$\text{det }A=\text{det }U$$ 

### **\(6\) Zero row가 존재하면 determinant는 0이다.** 

* \(3-a\) 이용: $$\begin{vmatrix} 0\cdot a&0\cdot b\\c&d \end{vmatrix}=0\begin{vmatrix} a&b\\c&d \end{vmatrix}=0$$ 

### **\(7\) Upper triangular matrix의 determinant는 대각원소\(pivot\)들의 곱이다.** 

* $$\text{det }U=\begin{vmatrix} d_1 & *&\cdots&*\\0&d_2&\cdots&*\\\vdots&\vdots&\ddots&\vdots\\0&0&\cdots&d_n \end{vmatrix}=d_1d_2\cdots d_n$$
* MATLAB에서 행렬의 determinant를 구하는 방법: 소거 후에 U를 만들고 대각원소를 곱한다. 
* 단, row exchange가 있었다면, 2번에 의해 부호를 결정한다. 

#### \[주의\] 만약 pivot을 1을 만들기 위해 row를 나누어주었다면?

*  \(3\)에 의해 전체 determinant에 같은 수를 곱해주어야 한다. 

#### \[주의\] 만약 row exchange가 있었다면? 

* \(2\)에 의해 부호를 결정한다.

#### 위 공식을 증명해보자. 

* \(5\)에 의해 backward elimination을 해도 determinant는 유지된다는 것을 보장할 수 있다. 
* Backward elimination을 통해 대각행렬로 만든 후, \(3\)과 \(1\)을 이용하여 아래와 같이 증명가능하다: 
* $$\text{det }D=\begin{vmatrix} d_1 & 0&\cdots&0\\0&d_2&\cdots&0\\\vdots&\vdots&\ddots&\vdots\\0&0&\cdots&d_n \end{vmatrix}\stackrel{(3)}{=}d_1d_2\cdots d_n\begin{vmatrix} 1 & 0&\cdots&0\\0&1&\cdots&0\\\vdots&\vdots&\ddots&\vdots\\0&0&\cdots&1 \end{vmatrix}\stackrel{(1)}{=}d_1d_2\cdots d_n$$ 

#### 우리가 흔히 알고 있던 2차원 행렬에 대한 행렬식과 비교해보자. 

* $$\begin{vmatrix} a&b\\c&d\end{vmatrix}\stackrel{E}{\rightsquigarrow}\begin{vmatrix} a&b\\0&d-\dfrac{c}{d}b\end{vmatrix}\stackrel{(7)}{=}ad-bc$$ \(일치\) 

### **\(8\)**$$A$$**가 singular matrix이면,**$$\text{det }A=0$$**이다.** 

#### \(= $$A$$의 역행렬이 존재하면, $$\text{det }A\neq0$$ 이다.\)

* 역행렬이 존재하는지\(Invertibility\)의의 테스트로써 사용할 수 있다!

#### 증명해보자. 

* Singular matrix를 가지고 \(7\)에서의 증명과정을 진행해보자. 
* 두번째 등호 다음의 determinant에서 zero row가 등장한다.
* \(6\)에 의해서 determinant는 0이 된다. 

#### \(4\)에서 언급했듯이 singular matrix는 $$\bm{0}$$아닌 원소가 nullspace에 존재한다. 

* 찌부러지는 차원이 존재하고, determinant도 0이다. 

### \(9\) $$\text{det }AB=(\text{det }A)(\text{det }B)$$ 

* 직관적인 의미는 위에서 link했던 page를 참조하자. \(면적/부의 변화율로 이해하자.\) 

#### 이 공식을 이용하면 다음 식들을 유도할 수 있다.

*  $$\text{det } A^{-1}=1/\text{det } A$$
  * $$\text{det }A^{-1}A=\text{det }I$$이므로, $$(\text{det }A^{-1}) (\text{det }A)=1$$
  * 역시 면적/부의 변화율로 이해한다면, 변화율의 반대는 multiplier의 역수가 된다. 
  * $$\det A=0$$일 경우, 분모가 0이 됨을 주목하라. 
* $$\text{det } A^{2}=(\text{det } A)^2$$ 

### \(10\) $$\det A^\top=\det A$$ 

* 이 공식에 의하여, 위의 모든 row 관련한 특성들이 column에도 그대로 적용될 수 있다. 
* 예를 들어, **row operation 뿐 아니라, column operation도 determinant를 바꾸지 않는다!**

#### 증명해보자. 

* 목표:$$\vert A^\top\vert=\vert A \vert$$임을 보인다.
  * $$\vert U^\top L^\top\vert=\vert LU \vert$$ 
  * $$\vert U^\top \vert \vert L^\top\vert=\vert L \vert \vert U \vert$$ 
  * $$\vert L^\top \vert= \vert L \vert=1$$ and $$\vert U^\top\vert = \vert U \vert$$ 
* \[주의\] Lower/upper 구분없이 모두 대각원소의 곱이 determinant가 된다. 
  * non-zero element가 대각 기준으로 어디에 있던 위에서 설명한 방법으로 똑같이 유도 가능.

## 주요 공식을 한눈에 모아보자. 

{% hint style="info" %}
* $$\text{det }I=1$$
* $$\text{det }A=\text{det }U$$\(when $$A \stackrel{E}{\rightsquigarrow }U$$\)
* $$\text{det }U=\begin{vmatrix} d_1 & *&\cdots&*\\0&d_2&\cdots&*\\\vdots&\vdots&\ddots&\vdots\\0&0&\cdots&d_n \end{vmatrix}=d_1d_2\cdots d_n$$
  * 위 두 공식은 Upper/lower triangular, diagonal matrix 모두 해당! 
* $$\text{det }AB=(\text{det }A)(\text{det }B)$$
* $$\text{det } A^{-1}=1/\text{det } A$$
* $$\text{det } A^{2}=(\text{det } A)^2$$
* $$\det 2A=2^n \det A$$ 
* $$\det A^\top=\det A$$
{% endhint %}

