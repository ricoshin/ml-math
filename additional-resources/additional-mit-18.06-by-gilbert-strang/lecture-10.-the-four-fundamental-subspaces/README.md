# Lecture 10. The Four Fundamental Subspaces

## Introduction

### 이번 장에서는 row space와 column space 간의 연결관계를 다룬다. 

* 다음 행렬을 보라: $$\begin{bmatrix} 1 & 2 & 3 \\ 2 & 2 & 3 \\ 2 & 5 & 8 \end{bmatrix}$$

#### \(Column의 관점\) Column들은 언뜻보면 선형 독립인 것처럼 보인다. 

* 3번 행이 1, 2번 행의 합인 $$\begin{bmatrix} 3 \\ 3 \\ 7 \end{bmatrix}$$과 거의 유사하지만 아주 살짝 다르다. 
* 1, 2번이 span하는 평면에서  "**살짝 삐져나와**"있으니, 선형 독립인 것 같이 보인다. 

#### \(Row의 관점\) 그런데, row들은 명백하게 선형 종속이다. 

* 1번 열과 2번 열이 같기 때문에 elimination의 과정에서 zero row가 나타날 것이다.
* 정방행렬이기 때문에 zero row가 생기는 순간 **pivot이 없어져**버린다. 
* Full **row** rank를 갖지 못하면, Full **column** rank도 갖지 못하는 것이다. 
  * 하나의 free column이 pivot column을 대체하게 된다. 
  * Nullspace가 1차원\(하나의 기저벡터\)이 된다.
  * 역행렬이 존재하지 않는다.

#### 알고보니, column도 선형 종속이었음이 밝혀졌다.

* 실제로 Nullspace를 구해보면: $$c\begin{bmatrix} 1 \\ -2 \\ 1 \end{bmatrix}$$ 
* 즉, 1, 3번 행의 합과 2번 행의 합이 같다.
* 우리가 눈으로는 찾지 못했지만, 영벡터를 만드는 선형조합이 존재했다!
* **Column의 관점**에서는 잘 보이지 않았던 종속성이 **row의 관점**으로부터 확인되었다.  

#### 즉, row의 세계\(row space\)와 column의 세계\(column space\)는 연결되어 있다. 

* 이 두 세계와 각 세계에의 나머지 부분을 fill up하는 nullspace들이 존재한다!
* 이 것이 Strang 교수님이 말씀하시는 **The Four Fundamental Subspaces**이다. 
  * 이 강의의 절반을 요약해주는 매우 중요한 그림\(**Big picture**\)에 주목하자.   
  * Gilbert Strang 교수님이 처음 만드신 개념.

### 하위 목차들의 내용과 함께 공부하자. 

* 하위 목차를 병행해서 보는 것이 좋겠다\(Textbook에 나온 내용 + 조교 문제풀이 영상\). 
* 내용의 범주화를 위해 강의 내용의 일부를 하위 목차에 포함시켰다. 

{% page-ref page="untitled.md" %}

{% page-ref page="recitation-basis-and-dimension.md" %}

## 4대 부분공간\(The 4 fundamental subspaces\) 

### 행렬 $$A$$의 \($$m \times n$$\) 4대 부분공간

|  | **Column space of** $$A$$\*\*\*\* | Nullspace of $$A$$ | Row space of $$A$$ | Left nullspace of $$A$$ |
| :--- | :---: | :---: | :---: | :---: |
| **Notation** | $$\mathcal{C}(A)$$ | $$\mathcal{N}(A)$$ | $$\mathcal{C}(A^\top)$$ |  $$\mathcal{N}(A^\top)$$ |
| **Entire space** | $$\mathbb{R}^m$$ | $$\mathbb{R}^n$$ | $$\mathbb{R}^n$$ | $$\mathbb{R}^m$$ |
| **Basis** | Pivot cols. in $$A$$ | Special solutions | Pivot rows in $$R$$ | Bottom rows in $$E$$ |
| **Dimension** | Rank $$r$$ | $$n-r$$ | Rank $$r$$ | $$m-r$$ |

* 위 부분공간들은 행렬$$A$$를 기준으로 정의되지만, 표기에는 transpose가 사용되는 것을 볼 수 있다. 
* Row space와 left nullspace라는 2개의 새로운 subspace가 등장했다. 
* Basis와 Dimension은 하위 문서인 **\(Textbook\) Basis and Dimension of 4 Subspaces**를 참고하자. 

### Row space는 row들의 모든 선형조합을 말한다.

* 새로운 표기법을 도입할 수도 있을 것이다.
  * $$\mathcal{R}(A)$$: Row space of $$A$$
* 그러나 우리는 열벡터보다는 행벡터에 익숙하다.  
* Transpose를 이용하면 기존의 표기를 따르면서 행벡터를 계속 사용할 수 있다.
  * $$\mathcal{C}(A^\top)$$: Column space of $$A^\top$$

### Left nullspace는 row space의 nullspace를 말한다. 

* Row space에서 했던 것과 동일하게 transpose로 나타낼 수 있다. 
  * $$ \mathcal{N}(A^\top)$$: Nullspace of $$A^\top$$\($$A^\top \bm{y}=\bm{0}$$\) 
* 그리고 이것을 $$A$$**의 left nullspace**라고 부른다. 
  * $$A^\top$$의 관점이 아닌, 원시행렬 $$A$$ 관점에서의 이름이다. 
* $$A^\top \bm{y}=\bm{0}$$ 를 $$A$$에 대해 나타내기 위해 **양변에 transpose**를 취한다. 
* $$\bm{y}^\top A=\bm{0}^\top$$: $$\bm{y}$$가 $$A$$의 **왼쪽\(left\)**에서 곱해져서 **영벡터를 만든다\(nullspace\)**!  

### 기존에 알고 있던 사실들 about $$\mathcal{C}(A)$$, $$\mathcal{N}(A)$$

* **Basis of** $$\mathcal{C}(A)$$**:** \(소거된 상태의 echelon form의 행렬이 아닌\) 원시행렬$$A$$의 pivot column들
* **Basis of** $$\mathcal{N}(A)$$**:** $$A\bm{x}=\bm{0}$$의 special solution들
* **Dimension of** $$ \mathcal{C}(A)$$**:** pivot variable의 개수 \(rank $$r$$\) 
* **Dimension of** $$\mathcal{N}(A^\top)$$**:** free variable의 개수 \($$n-r$$\)

### **새로운 사실들  about** $$\mathcal{C}(A^\top)$$**,** $$\mathcal{N}(A^\top)$$ ****

* **Dimension of row space** $$\mathcal{C}(A^\top)$$**:** rank $$r$$
  * Column space의 차원과 같다\(Wonderful fact!\)
* **Dimension of left nullspace** $$\mathcal{N}(A^\top)$$**:** rank $$m-r$$
* Big picture에서 왼쪽 subspace들의 차원 합은 column의 개수 
  * Dim$$\mathcal{C}(A^\top)$$ + Dim$$\mathcal{N}(A)$$ = $$n$$
* Big picture에서 오른쪽 subspace들의 차원 합은 row의 개수 
  * Dim$$\mathcal{C}(A)$$ + Dim$$\mathcal{N}(A^\top)$$ = $$m$$\*\*\*\*

### **\(정리\) Fundamental Theorem**

* **Row space**와 **column space**의 차원은 rank $$r$$로 같다! 
* **Null space**와 **left nullspace**는 각각의 full dimension인 $$n$$과 $$m$$의 나머지를 채운다. 
  * Nullspace는 $$n-r$$차원 / left nullspace는 $$m-r$$차원 

## 좀 더 자세히 들여다보자. 

### 선형변환의 양단에서 바라보는 column space와 nullspace

* 선형변환 전과 후는 다른 전체 차원을 갖는다. 
* $$m\times n$$의 행렬의 경우$$\mathbb{R}^n \rightarrow \mathbb{R}^m $$
* 이 변환\(함수\)에서 $$\mathbb{R}^n$$의 모든 점은 $$ \mathbb{R}^m $$ 의 어떤 점으로 mapping이 되야한다. 

#### Column space는 선형변환 후의 부분공간이다. \($$\in \mathbb{R}^m$$\) 

* 변환 후 **살아남는** 공간을 **출력단**의 관점에서 본 것. $$\red {\mathcal{C}(A)} $$ in **\[Fig. 1\]**.
* 변환 전의 $$n$$차원의 공간에서 nullspace를 제외한 부분이  변환 후의 $$r$$차원의 공간이 된다. 
* 공간 자체는 선형변환하지만, 차원이 보존되는 선택받은 공간이다.  

#### Nullspace는 선형변환 전의 부분공간이다. \($$\in \mathbb{R}^n$$\)

* 변환 후 **원점으로 소실되는** 공간을 **입력단**의 관점에서 본 것. $$\mathcal{N}(A)$$ in **\[Fig.1\]**.
* Nullspace는 선형방정식계의 solution이 살고 있는 공간과 같다. 
  * solution도 선형변환의 입력으로써 선형변환 전의 공간에 산다. 
* Column space가 만들어지면서 남은 차원이 원점으로 소실되는 것이 nullspace이다. 
* 선형변환의 풍파를 견디지 못하고 블랙홀으로 빨려들어가는 버려진 공간이다.  

![\[Fig. 1\] N\(A\)&#xB97C; &#xC81C;&#xC678;&#xD55C; &#xB098;&#xBA38;&#xC9C0; &#xC804;&#xCCB4; R^3&#xAC00; C\(A\)&#xB85C; &#xC120;&#xD615;&#xBCC0;&#xD658; &#xB41C;&#xB2E4;. N\(A\)&#xB294; &#xC6D0;&#xC810;&#xC73C;&#xB85C; &#xBE68;&#xB824;&#xB4E4;&#xC5B4;&#xAC04;&#xB2E4;.](../../../.gitbook/assets/image%20%2885%29.png)

#### Nullspace가 0으로 소실되는 이유\(=free column이 생기는 이유\):

1. 변환 후의 column space의 basis가 선형종속이되면서 차원이 손실 
   * 행렬이 정방형이거나 위아래로 길때,  한개 이상의 행에서 pivot 찾기에 실패 
2. 변환 후의 전체 공간의 차원 자체가 작아서 차원이 손실 
   * 모든 행에 pivot을 다 찾았지만, 행렬이 옆으로 길어서 열에는 pivot이 부족할때
3. 1과 2가 동시에 일어나면서 차원이 손실  

## 4대 부분공간을 그림으로 그려보자.

### _Big Picture_ of 4 fundamental subspaces

![\[Fig. 2\] https://sn1729.com/2016/11/22/linear-algebra-101-vector-spaces/](../../../.gitbook/assets/image%20%2873%29.png)

#### 변환\($$A$$\) 전 차원에서의 그림 \[Fig. 2 왼쪽\] 

* **변환 전**의 전체 벡터공간의 차원: $$n$$
* 변환 후에 0으로 소실되는 **변환 전** 부분공간\(**nullspace**\)의 차원: $$n-r$$
* 변환 후에 0으로 소실되지 않고 남아있는 **변환 전** 가장 큰 부분공간의 차원 : $$r$$  $$\cdots\red{(1)}$$

#### 변환\($$A$$\) 후 차원에서의 그림 \[Fig. 2 오른쪽\] 

* **변환 후**의 전체 벡터공간의 차원: $$m$$
* 성공적으로 선형변환된 **변환 후** 부분공간\(**column space**\)의 차원 : $$r$$                                   
* column들이 span하지 못하는 **변환 후** 가장 큰 부분 공간의 차원: $$m-r$$           $$\cdots\red{(2)}$$

{% hint style="warning" %}
**어떤 부분공간을 포함하지 않는\(원점 제외\) 가장 큰 부분공간이란?** 

*  그 부분공간과 **직교\(orthogonal\)하는 가장 큰 subspace**이다. 
* 이 부분공간의 차원은 전체 차원\($$n$$\)에서 nullspace의 차원\($$n-r$$\)을 뺀 값이다. 
  * $$n-(n-r)=r$$

**\(주의\) 전체 공간에서 어떤 부분공간을 뺀 것\(차집합\)과는 다르다!** 

* 차원을 빼준다고 공간자체의 차집합이라는 것으로 오해해서는 안된다. 
* 이 공간은 subspace가 아니다. \(차원을 말할 수 없다.\)  
* 이미 배운 subspace의 정의를 위반하기 때문이다. \(e.g. 원점을 통과하지 않는다.\) 
* 그러나 이 집합은 엄연한 선형변환의 정의역이다. \(이후 다시 논하겠다.\) 
{% endhint %}

#### Transposed된 변환\($$A^\top$$\) 의 관점에서 위의 작업을 똑같이 해주면?  

* 이 별개로 보이는 두쌍의 subspace들 사이의 **놀라운 관계성**이 발견된다. 
* $$\red{(1)}$$ $$A^\top$$의 **column space**가 되고, $$\red{(2)}$$는 $$A^\top$$의 **null space**가 된다! 

#### \[Fig. 2\]의 화살표들은$$A$$와 $$A^\top$$가 어떻게 서로 상호작용하는지 보여준다.  

* 양방향의 변환을 계속하게 되면, 같은 부분공간 안에서 왔다갔다 하는 것은 사실이다.
* 그러나, 다시 같은 포인트로 되돌아오지는 않는다.  \(역변환 \(pseudo\) inverse 이 아님\)  
  * $$A$$가 orthogonal matrix인 경우는  예외. $$A^\top = A^{-1}$$
* \(TODO\) 나중에 배울 left inverse / pseudo inverse가 이 상황에서 어떻게 표현될까? 

![\[Fig. 3\] https://kevinbinz.com/2017/02/20/linear-algebra/](../../../.gitbook/assets/image%20%28129%29.png)

#### \[Fig. 3\]의 매핑 묘사\(화살표들\)는 다소 오해의 소지가 있다고 생각한다. \(Fig. 2도 마찬가지\)

* $$\mathbb{R}^{n}$$의 domain\(정의역\)이 row space\(보라\)과 nullspace\(초록\)이 전부인 것처럼 보이기 때문이다. 
* 전체 3차원에서 nullspace가 1차원 직선이라고 가정해보자. 
  * 전체공간에서 nullspace를 빼 준 영역\(**차집합**\)은 **2차원 부분공간**일까? 
  * **그렇지 않다**. 위에서 언급했든 부분공간도 아니고, 차원 자체를 갖을 수도 없다.
* 그러나 이 영역에 살고 있는 모든 벡터는 $$\mathbb{R}^{m}$$에 있는 column space\(주황\)로 매핑될 수 있다. 
  * Row space\(보라\)도 이 영역의 부분집합이지만, 이 것이 유일한 것은 아니다. 
  * 2차원으로 추상화된 그림에서 이러한 사각지대\(dead zone\)를 표현하기가 쉽지 않다. 
  * \(실제로는 사각형들이 놓여있는 흰 여백에서도 row나 column space에 매핑 가능\) 

## 좀 더 직관적으로 그려볼 수 없을까? 

### \[Fig. 4\]는 실제 행렬을 예시로 하여 그려본 그림이다. 

![\[Fig. 4\] &#xC2E4;&#xC81C; &#xD589;&#xB82C;&#xC744; &#xAC00;&#xC9C0;&#xACE0; &#xC880; &#xB354; &#xC0AC;&#xC2E4;&#xC801;&#xC778; &#xADF8;&#xB9BC;&#xC744; &#xADF8;&#xB824;&#xBCF4;&#xC558;&#xB2E4;.](../../../.gitbook/assets/image%20%2874%29.png)

* 2차원의 평면들의 직교로 단순화된 다른 그림들은 지나치게 추상적으로 느껴질 수 있다. 
* 여기서는 실제 행렬을 기반으로 시각적으로 모든 공간이 보이기 때문에 좀 더 직관적이다. 
* 동시에 많은 것들이 일어나고 있으므로 divide & conquer해보자! 

### \[Fig. 5\]는 column space와 row space 사이의 mapping에 집중한 그림이다. 

![\[Fig. 5\] row space vs. column space](../../../.gitbook/assets/image%20%285%29.png)

#### 오해를 풀어보자! \[Fig. 6\]

* $$A$$와 $$A^\top$$는 **row space**\(주황\)와 **column space**\(빨강\) 사이만을 오가는 mapping이 아니다. 
* **실제 mapping은 다음과 같이 이루어진다.** 
  * **입력:** 전체 벡터공간\(큰 파선 원\)에서 nullspace\(검정\)를 제외한 나머지 영역
  * **출력:** 각각의 subspace\(빨강 or 주황 직선\)
* 두 공간끼리는 선형변환은 일어나지만 차원이 짜부러지는 일은 없다. \(rank 유지\) 
* 이러한 그림에서는 다음 두가지를 명징하게 하여 오해의 여지를 줄여준다.  
  1. 선형변환$$A$$ 의 정의역은 row space가 아니라 전체 공간이다.  
  2. 선형변환 $$A^\top$$은 $$A$$의 \(pseudo\) inverse가 아니다. \(대부분의 경우\) 

![\[Fig. 6\] ](../../../.gitbook/assets/image%20%2840%29.png)

#### 만약 두 변환을 번갈아가면서 반복한다면\($$\cdots AA^\top A A^\top A  A^\top A\bm{x}$$\)? **\[Fig. 6\]**

* 처음 시작은 row space에서 하지 않더라도, 그 결과는 column space에 떨어지게 된다. 
* 한 번 subspace 안으로 들어오면 계속해서 두 subspace 안에서만 왕복하게 된다. 
* e.g. $$\begin{bmatrix} 1 \\ 2 \\ 1 \end{bmatrix} \xrightarrow{A} \begin{bmatrix} 6 \\ 12 \end{bmatrix} \xrightarrow{A^\top} \begin{bmatrix} 30 \\ 60 \\ 30 \end{bmatrix} \xrightarrow{A} \begin{bmatrix} 180 \\ 360 \end{bmatrix} \xrightarrow{A^\top} \cdots$$
* 계속 일정 크기만큼 증폭되지만 같은 subspace안에 머물러 있다. 
* \(TODO\) eigenvector와 관련 확인
* 당연한 얘기였지만, inverse는 확실히 아님을 알 수 있다.  

### \[Fig. 7\]는 nullspace와 left nullspace 사이의 mapping에 집중한 그림이다. 

![\[Fig. 7\] nullspace vs. left nullspace](../../../.gitbook/assets/image%20%28126%29.png)

* \[Fig. 1\]에서의 nullspace의 모습을 양단에서 동시에 보여주는 그림이다.  
* 블랙홀\(없음의 상태\)로 빨려들어가는 느낌으로 상상해보자.  
  * 소멸하는, 짜부러지는, collapsed, squished되는 느낌.

