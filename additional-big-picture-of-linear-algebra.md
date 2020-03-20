---
description: (추가자료) 선형대수의 빅픽쳐
---

# \(Additional\) Big Picture of Linear Algebra

* \(경고\) 수정중. 내용 검증요.
  * 유의사항. inverse는 어떻게 매핑되는가?



* 선형대수의 큰 그림을 한번 살펴보자.
* 다음은 Gilbert Strang 교수님이 처음 만드신 것으로 알고 있는 선형대수의 4가지 subspace이다.
  * _**Four Fundamental Subspaces**_ 
    * Column space $$\mathcal{C}(A)$$
    * Null space $$\mathcal{N}(A)$$
    * Row space $$\mathcal{C}(A^\top) \; or \; \mathcal{R}(A)$$
    * Left null space $$\mathcal{N}(A^\top)$$

![https://kevinbinz.com/2017/02/20/linear-algebra/](.gitbook/assets/image%20%28129%29.png)

* 다음은 함수의 가역성을 좀 더 강조하고 있는 그림이다. \(양방향 화살표만이 서로 1:1 대응이다\)
  * Row space와 Column space는 원소끼리 1:1 대응이되므로 왔다갔다 할 수 있다.
  * Null space와 Left null space는 한번 가면 모든 점들이 $$\bm{0}$$으로 수렴한다.
    * 한번 $$\bm{0}$$으로 collapse되게 되면 돌아갈 수가 없다.
    * 우리는 어디서 왔는지 기억하지만, 수학적으로는 비가역적이다.
      * 한번 0을 곱해버리면 어떤 수를 곱해도 다시 0에서 빠져나올 수 없는 것과 같음. 
    * 결국 행렬 $$A$$의 null space가 $$\bm{0}$$만 존재해야  항상 다시 돌아갈 수 있다.\($$A^{-1}$$이 존재\)
    * 반대로 행렬 $$A^\top$$의 null space가 $$\bm{0}$$만 존재해야  

![https://sn1729.com/2016/11/22/linear-algebra-101-vector-spaces/](.gitbook/assets/image%20%2873%29.png)

* 아래 그림은 subspace간의 orthogonality를 좀 더 실감나게 보여준다. 
  * 다른 그림들은 사각형들이 서로 평면에서 직각을 이루고 있다.
    * 그러나 너무 추상화되어 있어서 다소 counter-intuitive할 수 있다고 생각한다.
  * 그러나 아래 그림은 좀 더 real하게 다가올 수 있을 것 같다.
    * 3차원이라고 하면 실제로 저렇게 서로 수직관계를 가진다.
      * column space가 2차원이면 

![https://statweb.stanford.edu/~candes/teaching/math104/](.gitbook/assets/image%20%2823%29.png)

* 비슷한 맥락으로 오래 전 직접 그런 그림.  
  * 실제 \(2x3\)행렬을 가지고 예시를 직접 만들어본 내용. 

![](.gitbook/assets/image%20%2848%29.png)

* 위의 내용들은 column picture들?

