# Lecture 20. Cramer's Rule, Inverse Matrix, and Volume

## Formula for $$A^{-1}$$ 

#### 역행렬도 대수적 공식으로 나타낼 수 있다! 

* 지난 강의에서와 같은 포맷이다. 
  * 행렬식을 Gauss elimination을 통해 구할 수 있지만, formula로 나타낼 수 있었다.
* 기존에도 Gauss-Jordan elimination을 통해 역행렬을 구할 수 있었다. **\(Algorithm\)**
* 이를 수학적으로 표현할 수 있는 대수적 shortcut이 존재한다는 이야기다. **\(Algebra\)**  
  * 절차를 하나의 수식으로 '표현'할 수 있다는 점에서 shortcut.
  * 기호의 규약으로 압축적으로 표현한다는 것이 실제 계산비용의 감소를 의미하지는 않음. 
* 역행렬의 formula를 구하는 것은 이어서 배울 **Crammer's rule에 대한 준비단계**로써의 의미가 있다. 

#### 2차원 행렬의 역행렬 공식은 매우 유명하다. 

$$A^{-1}=\begin{bmatrix} a & b \\c & d \end{bmatrix}^{-1}=\dfrac{1}{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}$$

* Prof. Strang은 이 강의의 수강생들은 이 공식을 이미 알고 있다고 가정하는 것 같다. 
* 행렬식도 역행렬이 존재하기 위한 테스트 조건\(분모가 0이면 모순\) 정도로 알고 있다고 가정한다. 

#### 이 식의 요소들을 지난 강의까지 배운 개념들과 매칭시켜보자. 

* $$ad-bc$$: 이 것은 명백히 $$A$$의 determinant이다.
* $$\begin{bmatrix}d&-b\\-c&a\end{bmatrix}$$ : 이 행렬은 $$A^\top$$의 cofactor들로 만들어진 것이다.  
  * 즉, $$\begin{bmatrix} C_a&C_c\\C_b&C_d\end{bmatrix}$$ 

#### 이 식은 다음과 같이 일반화할 수 있다. 

{% hint style="info" %}
$$A^{-1}=\dfrac{1}{\det A}C^\top$$\(when $$C=\begin{bmatrix} C_a&C_b\\C_c&C_d\end{bmatrix}$$\)

* $$\det A$$: Products of $$n$$ elements.
* $$C^\top$$: Products of $$n-1$$ elements.
{% endhint %}

#### 예를 들어, 행렬 $$A$$ 가 다음과 같을 때의 역행렬은: 

* $$A^{-1}=\dfrac{1}{\det A}\begin{bmatrix} C_a&C_b\\C_c&C_d\end{bmatrix}^\top$$ 

$$\displaystyle \small \begin{bmatrix} a_{11}&a_{12}&a_{13}\\a_{21}&a_{22}&a_{23}\\a_{31}&a_{32}&a_{33}\end{bmatrix}^{-1}=\dfrac{1}{\sum\limits_{(\alpha, \beta, \gamma)} \pm a_{1\alpha}a_{2\beta}a_{3\gamma}} \footnotesize\begin{bmatrix} +(a_{22}a_{33}-a_{23}a_{32}) &-( a_{21}a_{33}-a_{23}a_{31}) & +(a_{21}a_{32}-a_{22}a_{31}) \\ -(a_{12}a_{33}-a_{13}a_{32}) &+( a_{11}a_{33}-a_{13}a_{31}) & -(a_{11}a_{32}-a_{12}a_{31}) \\ +(a_{12}a_{23}-a_{13}a_{22}) &-( a_{11}a_{23}-a_{13}a_{21}) & +(a_{11}a_{22}-a_{12}a_{21})   \end{bmatrix}^\top$$

* $$\det A$$: Products of $$3$$ elements.
* $$C^\top$$: Products of $$2$$ elements.

#### 실제로 위 공식이 $$AA^{-1}=I$$ 에 대입하여 만족하는지 체크해보자. 

* $$AA^{-1}=\dfrac{1}{\det A}AC^\top=I$$ 
* 아래와 같이, $$AC^\top=(\det A)I$$를 만족한다. **\(확인\)**

$$\begin{bmatrix} a_{11}&\cdots& a_{1n} \\    \\ a_{n1}&\cdots& a_{nn} \end{bmatrix}\begin{bmatrix} C_{11}&\phantom{\cdots}& C_{n1} \\  \vdots &&\vdots \\ C_{1n}&& C_{nn} \end{bmatrix}=\small\begin{bmatrix} \det A   & 0 & 0& \cdots \\  0 & \det A & 0& \cdots\\ 0&0& \det A &\cdots\\\vdots & \vdots & \vdots &\ddots \end{bmatrix}=\det A \small\begin{bmatrix} 1   & 0 & 0& \cdots \\  0 & 1 & 0& \cdots\\ 0&0& 1 &\cdots\\\vdots & \vdots & \vdots &\ddots \end{bmatrix}$$

* **대각원소가** $$\det A$$**인 이유?**
  * $$A$$의 $$i$$행과 $$C^\top$$의 $$i$$열의 곱은 cofactor formula와 일치한다.  
    * $$\det A={\color{red}a_{i1}}{\color{blue}C_{i1}}+{\color{red}a_{i2}}{\color{blue}C_{i2}}+\cdots +{\color{red}a_{in}}{\color{blue}C_{in}}$$
* **비대각원소가 0인 이유?**
  * $$(i,j)$$위치의 원소는$$A$$의 $$i$$번째 행을 $$j$$번째 행에 복사한 행렬의 determinant와 같다. 
    * $$\det A_{i\rightarrow j}={\color{red}a_{i1}}{\color{blue}C_{j1}}+{\color{red}a_{i2}}{\color{blue}C_{j2}}+\cdots +{\color{red}a_{in}}{\color{blue}C_{jn}}$$ 
  * 같은 행을 갖는 행렬의 determinant는 0이다. 

## Cramer's Rule for $$\bm{x}=A^{-1}\bm{b}$$ 

#### 역행렬의 공식을 이용해서 선형방정식계의 해를 구해보자. 

* $$\bm{x}=A^{-1}\bm{b}=\dfrac{1}{\det A}C^\top\bm{b}$$

$$\begin{bmatrix}x_1\\\vdots \\x_n\end{bmatrix}=\dfrac{1}{\det A}\begin{bmatrix} C_{11}&\cdots& C_{n1} \\  \\ C_{1n}& \cdots & C_{nn} \end{bmatrix}\begin{bmatrix}b_1 \\ \vdots \\b_n\end{bmatrix}=\dfrac{1}{\det A}\begin{bmatrix} b_1C_{11}+\cdots+b_nC_{n1} \\ \vdots \\ b_1C_{1n}+\cdots+b_nC_{nn}\end{bmatrix}$$ 

#### 다음 식으로 요약할 수 있다: $$x_i=\dfrac{b_1C_{1i}+\cdots+b_nC_{ni}}{\det A}$$ 

* 분자의 모양을 자세히 보면 왠지 어디서 많이 본 것 같다. 
  * Determinant를 구하기 위한 **cofactor formula와 유사**하다!
  * $$i$$번째 row가 아닌 $$i$$**번째 column의 cofactor에 대한 공식**이라는 점은 조금 다르다.  
  * 그러나 property \(10\)에 의하여, transpose해도 행렬식은 변하지 않으므로, **동일한 공식**이다. 
* 이는 **분자도** 분모와 같이 **어떤 행렬의** $$B_i$$**의 determinant로써 표현할 수 있다**는 것을 암시한다. 
  * $$B_i$$**는 행렬** $$A$$**의** $$i$$**번째 행을** $$\bm{b}$$**로 바꾸어준 행렬**이 된다. 
  * 아래 table은 $$n=4$$이고, $$i=3$$일때의 예시이다. 

<table>
  <thead>
    <tr>
      <th style="text-align:center"></th>
      <th style="text-align:center"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:center">
        <p></p>
        <p></p>
      </td>
      <td style="text-align:center">
        <p></p>
        <p></p>
      </td>
    </tr>
    <tr>
      <td style="text-align:center"></td>
      <td style="text-align:center"></td>
    </tr>
  </tbody>
</table>#### 이제 식은 다음과 같이 쓸 수 있다:$$x_i=\dfrac{\det B_i}{\det A}$$ 

* 이로써 inverse formula의 행렬곱 대신, $$B_i$$의 determinant를 구하는 것으로 대체할 수 있다. 
* 이러한 계산 방법을 **Cramer's rule**이라고 한다. \(크래머 공식이라고 표기. 실제 발음은 크레이머.\) 
* 이로 인해, cofactor의 계산 trick을 차용할 수 있긴 하지만, 계산량이 줄어들거나 하지는 않는다.
* 사실 이 방법은 elimination에 비해 속도도 늦고 **실용성이 없다**. **대수적 이해에 목적**을 두자.

#### Crammer's rule을 음미하는 다른 방법은 그 것을 기하학적으로 이해하는 것이다. 

* 다음 페이지 링크를 참조하자. 

{% page-ref page="../additional-essence-of-linear-algebra-by-3blue1brown/part-5.-e12.md" %}

* **면적/부피에 관련한 행렬식의 의미**를 알고 있어야 이해할 수 있다. 
  * Lec. 18에서 페이지 링크했던 내용. 
  * Strang 교수님 강의에서는 가장 마지막\(다음 소제목\)에 설명. 

## $$|\det A|=$$ Volume of box

{% hint style="danger" %}
* Lec 18-20에 걸친 세부내용을 모두 참조했다면, 이미 알고있는 내용이리라 생각한다. 
* 전반적으로 매우 straightforward하므로, 중복되지 않는 부분만 다루겠다.  
{% endhint %}

### Determinant의 기하학적 의미

#### **행렬의 row vector들이 이루는** $$n$$**차원 box 의 부피를 의미한다!**

* 단, vector들의 순서에 따라, 부호는 minus가 될 수 있다. 
* Box보다 더 폼나는 용어가 있다: **parallelepiped**

#### 3B1B 채널에서는 **column vector**가 선형변환 후에 만드는 부피라고 설명한다.

* 문제없다.  Property \(10\)에 의해서 **row vector**가 만드는 부피도 **동일**하다.  

#### 이 개념을 왜 Lec. 18. 초반에 이야기해주지 않았는지 궁금하다. 

* 의미도 모르는 숫자에 대해 벌써 3시간의 강의가 진행되었다. 
* 나는 미리 알고 강의를 들었지만, 그렇지 않았다면 많이 답답했을 것 같다. 
* 기하학적 직관이 연역적 설명보다 앞서는 것이 좋다고 생각한다. 

### Orthogonal Matrix의 Determinant를 구해보자. 

#### Orthogonal matrix $$Q$$일 경우, row vector들이 만드는 box는 unit hyper-cube이다!

* 즉, 모든 변\(벡터\)의 길이가 1이고, 모든 인접한 변이 수직이기 때문이다. 
* Hyper-cube의 면적은 1이다: $$\det Q=\pm1$$
* 대수적으로 검증해보자. \(Property \(7\) 사용\)
  * $$Q^\top Q=I \quad \Rightarrow  \quad |Q^\top Q|=|Q^\top||Q|=|Q|^2=I \quad \Rightarrow \quad |Q|=\pm1$$

#### $$Q$$가 정방행렬이 아닌 tall matrix이지만, 여전히 orthogonal basis를 갖는 경우? 

* 더이상 orthogonal matrix라고 불릴 수 없다. \(Lec. 17 참조\) 
* 참고로, wide matrix는 orthogonal basis의 정의에 위배되므로 존재 불가. 
* 이 행렬은 전체 차원을 span하지 않으므로 hyper-plane을 구성한다. 
*  Hyper-plane의 면적은 0이다: $$\det Q=0$$

### 단일 row/column 연산에 대한 선형성을 검증해보자. 

* Lec. 18에서 property \(3\)에 대한 내용을 box의 넓이로써 그려보면 다음 그림\[Fig. 1\]과 같다. 
* 천천히 그림을 해석해보면, 선형성이 쉽게 증명됨을 확인할 수 있다. 

![\[Fig. 1\] Textbook\(Introduction to Linear Algebra\)&#xC744; &#xCC38;&#xACE0;&#xD558;&#xC600;&#xB2E4;.](../../.gitbook/assets/image%20%28125%29.png)

### Determinant를 이용하여 삼각형의 넓이를 구해보자. 

![\[Fig. 2\]](../../.gitbook/assets/image%20%28137%29.png)

#### \[Fig. 2\]와 같이 **원점에서 떨어져 있는 삼각형의 넓이**를 행렬식을 이용해서 구해보자. 

* 기본적으로 행렬식\(평행사변형의 넓이\)의 1/2은  삼각형의 넓이를 의미함을 생각하자. 
* 그러나, 행렬식은 기본적으로 한 점이 원점에 놓여있는 상황만을 전제하고 있다. 
* 원점에서 떨어져 있다는 문제를 회피하는 방법은 두가지가 있을 수 있다. 
  1. 도형 전체를 원점으로 옮겨서 해결. 
  2. 새로운 차원을 만들어서 원점에 연결. 

![\[Fig. 3\]](../../.gitbook/assets/image%20%28155%29.png)

#### \[Fig. 3\]은 이 두가지 방법을 구체적으로 보여주고 있다. 

1. 한 꼭지점을 원점으로 이동시킨 후, 인접한 두 변이 이루는 행렬식\(parallelogram\)의 1/2. **\(왼쪽 그림\)**
2. 높이가 1인 parallelepiped의 부피는 밑변과 같음을 이용하여, parallelepiped 부피의 1/2. **\(오른쪽 그림\)**

* 오른쪽의 행렬식에 두번째와 세번째 열에 첫번째 열을 빼주고 계산을 하면 왼쪽 행렬식과 동일하다. 
  * Property \(5\)에 의해 row operation은 행렬식 값을 바꾸지 않음. 
  * $$\dfrac{1}{2}\begin{vmatrix}x_1&y_1&\red {\fbox 1}\\ \color{blue}x_2-x_1&\color{blue}y_2-y_1 & 0\\\color{blue}x_3-x_1&\color{blue}y_3-y_1&0 \end{vmatrix}=\dfrac{1}{2} \begin{vmatrix}x_2-x_1&y_2-y_1 \\x_3-y_1&y_3-y_1 \end{vmatrix}$$

