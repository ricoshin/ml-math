# \(Recitation\) Basis and Dimension

### Reference

* 이 추가자료는 다음 자료들을 기반으로 작성되었다.  
  * [Basis and Dimension](https://www.youtube.com/watch?v=MMWqGD4Urso&list=PL221E2BBF13BECF6C&index=22)
  * [Computing the Four Fundamental Subspaces](https://www.youtube.com/watch?v=D8u1LV9CnCk&list=PL221E2BBF13BECF6C&index=24)

## 1. 다음 4개 벡터가 span하는 벡터공간의 차원과 그 기저를 찾아라. 

* $$\begin{bmatrix}1\\1\\-2\\0\\-1\end{bmatrix},  \begin{bmatrix}1\\2\\0\\-4\\1\end{bmatrix},  \begin{bmatrix}0\\1\\3\\-3\\2\end{bmatrix},  \begin{bmatrix}2\\3\\0\\-2\\0\end{bmatrix}$$

### Elimination은 다음 특성이 있다. 

* Elementary operation은 row들의 linear combination 통한 재조합이다. 
* 즉, column space는 변하지만,  row space는 변하지 않는다. 

### \(1\) 첫번째 방법은 벡터를 행렬의 row에 집어넣어서 elimination하는 것이다. 

* \(아래 행렬의 row space의 basis 찾기\)
* $$A=\begin{bmatrix}  1 & 1 & -2 & 0 & -1\\ 1 & 2 & 0 & -4 & 1\\ 0 & 1 & 3 & -3 & 2\\ 2 & 3 & 0 & -2 & 0  \end{bmatrix}\begin{matrix}\red{\leftarrow?} \\ \red{\leftarrow?} \\ \red{\leftarrow?} \\ \\  \end{matrix} \xRightarrow{\text{elimination}} \begin{bmatrix}   \fbox1 & 1 & -2 & 0 & -1\\  0 & \fbox1 & 2 & -4 & 2\\  0 & 0 & \fbox1 & 1 & 0\\  0 & 0 & 0 & 0 & 0   \end{bmatrix}\begin{matrix} \green\leftarrow \\ \green\leftarrow \\ \green\leftarrow \\ \\  \end{matrix}=R$$
* 벡터들이 행으로 존재하므로, 행들의 elementary operation은 row space를 유지시킨다. 
  * 벡터끼리 재조합하여 새로운 벡터를 만듦.
  * 선형계에서 방정식끼리 더하고 빼도 해는 같은 것과 유사. 
* 소거전\(원시행렬 $$A$$\)의 pivot row들\(왼쪽 초록색\)이 벡터공간의 basis가 된다. 
* 소거후\(소거행렬 $$R$$\)의 pivot row들\(오른쪽 초록색\)도 동일한 공간을 span한다. 
* Permutation\(row exchange\)이 있었을 경우에는? 
  * 소거후\($$R$$\)의 pivot row의 위치가 소거전\($$A$$\)과 다르다. 
  * $$A$$에서 basis를 찾으려면 소거과정에서의 row의 위치변경을 고려해야 한다. 
* 즉, permutation을 고려할 필요없고, 형태도 더 간단한, $$R$$에서 basis를 찾는 것이 유리하다. 

### \(2\) 두번째 방법은 벡터를 행렬의 column에 집어넣어서 elimination하는 것이다.

* \(아래 행렬의 column space의 basis 찾기\) 
* $$A=\begin{array}{c}\left[ \begin{array}{c c c c}   1 \\ 1 \\ -2 \\ 0 \\ -1 \end{array} \begin{array}{cccc} 1 \\ 2 \\ 0 \\ -4 \\ 1 \end{array} \begin{array}{cccc} 0 \\ 1 \\ 3 \\ -3 \\ 2 \end{array}  \begin{array}{cccc} 2 \\ 3 \\ 0 \\ -2 \\ 0  \end{array} \right] \\ \begin{array}{ccccc}  & \green\uparrow & \ \ \ \green\uparrow & \  \ \  \green\uparrow & \phantom{-2} & \end{array}\end{array}\xRightarrow{\text{elimination}}   \begin{array}{c}\left[ \begin{array}{c c c c}   \fbox1 \\ 0 \\ 0 \\ 0 \\ 0 \end{array} \begin{array}{cccc} 1 \\ \fbox1 \\ 0 \\ 0 \\ 0 \end{array} \begin{array}{cccc} 0 \\ 1 \\ \fbox1 \\ 0 \\ 0 \end{array}  \begin{array}{cccc} 2 \\ 1 \\ 2 \\ 0 \\ 0  \end{array} \right] \\  \ \begin{array}{ccccc}  &   \ \  \red\times &    \  \red\times &    \ \red\times & \phantom{-2} & \end{array}\end{array}=R$$ 
* Row operation은 column space를 변화시킨다. 
  * $$\mathcal{C}(A) \neq \mathcal{C}(R)$$
* 소거전의 pivot column들이\(왼쪽 초록색\) 벡터공간의 basis가 된다. 
* 소거후의 pivot column들\(오른쪽 빨간색\)은 더이상 같은 공간을 span하지 않는다. 
* Permutation\(row exchange\)이 있었을 경우에는? 
  * 소거후\($$R$$\)의 pivot row의 위치가 소거전\($$A$$\)과 다르다. 
  * $$A$$에서 basis를 찾으려면 소거과정에서의 row의 위치변경을 고려해야 한다. 
* 즉, permutation을 고려할 필요없고, 형태도 더 간단한, $$R$$에서 basis를 찾는 것이 유리하다. 

### 결론: row/column space의 basis를 구할때는 위의 초록색 화살표만 보면 된다!  

## 다음 행렬의 4대 부분공간의 기저와 차원을 찾아라. 

* $$B=LU=\begin{bmatrix} 1 & 0 & 0 \\ 2 & 1 & 0 \\ -1 & 0 & 1 \end{bmatrix}\begin{bmatrix}\fbox5 & 0 & 3 \\ 0 & \fbox1 & 1 \\ 0 & 0 & 0 \end{bmatrix}$$

### Column space\($$L$$을 활용\) 

#### 원래 행렬 $$B$$를 계산한 다음, pivot column을 구하면 된다. \(1, 2번째 column\) 

* $$B=\begin{bmatrix} 1 & 0 & 0 \\ 2 & 1 & 0 \\ -1 & 0 & 1 \end{bmatrix}\begin{bmatrix}\fbox5 & 0 & 3 \\ 0 & \fbox1 & 1 \\ 0 & 0 & 0 \end{bmatrix}=\begin{bmatrix}\red 5 & \blue0 & 3 \\ \red{10} & \blue1 & 7 \\ \red{-5} & \blue0 & -3 \end{bmatrix}$$
* **기저:** $$\left\{ \begin{bmatrix} \red5 \\ \red{10} \\ \red{-5} \end{bmatrix} , \begin{bmatrix} \blue{0} \\ \blue{1} \\ \blue{0} \end{bmatrix}\right\}$$

#### 그러나, $$B=LU$$상태에서 $$L$$의 pivot column도 역시  column space의 기저가 된다! 

* $$B$$는 $$U$$의 row operation의 결과이다. 그러므로 row space가 보존된다. 
* $$B$$는 $$L$$의 column operation의 결과이다. 그러므로 column space가 보존된다. 
  * $$B$$와 $$L$$의 column space가 같고, 같은 기저로 표현될 수 있다! 
* $$B=\begin{bmatrix} \red1 & \blue0 & 0 \\ \red2 & \blue1 & 0 \\ \red{-1} & \blue0 & 1 \end{bmatrix}\begin{bmatrix}\fbox5 & 0 & 3 \\ 0 & \fbox1 & 1 \\ 0 & 0 & 0 \end{bmatrix}=\begin{bmatrix} 5 & 0 & 3 \\   {10} & 1 & 7 \\ {-5} & 0 & -3 \end{bmatrix}$$
* **기저:** $$\left\{ \begin{bmatrix} \red1 \\ \red2 \\\red{ -1} \end{bmatrix} , \begin{bmatrix} \blue0 \\ \blue1 \\ \blue0 \end{bmatrix}\right\}$$

### Nullspace\($$L$$을 활용\)

* Special solution을 구한다.
* **기저:** $$\left\{ \begin{bmatrix} -3/5 \\ -1 \\1 \end{bmatrix} \right\}$$

### Row space\($$U$$을 활용\) 

* $$U$$의 pivot row를 그대로 적어주면 된다. 
* **기저:** $$\left\{ \begin{bmatrix} 5 \\ 0 \\ 3 \end{bmatrix} , \begin{bmatrix} 0 \\ 1 \\ 1\end{bmatrix}\right\}$$

### Left nullspace\($$L^{-1}$$를 활용\)  

* $$L^{-1}$$에서$$U$$의 zero-row에 대응하는 row vector를 적어주면 된다.  
* \(주의: $$E$$와 혼동해서 $$L$$을 그대로 쓰면 안됨! 역행렬을 취해줘야 $$E$$가 된다.\)  
* **기저:** $$\left\{ \begin{bmatrix} 1 \\ 0 \\1 \end{bmatrix} \right\}$$

### 결론: $$LU$$분해의 $$L$$을 이용해서 column space와 left nullspace를 구할 수도 있다.  





