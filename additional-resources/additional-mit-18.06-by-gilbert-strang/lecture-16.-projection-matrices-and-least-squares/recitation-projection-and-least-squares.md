# \(Recitation\) Projection & Least squares

### $$\mathbb{R}^n$$의 부분공간$$S$$와 $$S^\perp$$의 선형조합으로 모든$$\bm{v}\in\mathbb{R}^n$$ 을 만들 수 있는가? 

* \(Recitation\) [Orthogonal Vectors and Subspaces](https://www.youtube.com/watch?v=h9aDgvW59TU&list=PL221E2BBF13BECF6C&index=32)
* $$S^\perp$$는 "$$S$$ perp"라고 읽으며 $$S$$에 직교하는 모든 벡터의 집합을 의미한다. 
  * $$(S^\perp)^\perp=S$$
* Orthogonal complement, 직교 여공간이라고 부른다. 
* $$S$$를 column space로 하는 행렬을 $$A_S$$라고 하면, $$S^\perp$$ 는 $$A_S$$의 nullspace이다. 

#### 두 공간의 선형조합 $$S+S^\perp$$가 span하는 공간은?

* $$\mathcal{C}(A_S)$$ 의 basis를 $$\{\bm{v}_1,...,\bm{v}_r\}$$, $$\mathcal{N}(A_S)$$의 basis를 $$\{\bm{w}_1,...,\bm{w}_{n-r}\}$$ 라고 하자.
* $$S+S^\perp=(c_1\bm{v}_1+\cdots+c_r\bm{v}_r)+(c_{r+1}\bm{w}_1+\cdots c_n\bm{w}_{n-r})$$ 

#### $$S+S^\perp$$는 다음 $$n\times n$$행렬의 column space와 같다. 

* $$\begin{bmatrix} |&\cdots&|&|&\cdots&|\\  \bm{v}_1&\cdots&\bm{v}_r&\bm{w}_1&\cdots&\bm{w}_{n-r}\\|&\cdots&|&|&\cdots&| \end{bmatrix}$$
* 이 행렬은 square matrix이며, column은 모두 선형독립이다. 
* 역행렬이 존재하므로, 모든 출력에 대해 입력을 역계산 가능하다. 

#### 즉, $$\mathbb{R}^n$$의 모든 벡터는$$S+S^\perp$$의 선형조합으로 유일하게 결정가능하다. 

### 평면 $$x+y-z=0$$ 에 대한 $$\bm{b}$$의 orthogonal projection\(정사영\)을 찾아라. 

* \(Recitation\) [Projection into Subspaces](https://www.youtube.com/watch?v=t-n4a18AW08&list=PL221E2BBF13BECF6C&index=34)

![](../../../.gitbook/assets/image%20%2867%29.png)

* Lecture에서 projection이라고 했던 것은 사실상 orthogonal projection을 의미했다. 
* **그러나 모든 projection이 반드시 orthogonal한 것은 아니다.** 
  * **e.g. oblique projection**

#### 방법 1. 

* 위 평면을 span하는 basis를 골라잡아서 행렬 $$A$$를 만들어준다.
  * $$A=\begin{bmatrix} 1&1\\-1&0\\0&1\end{bmatrix}$$
*  $$P=A(A^\top A )^{-1}A^\top$$를 계산해준다. 

#### 방법 2.

* 위 평면에 수직인 직선\(직교여공간\)에 대한 행렬 $$N$$을 이용한다. 
  * $$N=\begin{bmatrix} 1\\1\\-1\end{bmatrix}$$
* 주어진 벡터는 각 orthogonal complements에 대한 정사영의 합으로 표현가능.
  * $$\bm{b}=P\bm{b}+P_N\bm{b}$$
  * $$P\bm{b}=(I-P_N)\bm{b}$$
  * $$P=I-P_N$$
* $$P_N=N(N^\top N)^{-1}N^\top$$을 구해서 대입해준다. 
  * $$\mathcal{C}(A)$$보다 $$\mathcal{C}(N)$$의 차원이 더 작아서,$$P$$보다 $$P_N$$의 계산이 더 간단하다. 
  * subspace가 평면의 방정식으로 주어져있는 경우, $$N$$을 바로 읽어낼 수 있다. 
    * 평면의 방정식의 계수

{% hint style="info" %}
Projection하고자 하는 space의 직교여공간의 차원이 더 작을 경우

* 직교여공간의 projection matrix를 구한뒤, Identity matrix에서 빼주면 계산이 더 간편! 
{% endhint %}

