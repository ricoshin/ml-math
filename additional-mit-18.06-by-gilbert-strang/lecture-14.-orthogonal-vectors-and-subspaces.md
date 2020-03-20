# Lecture 14. Orthogonal Vectors and Subspaces

'**Orthogonal하다\(직교한다\)'의 의미를 알아보자!**  

* **벡터**들이 orthogonal하다는 것은?
* **부분공간**들이 orthogonal하다는 것은?
* **기저**들이 orthogonal하다는 것은?

## Orthogonal vectors

* Orthogonal은 perpendicular\(직각의, 수직의\)의 다른 표현이다. 
  * Orthogonal이 좀 더 수학적이고 일반적인 표현이라는 것이 중론. 
  * 지금 상황에서는 둘 다 interchangeably 사용가능. 

![\[Fig. 1\]](../.gitbook/assets/image%20%28132%29.png)

* 위 그림\[Fig. 1\]과 같이 서로 orthogonal한 두 벡터 $$\bm{x},  \ \bm{y}$$는 다음과 같은 방정식을 만족한다. 
  * $$\Vert\bm{x}\Vert^{2}+\Vert\bm{y}\Vert^{2} =\Vert\bm{x}+\bm{y}\Vert^{2} $$\(피타고라스의 정리\)
* 다음 사실을 이용하여 위 식을 전개해보자 : 
  * $$\begin{aligned}\cancel{\bm{x}^\top\bm{x}}+\cancel{\bm{y}^\top\bm{y}}&=(\bm{x}+\bm{y})^\top(\bm{x}+\bm{y})\\ &=\bm{x}^\top\bm{x}+\bm{y}^\top\bm{y}+\bm{x}^\top\bm{y}+\bm{y}^\top\bm{x}  \\ &=\cancel{\bm{x}^\top\bm{x}}+\cancel{\bm{y}^\top\bm{y}}+2\bm{x}^\top\bm{y}\end{aligned}$$
* Thus, $$\bm{x}^\top\bm{y}=0$$ \(dot product가 zero\)
  * 수직인 두 벡터는 이 식을 만족한다! 
* 영벡터는 모든 벡터와의 dot product가 zero.
  * 그러므로, 모든 벡터에 대해서 orthogonal.
  * \(이때는 perpendicular라는 말은 어색하다.\) 

{% hint style="warning" %}
**위의 전개는 이하의 사실을 활용하면 된다.** 

\(직접 symbolic vector들로 계산해보면 쉽게 증명 가능\)

* $$\Vert\bm{x}\Vert^{2}=\bm{x}\cdot\bm{x}=\bm{x}^\top\bm{x}$$
  * 벡터 길이의 제곱 = 자기 자신과의 dot product
* $$\bm{x}\cdot\bm{y}=\bm{y}\cdot\bm{x} \ \ \Leftrightarrow \ \ \bm{x}^\top\bm{y}=\bm{y}^\top\bm{x} $$ 
  * dot product는 순서에 무관 
{% endhint %}

{% hint style="info" %}
**결론:** 

* 두 벡터의 dot product가 0이면 orthogonal하다. 
* 영벡터는 모든 벡터에 orthogonal하다. 
{% endhint %}

## Orthogonal Subspaces 

두 부분공간 $$S$$와 $$T$$가 orthogonal하다는 것은 다음을 의미한다. 

* $$S$$에 속하는 모든 벡터와  $$T$$에 속하는 모든 벡터가 서로 orthogonal이다. 
* 즉, 두 부분공간에서 각각 어떤 벡터를 하나씩 뽑아도 항상 직교해야한다. 

#### 다음 그림\[Fig. 2\]과 같은 상황에서는 $$S$$와 $$T$$가 orthogonal한가? 

![\[Fig. 2\] Not orthogonal.](../.gitbook/assets/image%20%2868%29.png)

\*\*\*\*

* **그렇지 않다.** 
* **Counter-example:** 두 subspace의 intersection인 빨간 직선.

  * 두 subspace가 $$\bm{0}$$이 아닌 intersection을 가지는 순간, orthogonal할 수 없다. 
  * 어떤 벡터도 자기 자신에 대해 orthogonal할 수 없기 때문이다. 

#### 다음 그림\[Fig. 3\]과 같은 상황에서는 $$S$$와 $$T$$가 orthogonal한가? 

![\[Fig. 3\] Orthogonal](../.gitbook/assets/image%20%28128%29.png)

* **그렇다.** 
* 4대 부분공간을 배울때 봤던 그림이다.

![\[Fig. 4\] &#xB2E4;&#xC2DC;&#xBCF4;&#xB294; 4&#xB300; &#xBD80;&#xBD84;&#xACF5;&#xAC04;&#xC758; &#xC608;&#xC2DC;](../.gitbook/assets/image%20%2874%29.png)

### Row space와 nullspace는 orthogonal하다.

* 이미 언급한 내용이지만, 이번 기회에 구체적으로 증명해보자. 

#### Nullspace는 다음과 같다. 

* $$A\bm{x}=\begin{bmatrix} row  \ 1 \ of \  A \\ row  \ 2 \ of \  A \\ \vdots  \\row  \ m \ of \  A\end{bmatrix}\begin{bmatrix} \\  \bm{x} \\ \\ \end{bmatrix}= \begin{bmatrix}0\\0\\\vdots\\0\end{bmatrix}$$
* $$\begin{cases} (row \ 1)\bm{x}=0 \\ (row \ 2)\bm{x}=0 \\ \qquad \ \ \ \vdots \\(row \ m)\bm{x}=0\end{cases}$$
* 즉, nullspace $$\bm{x}$$는$$A$$의 모든 row들에 대해서 orthogonal하다. 

#### 양변에 각각 실수배를 해서 모두 더하면:

* $$(c_1(row \ 1)+ c_2(row \ 2)+ \cdots + c_m(row \ m))\bm{x}=0$$ 
* 즉, nullspace $$\bm{x}$$는 \(row들의 모든 combination\)에 대해서도 orthogonal하다. 
  * \(row들의 모든 combination\) = **row space**! 

{% hint style="info" %}
**두 subspace들이 이루는 기하학적 관계**

* Nullspace와 row space는 $$\mathbb{R}^n$$안에서 서로의 **orthogonal complements**\(직교여공간\)이다. 
  * 이 표현은 나중에 projection을 배울때 활용되니 기억해두자. 
* Nullspace는 row space에 orthogonal한 **모든**\(all, not some\) 벡터들을 포함한다. 
* 위 내용들은 column space와 left nullspace의 관계에도 그대로 적용된다. 
{% endhint %}

