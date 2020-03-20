# Lecture 13. Quiz 1 Review

### 강의에서 나오는 문제들 중에서 중요한 것들만 풀어보자.

#### \(1\)$$A\bm{x}=\begin{bmatrix} 2 \\ 4 \\ 2\end{bmatrix}$$을 만족하는 해가 $$\bm{x}=\begin{bmatrix} 2 \\ 0 \\0\end{bmatrix} +c\begin{bmatrix}1\\1\\0\end{bmatrix}+d\begin{bmatrix}0\\0\\1\end{bmatrix}$$일때, 행렬 $$A$$를 구하여라. 

* \(1\) particular solution인 $$\begin{bmatrix} 2\\0\\0\end{bmatrix}$$는 $$A\bm{x}=\bm{b}\left( =\begin{bmatrix} 2\\4\\2 \end{bmatrix} \right)$$를 만족하고,
* \(2\) special solution인 $$\begin{bmatrix}1\\1\\0\end{bmatrix},\begin{bmatrix}0\\0\\1\end{bmatrix}$$ 들은 $$A\bm{x}=\bm{0}$$를 만족한다. 
* \(1\)에 의하여 $$A$$의 첫번째 행은 $$\begin{bmatrix} 1\\2\\1\end{bmatrix}$$임을 알 수 있다. 
* \(2\)에 의하여, $$A$$의 두번째 행은 $$\begin{bmatrix} -1\\-2\\-1\end{bmatrix}$$ 이고, 세번째 행은 $$\begin{bmatrix} 0\\0\\0\end{bmatrix}$$ 임을 알 수 있다. 
* **Ans:** $$A=\begin{bmatrix} 1&-1&0\\2&-2&0\\1&-1&0\end{bmatrix}$$

#### \(2\) 다음 행렬 $$B=\begin{bmatrix} 1&1&0\\0&1&0\\1&0&1\end{bmatrix}\begin{bmatrix}1&0&-1&2\\0&1&1&-1 \\ 0&0&0&0\end{bmatrix}$$의 nullspace를 구하여라.

* $$B=CD$$일때, $$C$$의 역행렬이 존재하면 $$\mathcal{N}(B)=\mathcal{N}(CD)=\mathcal{N}(D)$$이다!
  * $$\text{if }CD\bm{x}=\bm{0} \text{, then } D\bm{x}=C^{-1}\bm{0}=\bm{0}$$
  * 그러므로,  **두번째 행렬**$$D$$**에 대한 nullspace**를 구하면 된다.  
* $$\text{Basis for }\mathcal{N}(B)=\left\{ \begin{bmatrix} 1\\-1\\1\\0\end{bmatrix}, \begin{bmatrix} -2 \\ 1\\0\\1\end{bmatrix} \right\}$$

#### \(3-1\)$$A$$와 $$-A$$는 같은 4대 부분공간을 갖는가? \(Yes / No\)

* **Yes.** 공간들을 span하는 basis에 minus를 취해도 공간은 변하지 않는다. 

#### \(3-2\) 만약 $$A$$와 $$B$$가 같은 4대 부분공간을 갖는다면 $$A=cB$$인가? 

* **No.** $$A$$와 $$B$$가 $$m\times m$$의 역행렬이 존재하는 서로 다른 행렬일 경우에도 4대 부분공간이 같다. 
* 둘다 Row/column space는 $$\mathbb{R}^m$$ 전체공간이고, 두 개의 nullspace에는 모두 영벡터만 존재한다. 

### \(Recitation\) complete solution 구하는 또다른 방법

#### 다음과 같은 augmented matrix\(REF 상태\)의 해를 구해보자.  

* $$U=\left[ \begin{array} {ccc|c} 1 & 1&1 & 2 \\0&1&2&1\\0&0&0&0\end{array} \right]$$ 

#### RREF를 만들어서 기존의 방법으로 바로 구하면: 

* $$R=\left[ \begin{array} {ccc|c} 1 & 0&-1 & 1 \\0&1&2&1\\0&0&0&0\end{array} \right]$$
* $$\bm{x}=\begin{bmatrix}1\\1\\0\end{bmatrix}+c\begin{bmatrix} 1\\-2\\1\end{bmatrix}$$

#### Back-substitution으로 구해보자.

* 세번째 방정식: $$x_3$$이 어떤 수가 되어도 관계없으므로 $$x_3=c$$로 두자. 
* 두번째 방정식: $$x_2=1-2x_3=1-2c$$ 
* 세번째 방정식: $$x_1=2-x_2-x_3=2-(1-2c)-c=1+c$$
* $$c$$가 곱해지는 항과 그렇지 않은 항을 분해하면: $$\begin{bmatrix} 1+c \\1-2c\\c\end{bmatrix}=\begin{bmatrix}1\\1\\0\end{bmatrix}+c\begin{bmatrix} 1\\-2\\1\end{bmatrix}$$
* **같은 solution에 도달한다!**





