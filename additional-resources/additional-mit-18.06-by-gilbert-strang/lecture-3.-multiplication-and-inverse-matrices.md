# Lecture 3. Multiplication and Inverse Matrices

### **매트릭스 곱\(**$$AB=C$$**\)의 4가지 방법** 

1. **Regular way**: 우리가 고등학교때 배웠던 dot product 이용하는 방법. 
2. **Column way**: columns of $$C$$are linear combinations of the columns of $$A$$.
3. **Row way**: rows of $$C$$ are linear combinations of the row of $$B$$
4. **여러 layer의 full-sized 행렬의 합**: Sum of \($$i^{th}$$columns of $$A$$\) $$\times$$\($$i^{th}$$rows of $$B$$\) **\(중요\)**
5. **Block matrix multiplication**

### **Inverses**

* $$AA^{-1}=A^{-1}A=I$$: **left inverse**와 **right inverse**가 **같아야 함**.

#### **square matrix**의 경우

* left inverse를 구할 수 있다면\(invertible\), right inverse와 무조건 같다. 
* **Singular case**
  * \*\*\*\*$$A\bm{x}=\bm{0}$$인 $$\bm{x}$$\($$\neq \bm{0}$$\)가 존재하면 no inverse. 
    * **Reasoning**: inverse를 양변에 곱하면 $$\bm{x}=A^{-1}\bm{0}=\bm{0} $$ \(모순\) 
* **Non-singular case**
  * **Gauss-Jordan elimination**
    * 역행렬 구하는 방법! \(if possible\) 
    * solve 2 equations at once
    * $$[\;A\;|\;I\;] \xrightarrow{E} [\;I\; | \;A^{-1\;} ]$$\*\*\*\*

#### **rectangular matrix**의 경우

* left inverse를 구하더라도 right inverse와 shape 자체가 다르다. 
* 근본적으로 **not invertible**

### _**\(Additional\)**_ Remark 

* **Gaussian elimination**: 
  * **Forward elimination**\(REF 만들기\) + **Back-substitution**
  * 실제 컴퓨터로 계산할 때는 **효율적인 비용** 때문에 선호되는 경우가 많음.  
  * rank를 확인하는 경우 등 REF에서 멈춰도 이미 밝혀지는 정보들이 있음. \(RREF=투머치\) 
  * 그러나 해가 명시적으로 보이지 않아서 추가적인 **대입과정**\(back-substitution\)이 필요. 
* **Gauss-Jordan elimination**: 
  * **Forward elimination**\(REF 만들기\) + **backward elimination**\(RREF 만들기\)
  * Gaussian elimination의 forward elimination까지 수행 후에, 좀 더 진행. 
  * 작은 시스템을 손으로 풀 때 등은 시스템의 **해를 보다 명시적으로 보여주는** 장점. 
  * 그러나 Gaussian elimination에 비해 계산 절차가 늘어나 **round-off에 의한 오차**가 더 커짐. 

