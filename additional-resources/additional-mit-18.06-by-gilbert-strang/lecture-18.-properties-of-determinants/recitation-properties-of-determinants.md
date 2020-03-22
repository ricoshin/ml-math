# \(Recitation\) Properties of Determinants

## 다음 행렬의 determinant를 구하라. 

### Vandermonde Matrix

* $$\begin{aligned} |V|&=\begin{vmatrix} 1&a&a^2\\1&b&b^2\\1&c&c^2\end{vmatrix}=\begin{vmatrix} 1&a&a^2\\0&b-a&(b-a)(b+a)\\0&c-a&(c-a)(c+a)\end{vmatrix}=(b-a)(c-a)\begin{vmatrix} 1&a&a^2\\0&1&b+a\\0&1&c+a\end{vmatrix}\\ &=(b-a)(c-a)\begin{vmatrix} 1&a&a^2\\0&1&b+a\\0&0&c-b\end{vmatrix}=(b-a)(c-a)(c-b)\end{aligned}$$
* 이런 모양의 행렬\(각 행이 초항이 1인 등비수열로 구성\)을 **방데르몽드 행렬**이라고 한다.
  * 모든 $$i, j$$에 대하여 다음과 같이 쓸 수 있다: $$V_{i,j}=\alpha_i^{j-1}$$
* 이 행렬의 determinant를 **방데르몽드 행렬식**이라고 한다.
  * 일반식으로 쓰면 다음과 같다: $$\displaystyle \det V=\prod_{1\leq i\leq j\leq n}(\alpha_j -\alpha_j)$$

### Rank 1 matrix

* $$C=\begin{bmatrix} 1\\2\\3\end{bmatrix}\begin{bmatrix} 1&-4&5\end{bmatrix}$$
* Rank 1 matrix는 linearly dependent한 열이 존재하며, singular matrix이다.
* 즉, $$|C|=0$$이다. 

### Skew-symmetric matrix

* $$D=\begin{bmatrix} 0&1&3 \\ -1&0&4 \\ -3&-4&0 \end{bmatrix}$$
* 위와 같이, $$D^\top=-D$$를 만족하는 행렬을 **비대칭행렬** 또는 **반대칭행렬**이라고 한다. 
  * **skew-symmetric** or **anti-symmetric** matrix
* 비대칭행렬은 다음을 만족한다:
  * $$|D^\top|=|-D|=(-1)^n|D|$$
  * 행렬식 안의 마이너스 부호가 바깥으로 나오려면 모든 행마다 개별적으로 나와야 한다. 
  * 행의 개수만큼 부호가 바뀌므로 $$(-1)^n$$을 곱해준 것이 최종 부호가 된다. 
* 만약 정방행렬\($$n \times n$$\) 의 $$n$$이 홀수이면 다음을 만족한다:
  * $$|D^\top|=-|D|$$
  * Property \(10\)에 의$$|D^\top|=|D|$$이므로, $$|D|=-|D|$$
  * 음수화를 해도 같은 수는 0뿐이다.
* $$D$$는 $$n$$이 홀수인 비대칭행렬이므로, $$|D|=0$$이다. 

