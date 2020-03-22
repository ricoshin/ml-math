# \(Recitation\) Matrix spaces

### 1. 벡터$$\begin{bmatrix} 2 \\ 1 \\ 1 \end{bmatrix}$$를 영공간에 포함하는 2x3행렬의 집합이 있다. 

#### Vector space임을 보여라.  

* $$A$$와 $$B$$가 해당 부분공간의 행렬이라고 하자.
  * $$A\begin{bmatrix} 2 \\ 1 \\ 1 \end{bmatrix}=\begin{bmatrix} 0 \\ 0 \end{bmatrix}$$, $$B\begin{bmatrix} 2 \\ 1 \\ 1 \end{bmatrix}=\begin{bmatrix} 0 \\ 0 \end{bmatrix}$$ 
* **덧셈에 대해 닫혀있는지 확인:** 
  * \*\*\*\*$$(A+B)\begin{bmatrix} 2 \\ 1 \\ 1 \end{bmatrix}=A\begin{bmatrix} 2 \\ 1 \\ 1 \end{bmatrix}+B\begin{bmatrix} 2 \\ 1 \\ 1 \end{bmatrix}=\begin{bmatrix} 0 \\ 0 \end{bmatrix}+\begin{bmatrix} 0 \\ 0 \end{bmatrix}=\begin{bmatrix} 0 \\ 0 \end{bmatrix}$$
* **실수곱에 대해 닫혀있는지 확인:** 
  * \*\*\*\*$$(cA)\begin{bmatrix} 2 \\ 1 \\ 1 \end{bmatrix}=c\left(A\begin{bmatrix} 2 \\ 1 \\ 1 \end{bmatrix}\right)=c\begin{bmatrix} 0 \\ 0 \end{bmatrix}=\begin{bmatrix} 0 \\ 0 \end{bmatrix}$$ 
* **vector space이다!**

#### 기저를 찾아라. 

* 해당 부분공간에 존재하는 행렬의 각 row는 다음을 만족한다.
  * $$\begin{bmatrix} a & b & c \end{bmatrix}\begin{bmatrix}2 \\ 1 \\ 1 \end{bmatrix}=\begin{bmatrix} 0 \end{bmatrix}$$,  $$2a+b+c=0$$ 
* 행렬의 row는 다음과 같이 다시 쓸 수 있다. 
  * $$\begin{bmatrix} a & b & -2a-b \end{bmatrix}=\begin{bmatrix} a & 0 & -2a \end{bmatrix}+\begin{bmatrix} 0 & b & -b \end{bmatrix}$$ 
* 이는 다음 두 row의 linear combination이다: 
  * $$\begin{bmatrix} 1 & 0 & -2 \end{bmatrix},\begin{bmatrix} 0 & 1 & -1 \end{bmatrix}$$ 
* 기저는 다음과 같다. 
  * $$\begin{bmatrix} 1 & 0 & -2 \\ 0&0&0 \\\end{bmatrix},\begin{bmatrix} 0 & 1 & -1 \\ 0&0&0 \end{bmatrix}, \begin{bmatrix} 0&0&0 \\ 1 & 0 & -2 \\\end{bmatrix},\begin{bmatrix}  0&0&0 \\0 & 1 & -1 \end{bmatrix}$$ 

### 2. 벡터$$\begin{bmatrix} 2 \\ 1  \end{bmatrix}$$를 행공간에 포함하는 2x3행렬의 집합은 어떠한가? 

#### 벡터공간인지 확인하기 위해서 할 수 있는 가장 간단한 테스트!

* 영행렬을 포함하는가?

#### 영행렬을 포함하지 않는다. 

* $$\begin{bmatrix} 0 & 0 & 0 \\ 0&0&0 \end{bmatrix}\bm{x}=\begin{bmatrix} 2 \\ 1 \end{bmatrix}$$ 을 만족하는 $$\bm{x}$$가 존재하지 않는다. 

