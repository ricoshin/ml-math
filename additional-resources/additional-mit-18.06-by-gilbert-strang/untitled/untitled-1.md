# \(Discussion\) Project-then-scale!

## Normal equation에서 $$\bm{x}$$와 $$\hat{\bm{x}}$$이 다른 이유 

### 왜 $$A\bm{x}=\bm{b}$$의 양변에 $$A^\top$$을 곱해주면 $$\bm{x}$$가 $$\hat\bm{x}$$으로 달라질까? 

$$
A\bm{x}=\bm{b} \quad \Rightarrow \quad A^\top A \hat\bm{x}=A^\top\bm{b}
$$

* 일반 대수학의 경우와 비교해보면 이해가 잘 가지 않을 수 있다. 
  * $$3x=6 \quad \Rightarrow \quad 2\cdot3x=2\cdot 6$$
  * 좌우변의 $$x=2$$가 달라지지 않는다. 
* 물론 projection에서 시작하여 least squares로 이어지는 일련의 과정을 따라갈 수는 있다.
* 그러나, 대수적으로는 결국 양변에 $$A^\top$$을 곱하는 행위 아니던가? 
  * 실제로 transpose를 곱한다는 action이 어떤 물리적 의미를 지니는지 궁금하지 않을 수 없다. 
  * 이 단일 연산의 의미를 이해한다면 긴 직관의 사슬을 의미있게 단축시킬 수 있을 것이다. 

### Big picture에서 숨은 단서를 찾아보자. 



![\[Fig. 1\]](../../../.gitbook/assets/image%20%2811%29.png)

* Nullspace는 선형변환$$A$$의 과정에서 출력공간의 원점으로 빨려들어간다.
* Rowspace의 모든 점들은 column space로 선형변환을 통해 매핑된다. 

#### 이 두 변환 사이에 우리가 놓치고 있는 그림이 있다. 

![\[Fig. 2\] Pink plane&#xC774; nullspace&#xC774;&#xB2E4;. &#xC774;&#xC5D0; &#xD3C9;&#xD589;&#xD55C; &#xBAA8;&#xB4E0; &#xD3C9;&#xBA74;&#xB4E4;&#xB3C4; column space&#xC758; &#xD55C; &#xC810;&#xC73C;&#xB85C; &#xBE68;&#xB824;&#xB4E4;&#xC5B4;&#xAC04;&#xB2E4;.](../../../.gitbook/assets/nullspace_3_to_1.gif)

* 위의 두 변환을 선형성의 법칙 안에서 동시적으로 상상해보면 그 사이의 missing piece를 찾을 수 있다. 
* **Nullspace가 한 점으로 빨려들어간다는 것은 그와 평행한 모든 공간에도 같은 일이 일어난다는 뜻이다.** 
  * 선형성을 유지하려면 그렇게 될 수 밖에 없다.
  * Evenly-spaced grid를 유지하려면 row space를 향해서 모든 공간이 짜부러져 들어와야 한다. 
* **즉, Nullspace와 평행인 평면은 column space에서 같은 점으로 매핑**된다. 
  * 그 점\(출력\)에 대한 입력을 역추적하면 다시 원래 평면\(무수히 많은 해\)에 도달하게 된다. 
  * complete solution이 nullspace을 평행이동한 꼴로 나오는 이유가 바로 이것이다. 
* 선형변환 $$A^\top$$의 과정에서도 마찬가지로 대칭적인 상황이 발생한다. 

#### 선형대수에서는 행렬곱이 공간의 원소들에 대하여 차별적으로 이루어진다!

* 일반 대수학에서 상수 $$c$$와의 곱은 모든 수에 같은 작용을 한다.
  * $$cx$$의 결과는 모든 $$x$$에 대해 동일하다. 
* 그러나 선형대수의 행렬곱은 마치 수의 범위에 따라 다른 수가 곱해지는 것과 같다. 
  * $$C\bm{x}$$는 $$\bm{x}$$의 범위에 따라 차등적인 연산결과를 보여준다. 
  * $$C\bm{x}=C(\bm{x}_{particular}+\bm{x}_{nullspace})=C\bm{x}_{particular}+\underbrace{C\bm{x}_{nullspace}}_{\bm{0}}$$
  * \[주의\] 실제로 선형변환은 동일하지만, 그 결과가 차별적이라는 것. 
* 즉, 방정식의 양변에 같은 행렬을 곱하더라도, 입력벡터의 위치에 따라 결과는 달라질 수 있음. 
  * $$\bm{x}$$를 $$\hat\bm{x}$$로 새롭게 표현하는 이유.  

### 이제 $$A\bm{x}$$와 $$A^\top \bm{y}$$가 어떤 의미를 갖는지 다시 한번 생각해보자. 

![\[Fig. 3\] Projection&#xACFC; scaling&#xC774; &#xB3D9;&#xC2DC;&#xC5D0; &#xC77C;&#xC5B4;&#xB098;&#xB294; &#xADF8;&#xB9BC;. \(&#xCD5C;&#xC885;&#xACB0;&#xACFC;&#xB294; project&#xD55C; &#xD6C4;&#xC5D0; scaling&#xD558;&#xB294; &#xAC83;&#xACFC; &#xB3D9;&#xC77C;\)](../../../.gitbook/assets/image%20%28152%29.png)

* $$A$$를 곱한다는 것은 $$\mathcal{C}(A^\top)$$에 대한 projection 상의 모든 벡터를 같은 점에 매핑한다는 의미이다. 
* $$A^\top$$를 곱한다는 것은 $$\mathcal{C}(A)$$으로의 projection 상의 모든 벡터를 같은 점에 매핑한다는 의미이다. 
  * 보라색 점선을 포함하는 직선 위의 모든 벡터들이 같은 점으로 매핑.

#### 수식적으로 생각해보자. 

* $$A^\top\bm{x}=\begin{bmatrix} \text{---} \ \bm{a}_1^\top \ \text{---} \\ \vdots \\ \text{---} \ \bm{a}_n^\top \ \text{---}\end{bmatrix}\bm{x}=\begin{bmatrix} \bm{a}_1^\top\bm{x} \\ \vdots \\ \bm{a}_n^\top\bm{x}\end{bmatrix}=\begin{bmatrix} \bm{a}_1\cdot \bm{x} \\ \vdots \\ \bm{a}_n\cdot\bm{x}\end{bmatrix}$$
* $$A^\top$$을 곱한다는 것의 의미는? 
  * $$A$$의 column vector들과의 dot product를 각 성분으로 하는 벡터를 구한다는 의미. 
* 좀 더 구체적으로 말해, **출력벡터의 성분**은? 
  * \(1\) 각각의 column vector에 대해 project하고, \(2\) 그 것의 길이만큼 scaling한 것. 
    * scaling은 모든 벡터에 대해 같은 비율로 일어남. 
  * Lec. 17-1.에서 배웠듯이,  $$Q^\top$$인 경우에는 \(1\)에서 멈춘 것과 같다. \(basis의 길이가 모두 1\) 
    * \(아래의 첫번째 링크 참조\) 
  * 한마디로 이야기 하면: **Project-then-scale!**
  * 이것은 **dot product의 duality 개념**을 **고차원의 column space로 확장**한 것이다. 
    * \(아래의 두번째 링크 참조\)

{% page-ref page="../lecture-17.-orthogonal-matrices-and-gram-schmidt.md" %}

{% page-ref page="../../additional-essence-of-linear-algebra-by-3blue1brown/part-ii.-e9-e15.md" %}

#### 기하학적으로 생각해보자. 

![\[Fig. 4\] A&#xAC00; 3x2 &#xD589;&#xB82C;, &#xC989; column space&#xAC00; 2&#xCC28;&#xC6D0;&#xC778; &#xC0C1;&#xD669;&#xC5D0;&#xC11C;&#xC758; A transpose&#xC758; &#xC758;&#xBBF8;.](../../../.gitbook/assets/image%20%28158%29.png)

* **같은 projection을 갖는 모든 벡터들\(** $$\bm{b}^{(k)}$$; Fig. 4의 보라색 벡터\)**은 같은 결과벡터** $$A^\top\bm{b}^{(k)}$$ **를 갖는다!**
  * 그리고 이 벡터들의 집합은 평면 위의 모든 $$\bm{b}^{(k)}$$의 $$\mathcal{C}(A)$$에 대한 **projection인** $$\bm{p}$$**를 포함**한다.
    * $$A^\top\bm{b}^{(3)}=A^\top\bm{b}^{(2)}=A^\top\bm{b}^{(1)}=A^\top\bm{b}^{(0)}=A^\top\bm{p}=A^\top A\hat{\bm{x}}$$
* $$A^\top$$를 곱한다는 것의 의미는 $$A$$의 basis 행벡터들에 대해 project-then-scale을 하는 것이다! 
  * Projection 벡터들의 합\($$\sum{\bm{p}}_i=\sum \frac{\bm{a}_i^\top\bm{b}^{(k)}}{\bm{a}_i^\top\bm{a_i }}\bm{a}_i$$\): \[Fig. 4\] 좌측 그림의 빨간색$$\red {\text{x}}$$
  * 이어서 Scaling까지 마친 벡터들의 합\( $$\sum \frac{\bm{a}_i^\top\bm{b}^{(k)}} {\Vert\bm{a}_i{\Vert}}\bm{a}_i$$ \): \[Fig. 4\] 좌측 그림의 주황색$$\orange {\text{x}}$$ 
  * 이 합벡터를 $$A$$의 basis를 기준 좌표계로 삼아서 표현한 것이 출력벡터가 된다. 
* **즉,**$$A\bm{x}=\bm{b}$$**를 만족하는** $$\bm{x}$$**가 존재하지 않을때 양변에** $$A^\top$$**를 곱해주는 의미는:**
  * 양변의 벡터들을 project-then-scale한 뒤, 새로운 좌표계로 해석. 
  * 이러한 선형변환을 통해, 양변을 만족시키는 새로운 해 $$\hat{\bm{x}}$$가 존재하게 됨.

### 만약 두 변환을 번갈아가면서 반복한다면\($$\cdots AA^\top A A^\top A  A^\top A\bm{x}$$\)? 



![\[Fig. 4\] ](../../../.gitbook/assets/image%20%2840%29.png)

#### Lec. 10.에서 한번 다루었던 내용이다. 

{% page-ref page="../lecture-10.-the-four-fundamental-subspaces/" %}

* 처음 시작은 row space에서 하지 않더라도, 그 결과는 column space에 떨어지게 된다. 
* 한 번 subspace 안으로 들어오면 계속해서 두 subspace 안에서만 왕복하게 된다. 
* e.g. $$\begin{bmatrix} 1 \\ 2 \\ 1 \end{bmatrix} \xrightarrow{A} \begin{bmatrix} 6 \\ 12 \end{bmatrix} \xrightarrow{A^\top} \begin{bmatrix} 30 \\ 60 \\ 30 \end{bmatrix} \xrightarrow{A} \begin{bmatrix} 180 \\ 360 \end{bmatrix} \xrightarrow{A^\top} \cdots$$
* 계속 일정 크기만큼 증폭되지만 같은 subspace안에 머물러 있다. 

#### 위에서 배운 내용과 연결시켜서 지식을 확장해보자.

* 위 행렬곱은 row space와 column space를 오가며, **project-then-scale**을 반복하는 것이다. 
* **Projection**은 한번만 수행하면 그 이후로는 계속 두 subspace안에 존재하므로, 아무 효과가 없다. 
* 두 subspace를 왕복하는 동안 **Scaling만 계속 반복**된다.  



