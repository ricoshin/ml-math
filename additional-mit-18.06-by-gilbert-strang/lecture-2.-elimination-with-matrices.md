# Lecture 2. Elimination with Matrices

## **Gaussian elimination\(가우스 소거법\)**

### 무엇?

* 이 방법을 통해 어떤 사이즈든지 관계없이 linear system을 풀 수 있음.
* MATLAB과 같은 모든 소프트웨어가 이 알고리즘을 사용. \(20년전 이야기?\)
* 이 알고리즘은 **해가 없는 경우 fail**할 수 있음.

### 다음 기본 행연산\(Row elementary operation\)을 사용

* **\(1\)** 두 행을 교환 **\(2\)** 행을 상수\(0 제외\)배 **\(3\)** 행을 상수배하여 다른 행에 더함

### 방법 및 절차 

#### **Forward elimination**

* **REF\(Row Echelon Form\)** 만들기
  * 왼쪽 위에서부터 대각 위치를 따라 pivot 찾기 
  * pivot 아래의 수들은 기본 행연산을 통해 전부 0으로 만들기
    * 항상 현재 row를 가지고 그 아래 row들을 clean up함 
  * 만약 pivot자리에 0이 나타나면 아래 행에서 찾아서 위치 교환
    * 당분간 위치 교환이 필요없는 행렬만 다룸 
* **성공조건**
  * 모든 행마다 0이 아닌 pivot을 찾으면 success!
  * pivot을 찾지 못하면 failed!
* 일단 여기서는 **square matrix**만 다루고 있음. 
  * 그래서 완벽한 upper triangular matrix를 만들 수 있음. 

#### **Back-substitution**

* 뒤에서부터 대입해서 푼다.

### elimination은 한마디로:$$A \rightarrow U$$

* 즉, **upper triangular matrix**로 만드는 과정. 
* 실제로는 **augmented matrix** 사용: $$[A|b] \rightarrow [U|c] $$ 
  * back-substitution을 위해 상수항도 같이 tracking 
* Scientific computing에서 **가장 흔한 연산**! 
* **Triangular matrix 형태는 많은 것을 말해줌.**
  * pivot을 전부 곱하면 **determinant**. 
  * pivot이 diagonal에 전부 없으면 **not invertible**. 

### **Elementary operation은 행렬로 나타낼 수 있다!**

#### 행렬의 오른쪽에서 곱할 때의 의

* \*\*\*\*$$A\bm{x}$$ **:** linear combination of the **columns** of $$A$$. 
  * $$A\bm{x}=\begin{bmatrix}  \vert &  & \vert \\  A_1 &  \cdots &A_n \\ \vert &  & \vert \end{bmatrix}\begin{bmatrix} x_1  \\  \vdots \\x_n \end{bmatrix} = x_1 \begin{bmatrix}  \vert  \\  A_1  \\ \vert \end{bmatrix} +\cdots + x_n \begin{bmatrix}  \vert  \\  A_n  \\ \vert \end{bmatrix}$$
* \*\*\*\*$$AX$$ **:** linear combination**s** **in columns**.
  * $$AX=A \begin{bmatrix}  \vert & \vert & & \vert  \\\bm{x}_1  & \bm{x}_2& \cdots  &\bm{x}_k \\ \vert & \vert & & \vert  \end{bmatrix} = \begin{bmatrix}  \vert & \vert & & \vert  \\A\bm{x}_1  & A\bm{x}_2& \cdots  &A\bm{x}_k \\ \vert & \vert & & \vert  \end{bmatrix}$$ 

#### 행렬의 왼쪽에서 곱할 때의 의미 

* \*\*\*\*$$\bm{x}A$$ **:** linear combination of the **rows** of $$A$$. 
  * $$\bm{x}A=\begin{bmatrix} x_1 & \dots &x_m \end{bmatrix} \begin{bmatrix} \text{---} A^\top_{1}\text{---} \\ \vdots \\ \text{---}A^\top_{m}\text{---}\end{bmatrix} = x_1 \begin{bmatrix}   \text{---} A^\top_{1}\text{---} \end{bmatrix}^\top +\cdots + x_n \begin{bmatrix}   \text{---} A^\top_{m}\text{---} \end{bmatrix}$$ 
* \*\*\*\*$$XA$$ **:** linear combination**s in rows**.
  * $$XA = \begin{bmatrix}  \text{---} \bm{x}_1 \text{---}  \\ \text{---} \bm{x}_2\text{---}  \\ \vdots \\ \text{---} \bm{x}_k \text{---} \end{bmatrix}A = \begin{bmatrix}  \text{---} \bm{x}_1A \text{---}  \\ \text{---} \bm{x}_2A\text{---}  \\ \vdots \\ \text{---} \bm{x}_k A \text{---}  \end{bmatrix}$$ 

#### Elementary row operation은 행렬의 왼쪽에서 곱하는 벡터/행렬로 표현 가능.  

* $$ R_2 - 3 R_1$$ \(2열에서 1열의 **-3**배를 더함\) / 그 역행렬은 **+3**배를 더하는 것. 
  *  $$E_{21} = \begin{bmatrix} 1 & 0 & 0 \\ -3 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}, E_{21}^{-1} = \begin{bmatrix} 1 & 0 & 0 \\ 3 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} $$
* Multiple step elimination을 다음과 같이 하나의 표현으로 압축 가능!
  * ​$$E_{32}E_{31}E_{21}A=U​$$
* \(​$$E$$의 subscript는 원래 행렬 ​AA에서 소거되는 원소의 위치를 의미.\) 
* \(왼쪽에서 오른쪽으로 갈수록 subscript의 숫자가 커짐.\) 
* 항상 현재 row를 가지고 그 아래 row들을 clean up하므로 다음을 만족한다.  
  * **clean up의 과정\(**$$E$$**\):** 대각 왼쪽 열들만 사용 \(lower triangular matrix\) 
  * **clean up의 결과\(**$$U$$**\)**: 대각 아래 행들만 제거 \(upper triangular matrix\) 
* $$E$$의 경우 개별 행렬 뿐 아니라 그 **composition**\( $$E_{32}E_{31}E_{21}$$ \)들도 마찬가지로 하삼각 행렬. 
  * 그리고 나중에 배우겠지만, 그 역행렬도 마찬가지로 하삼각 행렬:$$E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}=L$$ 

