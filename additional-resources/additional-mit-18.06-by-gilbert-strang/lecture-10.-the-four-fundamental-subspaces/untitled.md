# \(Textbook\) Basis and Dimension of 4 Subspaces

## Introduction

### 목표 

* Lecture 10.에서 배울 내용을 보충하고자 한다.
* [Textbook](https://math.mit.edu/~gs/linearalgebra/linearalgebra5_3-5.pdf)을 참조했다. 

#### 다음 질문에  대한 답을 찾는 과정이다. 

* 왜 elimination 과정을 거치면 pivot column / pivot row는 항상 선형독립이 될까? 
* 왜 row space와 column space는 차원\(rank\)이 같을까? 
* 왜 elimination 과정에서 column space는 변하는데 그 차원은 그대로 일까? 
* 왜 elimination 과정에서 특정 subspace는 보존되고 나머지는 변할까? 

#### 다음을 예시로 삼아서 설명한다.

행렬 $$A$$를 elimination을 통해 RREF인 $$R$$로 만드는 과정: 

* $$A=\begin{bmatrix} 1&3&5&0&7 \\ 0&0&0&1&2 \\ 1&3&5&1&9 \end{bmatrix} \rightsquigarrow \begin{bmatrix} \fbox1&3&5&0&7\\0&0&0&\fbox1&2\\0&0&0&0&0\end{bmatrix}=R$$

## $$R$$의 4대 부분공간의 차원을 알아보자.  

* $$A$$가 아닌 $$R$$의 subspace임을 주의하자. 
* $$R$$을 별개의 행렬로 보고 subspace의 차원을 구해보는 것이다. 

### Row space of$$R$$의 차원

#### 소거 후에 살아남은\(non-zero\) row들은 항상 선형독립이다! 

* Elimination의 과정을 통해 처음 $$r$$개 non-zero row가 살아남게 된다. 
  * 이들은 서로 선형독립이며, row space의 basis이다. 
* Elimination의 과정을 통해 마지막 $$m-r$$개의 zero row가 생긴다. 
  * 선형종속인 row가 다른 row들의 선형조합을 통해 zero-out된 것이다. 
* 선형방정식계를 풀때도 계수의 비율이 같은 방정식이 zero row가 되었었다. 
* 고로, 살아남은 row들은 항상 서로 선형독립이 된다. 

{% hint style="warning" %}
_**Remark.**_ zero row들은 아래에 깔려있기 때문에, non-zero row들은 처음 $$r$$\(rank\)개 이다.  
{% endhint %}

#### 그 증거를 찾아보자. 

* 일단 살아남은 row에는 반드시 leading coefficient\(pivot\)가 존재한다. 
* 그들은 RREF의 특성에 의해 위 아래로 0만 존재한다. \(identity matrix의 형태\) 
  * $$\begin{bmatrix} \red{\fbox1}&3&5&\red0&7\\\red0&0&0&\red{\fbox1}&2\\0&0&0&0&0\end{bmatrix} \begin{array}{} \green\leftarrow \text{survived the elimination} \\ \green\leftarrow \text{survived the elimination} \\ \phantom{} \end{array}$$ 
* 이는 살아남은 row들이 pivot 위치에 완전히 orthogonal한 성분을 갖도록 한다. 
* 즉, 위의 두 pivot row들에 모두 0을 곱하지 않고는 절대 zero row를 만들 수 없다. 
  * $$\forall\green{c_1}, \ \forall\green{c_2} \in \mathbb{R}: \ \green{c_1}[\red1 \quad  3 \quad 5 \quad \red0 \quad 7 ] + \green{c_2}[\red0 \quad  0 \quad 0 \quad \red1 \quad 2 ] \neq [0 \quad  0 \quad 0 \quad 0 \quad 0 ]$$

{% hint style="warning" %}
_**Remark.**_ 두 벡터들의 동일 성분에 zero와 non-zero가 같이 있으면 항상 선형독립임을 기억하자.
{% endhint %}

#### 그래서 $$R$$의 row space의 차원은?

* Non-zero row\(처음 $$r$$개의 row\)는 항상 선형독립이면서 row space를 span할 수 있다.  
  * \(zero row는 contribution이 없기 때문에 제외\)
  * 즉, non-zero row들은 row space의 **basis**이다.  
* Basis의 개수\(차원\)는 살아남은 row의 개수이고, 이는 pivot의 개수\(rank\)와 같다.  

{% hint style="info" %}
**결론 1**: $$R$$의 row space의 **차원**은 rank $$r$$과 같다. 
{% endhint %}

{% hint style="info" %}
**결론 2:** $$R$$의 row space의 **기저**는 처음 $$r$$개의 **pivot**\(non-zero\) **row**들이다. 
{% endhint %}

### Column space of$$R$$의 차원 

#### 소거 후의 pivot column들은 항상 선형독립이다!  

* Pivot column들은 위에서 언급했듯이 identity matrix 형태이다. 
  * $$\begin{array}{c}\begin{bmatrix} \red {\fbox  1}&3&5&\red0&7\\\red0&0&0&\red{\fbox1}&2\\\red0&0&0&\red0&0\end{bmatrix} \\ \begin{matrix} \ \  \green \uparrow \   &\phantom{0}&\phantom{0}& \  \green \uparrow \ \  &\phantom{0} \end{matrix} \end{array}$$ 
* Identity matrix의 column들의 선형조합으로 절대 zero column을 만들 수 없다. 
* 그러므로 이들은 항상 선형독립이다. 
* 그러나 이들만 가지고 전체 공간을 span하는지는 알 수 없으므로, 아직 basis인지는 알 수 없다. 

{% hint style="warning" %}
Row/column space 모두 pivot column의 독특한 모양\(identity\)에 의해 선형독립성을 갖는다.
{% endhint %}

#### 소거 후의 free column들은 항상 pivot column들과 선형종속이다!

* 나머지 non-pivot\(free\) column들은 pivot column의 선형조합으로 쉽게 만들 수 있다. 
* Zero row를 제외한 모든 열 위치에 각각 1을 원소로 갖기 때문에 어떤 벡터든지 선형조합 가능하다. 
  * $$R$$의 column을 보라: $$\green7C_1+\green2C_4=\green 7\begin{bmatrix} \red1\\0\\0\end{bmatrix}+\green 2\begin{bmatrix} 0\\\red1\\0\end{bmatrix}=\begin{bmatrix} \green 7\\ \green 2\\0\end{bmatrix}=C_5$$
* 결국 모든 free column은 pivot column에 선형종속이고 새로운 차원에 기여하지 못한다. 
  * 즉, pivot column들만으로 column space를 span할 수 있다. 

#### 그래서 $$R$$의 column space 차원은?

* Pivot column들은 항상 선형독립이며, column space를 span할 수 있다. 
  * 즉, pivot column들은 column space의 **basis**이다.  
* Basis의 개수\(차원\)는 pivot의 개수\(rank\)이다. 

{% hint style="info" %}
**결론 1**: $$R$$의 column space의 **차원**은 rank $$r$$과 같다. 
{% endhint %}

{% hint style="info" %}
**결론 2**: $$R$$의 column space의 **기저**는 $$r$$개의 **pivot column**들이다. 
{% endhint %}

### Nullspace of$$R$$의 차원 

이 내용은 Lecture 7.에서 배운 내용이니, 해당 목차를 참조하자. 

#### Nullspace의 basis는 special solution들이다. 

* 각각의 special solution은 free variable 중 하나만 1이고 나머지는 모두 0이다. 
* 위에서 이야기했듯이, 이러한 identity matrix의 포함은 항상 선형독립을 보장한다. 
* Special solution들은 항상 서로 선형독립이다. 
* Special solution의 개수는 free variable의 개수\($$n-r$$\)와 같다. 

{% hint style="info" %}
**결론 1**: $$R$$의 nullspace의 **차원**은 $$n-r$$이다. 
{% endhint %}

{% hint style="info" %}
**결론 2**: $$R$$의 nullspace의 **기저**는 $$R\bm{x}=\bm{0}$$를 만족하는 **special solution**들이다. 
{% endhint %}

### Left nullspace of$$R$$의 차원

* Lecture 10.에서 배웠듯이 $$R^\top\bm{y}=\bm{0}$$는 양변에 transpose를 취해서 살펴보자. 
* $$\bm{y}^\top R=\bm{0}^\top$$ : 이렇게 left-hand side에 놓게 되면 나중에 $$\bm{y}^\top A=\bm{0}^\top$$ 를 풀때 유리한 점이 있다. 
  * \(스포\) 왼쪽에서 곱해지는 elimination matrix를 활용가능.

#### $$\bm{y}^\top R=\bm{0}^\top$$가 찾는 것은 어떤 선형조합이 영벡터를 만드는지를 찾는 것이다. 

* $$\begin{bmatrix}y_1 \ \ y_2 \ \ \red {y_3} \end{bmatrix}\begin{bmatrix} \fbox1&3&5&0&7\\0&0&0&\fbox1&2\\\red0& \red0&\red0&\red0&\red0\end{bmatrix}=\begin{bmatrix}0 \ \ 0 \ \ 0 \ \ 0 \ \ 0 \end{bmatrix}$$ 
* 이 식을 만족하는 $$\bm{y}$$가 left nullspace이고, 그 차원을 구하면 된다. 
* 예시에서는 $$r=2$$이고 $$m-r=1$$인 상황. 
* 처음$$r$$개의 non-zero row들은 선형독립 관계이므로 둘 다 0일때만 영벡터를 만들 수 있다. 
* 마지막 $$m-r$$개의 zero row\(빨강\)들은 어떤 수를 곱해도 결과에 영향을 주지 않는다. 
  * 이들의 모든 선형조합이 nullspace를 span한다. 
* $$y_{1:r}$$: \(right\) : 무조건 0으로 고정.
* $$y_{r+1:m}$$: \(right\) nullspace를 구할때의 free variable 처럼 생각하면 된다. 

#### Left nullspace의 기저는 다음과 같다: 

* 위의 예시에서는 zero-row\(빨강\)가 한 개 뿐이다\( basis도 1개 / 차원도 1\). 
  * $$\bm{y} = c[\ 0 \ \ 0 \ \ \red1 \ ]$$\(직선을 의미함\) 
* $$n-r$$개의 zero-row로 일반화한 결과는 아래 **결론2**를 참조하자. 
* Left nullspace는 zero-row의 개수\($$m-r$$\)만큼 자유도를 갖게된다.  
*  즉, zero-row의 개수는 전체 row개수\($$m$$\)에서 pivot의 개수\($$r$$\)를 뺀 것이다.  

{% hint style="info" %}
**결론 1**: $$R$$의 left nullspace의 차원은 $$m-r$$이다. 
{% endhint %}

{% hint style="info" %}
**결론 2**: $$R$$의 nullspace의 **기저**는 다음과 같다: 

* $$\bm{y}^\top = \begin{cases} \quad c_{1} [\ 0 \ \  0 \ \ \cdots \ \ 0 \quad \red1\ \ 0 \ \ \cdots   \ \ 0 \ \  \ ] \\  \quad c_2 [\ 0 \ \  0 \ \ \cdots \ \ 0 \quad 0\ \ \red1 \ \ \cdots   \ \ 0 \ \  \ ] \\ \qquad \qquad \ \  \vdots \qquad \qquad \ \ \ \ \ddots \\c_{m-r} [\ \underbrace{0 \ \  0 \ \ \cdots \ \ 0}_{r} \quad \underbrace{1\ \ 0 \ \ \cdots   \ \ \red1}_{m-r} \ \  \ ] \\\end{cases}$$ 
{% endhint %}

## $$A$$의 4대 부분공간의 차원을 알아보자.

모든$$A$$의 부분공간의 차원은 해당하는$$R$$**의 부분공간의 차원과 같다**. 그 이유를 알아보자. 

### Row space of$$A$$의 차원

#### $$A$$와 $$R$$의 row space는 같다. 

* $$R$$의 모든 row는 $$A$$의 선형조합이다. 
  * 소거법의 정의에 따라,$$A$$의 row operation들의 결과가 $$R$$이다. 
  * $$EA=R $$ : 행렬의 왼쪽 곱은 row operation으로 해석가능.
    * $$E$$: elimination matrix\(전체 소거과정\) 
* $$A$$의 모든 row는 $$R$$의 선형조합이다. 
  * $$A=E^{-1}R$$ : 소거의 역방향 역시 row operation으로 해석가능.  
  * 직관적으로 생각해봐도 반대부호&역순인 row operation. 
* Elimination은 row 자체는 바꾸지만 row space는 유지한다. 
  * Row operation은 두 행벡터의 선형조합으로 하나의 행을 교체하는 행위다. 
  * 그리고 두 행벡터의 선형조합은  반드시 같은 부분공간에 존재! 
  * e.g. $$(R_3-2R_1) \rightarrow R_3$$: 세번째 row를 같은 subspace의 다른 벡터로 변경.

{% hint style="info" %}
**결론 1:** $$A$$는 $$R$$과 같은 row space를 갖는다. i.e. $$\mathcal{C}(A^\top)=\mathcal{C}(R^\top)$$
{% endhint %}

#### $$R$$의 non-zero row들은 row space의 basis이다.  

* $$R$$의 처음 $$r$$개의 non-zero row들은 선형독립인 basis이지만, $$A$$는 항상 그렇지 않다. 
* Permutation\(row exchange\)로 선형독립인 row들이 위치를 바꾸기 때문이다. 
* 물론 $$R$$의 non-zero row 들에 대응되는 원시행렬$$A$$의 row들을 잘 매칭하면 찾을 수는 있다. 
* 소거과정에서 permutation\(row exchange\)가 일어났는지의 여부가 중요하다. 
* **Permutation가 없었다면:**$$A$$도 역시 처음 $$r$$개의 row도 역시 basis일 것이다.  
* **Permutation이 있었다면:**$$R$$의 basis가 될 수 있었던 $$A$$의 row를 역추적해서 선택해야 한다. 

{% hint style="warning" %}
* Permutation 과정을 역추적하면$$A$$의 row에서 basis를 찾을 수도 있다. 
* 그러나, 이러한 과정도 필요없고, 보다 reduced된, $$R$$의 basis를 사용하자. 
{% endhint %}

{% hint style="info" %}
**결론2 :** $$A$$와 $$R$$의 row space는 같은 차원\($$r$$\)과 basis를 갖는다. 
{% endhint %}

{% hint style="info" %}
**결론 3 :** $$A$$의 rowspace의 basis는 ****$$R$$**의 pivot**\(non-zero\) **row**들이다. 
{% endhint %}

### Column space of$$A$$의 차원

#### $$A$$와 $$R$$의 column space는 다르다. 

* Row reduction은 column space의 보존에 아무런 주의를 기울이지 않는다.  
* 우리의 예시에서, $$R$$의 3번째 row가  zero-out되었다. 
  * $$A$$의 column들을 3번째 성분\(빨간색\)은 non-zero이다. 
  * zero들의 선형조합으로 non-zero\(초록색\)를 만들 수 없다.  
  * 즉, $$R$$의  선형조합으로 $$A$$의 column들을 절대 만들어낼 수 없다. 
  * $$A=\begin{bmatrix} 1&3&5&0&7 \\ 0&0&0&1&2 \\ \green1&\green3&\green5&\green1&\green9 \end{bmatrix} \rightsquigarrow \begin{bmatrix} \fbox1&3&5&0&7\\0&0&0&\fbox1&2\\\red0&\red0&\red0&\red0&\red0\end{bmatrix}=R$$ 

{% hint style="info" %}
**결론 1:** $$A$$는 $$R$$과 **다른** column space를 갖는다. i.e. $$\mathcal{C}(A)\neq\mathcal{C}(R)$$
{% endhint %}

#### 그렇지만 $$A$$와 $$R$$의 column space의 '차원'은 같다. 왜일까? 

* 왜 column space는 바뀌었는데, dimension은 같을까? 

#### **두 행렬에서 동일한 combination이 zero column을 만들기 때문이다.** 

* 예를 들어, 다음 선형조합은 두 행렬에서 모두 zero column을 만든다. 
  * $$3C_1-C_2=\bm{0}$$
  * $$2C_1+C_3+2C_4-C_5=\bm{0}$$
* 왜 이러한 combination이 유지가 되는걸까? 
  * $$3C_1-C_2=3\begin{bmatrix} \red{a_{11}}\\\blue{a_{21}}\\\green{a_{31}}\end{bmatrix}-\begin{bmatrix}\red{a_{12}}\\\blue{a_{22}}\\\green{a_{32}}\end{bmatrix}=\begin{bmatrix} \red0\\\blue0\\\green0\end{bmatrix}=\bm{0}$$ 
  * 선형조합의 벡터합이나 실수배는 모두 같은 행의 원소끼리 진행된다. 
  * Row operation에서 하는 일은 같은 행끼리 곱해서 더하고 빼는 것이다. 
  * 우변이 0이되는 선형조합의 관점에서는 0끼리 row operation을 하는 격이다. 
  * 0끼리 어떻게 곱해서 어떤 조합으로 더하고 빼든 항상 0이다. **\(combination 유지\)**

#### 다른 말로 표현하면: $$A$$와 $$R$$의 null space가 같다! 

* 위에서 살펴본 바에 따르면, $$A\bm{x}=\bm{0}$$의 해와 $$R\bm{x}=\bm{0}$$의 해는 같기 때문이다. 
* Elimination 과정에서 $$\mathcal{C}(A)$$는 변해도 $$\mathcal{N}(A)$$는 변하지 않는다! 
* Nullspace 공부할때도 같은 내용을 언급했다. 
  * Elimination 중에 $$A\bm{x}=\bm{0}$$의 solution은 변하지 않음. 
* 연립방정식을 풀때 방정식끼리 곱해서 더하고 빼고 해는 변하지 않는 것과 같다. 

{% hint style="warning" %}
* $$A\rightarrow R$$과정에서 **변하는** subspace: **Column space**, **Left nullspace**
  * Big picture에서 오른쪽\(선형변환의 출력\)에 있는 subspace들
* $$A\rightarrow R$$과정에서 **변하지 않는** subspace: **Row space**, **Nullspace** 
  * Big picture에서 왼쪽\(선형변환의 입력\)에 있는 subspace들  
* \(참고\) $$A^\top$$의 관점에서는 변화여부가 반대가 됨. \(아래 Left nullspace 참조\) 
{% endhint %}

#### 그런데 이게 차원이랑 무슨 상관?

* Free variable의 개수가 같으면 column variable의 개수도 같기 때문이다! 
* $$A$$와 $$R$$의 nullspace가 같다.
  * = nullspace의 차원, special solution의 개수, free column의 개수\($$n-r$$\)도 같다.
  * = 똑같이 $$n$$개의 행을 갖는 두 행렬에서 pivot column의 개수\($$r$$\)도 같다. 
* 그러므로 column space의  basis의 벡터수, 즉 차원도 같다.  

{% hint style="info" %}
**결론 2:** $$A$$와 $$R$$의 row space는 같은 차원\($$r$$\)을 갖는지만, basis는 다르다.
{% endhint %}

{% hint style="info" %}
**결론 3:** $$A$$의 row space의 basis 는 $$R$$**의 pivot column에 해당하는 원시행렬**$$A$$**의 column**이다. 
{% endhint %}

### Nullspace of$$A$$의 차원

* Column space의 차원을 알아내는 과정에서 이미 $$A$$와 $$R$$의 nullspace가 동일함이 밝혀였다. 
* Basis도 같으며, 차원은 당연히 같다. 

{% hint style="info" %}
**결론 1:** $$A$$와 $$R$$는 같은 nullspace를 갖는다.  i.e. $$\mathcal{N}(A)=\mathcal{N}(R)$$
{% endhint %}

{% hint style="info" %}
**결론 2:** $$A$$와 $$R$$의 nullspaces는 같은 차원\($$n-r$$\)과 basis를 갖는다. 
{% endhint %}

{% hint style="info" %}
**결론 3**: $$A$$의 nullspace의 **기저**는 $$R\bm{x}=\bm{0}$$를 만족하는 **special solution**들이다. 
{% endhint %}

### Left nullspace of$$A$$의 차원

위에서 논의한 내용들을 transpose의 관점에서 적용해보자. 

* $$R$$의 left nullspace는 $$R^\top$$의 nullspace이다. 
* $$A$$의 left nullspace는 $$A^\top$$의 nullspace이다. 

#### $$A^\top$$와 $$R^\top$$의 nullspace는 다르다. 

* $$R^\top$$은 \($$A$$의 row reduction의 결과\)$$\phantom{}^\top$$이며, 동시에 \($$A^\top$$의 column reduction의 결과\)이다. 
* Transpose 기준에서는 \(기존과 반대로\) row space와 nullspace가 보존되지 않는다. 
* 즉, $$R^\top$$의 nullspace는 $$A^\top$$의 nullspace와 다르다! 

{% hint style="info" %}
**결론 1:** $$A$$와 $$R$$는 다른 left nullspace를 갖는다.  i.e. $$\mathcal{N}(A^\top )\neq\mathcal{N}(R^\top)$$
{% endhint %}

#### $$A^\top$$와 $$R^\top$$의 nullspace의 차원은 같다. 

* $$A^\top$$의 전체 행의 개수는 $$m$$이다. 
* $$A^\top$$의 column space의 차원은 $$A$$의 row space와 같은 $$r$$이다. 
* $$A^\top$$의 nullspace의 차원은 $$m-r$$이다. 

{% hint style="info" %}
**결론 2:** $$A$$와 $$R$$의 left nullspaces는 같은 차원\($$n-r$$\)을 갖지만, basis는 다르다. 
{% endhint %}

#### $$A^\top$$의 nullspace의 기저는?

* 직접 $$A$$를 transpose한 한 뒤, 소거법을 통해 nullspace를 구할 수도 있다: $$A^\top \bm{y}=\bm{0}$$
* 그러나, $$R$$의 left nullspace를 구했을 때와 같이, transposed 버전을 살펴보자:  $$\bm{y}^\top A=\bm{0}^\top$$
  * 후자의 방법으로 추가비용 없이 더 간단히 구할 수 있다. 
* 어떤 row들의 선형조합이 영벡터\(빨강\)를 만드는지는 elimination 과정에 이미 드러나 있다. 
  * $$ EA= \begin{bmatrix} e_{1,1}&e_{1,2}&e_{1,3}\\ e_{2,1}&e_{2,2}&e_{2,3} \\ \green{e_{3,1}}&\green{e_{3,2}}&\green{e_{3,3}}\\ \end{bmatrix}\begin{bmatrix} 1&3&5&0&7 \\ 0&0&0&1&2 \\ 1&3&5&1&9 \end{bmatrix} =\begin{bmatrix} \fbox1&3&5&0&7\\0&0&0&\fbox1&2\\\red0&\red0&\red0&\red0&\red0\end{bmatrix}=R$$ 
* $$E$$는 전체 elimination 과정에 대응되는 행렬이다. 
* $$E$$의 세번째 row\(초록\)를 찾으면 어떤 row의 선형조합이 영벡터를 만들었는지 알 수 있다. 
* 그리고 그 선형조합의 임의의 실수배 또한 영벡터를 만들 것이다. 
  * 그러므로 $$A$$의 left nullspace: $$\bm{y}=c\begin{bmatrix} \green{e_{3,1}} \\ \green{e_{3,2}} \\ \green{e_{3,3}}\end{bmatrix}$$ 
  * 행렬 $$E$$안의 녹색 row는 $$\bm{y}^\top$$의 형태이며, 이를 다시 transpose 해주었다. 
  * $$R$$의 zero-row가 하나 뿐이므로 basis도 하나뿐이다. 

#### 일반화해보자!

* $$R$$의 zero-row\(빨간색\)의 개수\($$\red{m-r}$$\)만큼 대응되는 $$E$$의 row\(초록\)가 존재한다. 
* 아래 **결론 3**을 참조. 

{% hint style="info" %}
**결론 3:** $$A$$의 left nullspace는 다음과 같다 : 

* $$\bm{y}=c_1\begin{bmatrix} \green{e_{r+1,1}} \\ \green{e_{r+1,2}} \\ \vdots \\ \green{e_{r+1,m}}\end{bmatrix}+c_2\begin{bmatrix} \green{e_{r+2,1}} \\ \green{e_{r+2,2}} \\ \vdots \\ \green{e_{r+2,m}} \end{bmatrix}+\cdots +c_{\red{m-r}}\begin{bmatrix} \green{e_{m,1}} \\ \green{e_{m,2}} \\ \vdots \\ \green{e_{m,m}} \end{bmatrix}$$
* 각 벡터들이 left nullspace의 **기저**가 된다. 
{% endhint %}

#### 마지막으로 실제로 E를 어떻게 구하는 방법을 알아보자.

* Gauss-Jordan elimination을 활용하자. \(Lecture 3.에서 배웠다.\)
* $$E\begin{bmatrix} \blue{A_{m\times n}} \ | \ \green{I_{m\times m}} \end{bmatrix} \rightarrow \begin{bmatrix} \blue{R_{m \times n}} \ | \ \green{E_{m \times m}} \end{bmatrix} $$ 
  * $$E\blue{A_{m\times m}}=\blue{R_{m\times n}}$$
  * $$E\green{I_{m\times m}}=\green{E_{m\times m}}$$
* \(Recap\) Invertible square matrix의 경우에는 다음과 같았던 것을 기억하자. 
  * $$E\begin{bmatrix} {A_{m\times m}} \ | \ {I_{m\times m}} \end{bmatrix} \rightarrow \begin{bmatrix} {I_{m \times m}} \ | \ {A^{-1}_{m \times m}} \end{bmatrix} $$ 

