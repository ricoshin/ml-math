# Lecture 11. Matrix Spaces; Rank 1; Small World Graphs

## Introduction

* 이번 장은 여러 특이한 형태의 부분공간에 대한 보충수업 정도로 생각해두자. 
* Rank 1 matrix는 나중에도 등장하니 잘 기억해두자. 

## Matrix Spaces

### 행렬들로 이루어진 새로운 벡터공간에 대해 알아보자. 

#### 모든 3x3 행렬은 벡터공간이 될 수 있을까? 

* 벡터공간의 axiom을 확인하면 된다. 
  * 아주 간단히 말해서 벡터합과 실수배 연산, 즉 선형조합에 대해 닫혀있으면 된다! 
* $$A+B$$와  $$cA$$를 하거나, 행렬의 선형조합을 수행해도 여전히 3x3 행렬이다.
* $$AB$$의 결과도 여전히 3x3행렬이지만, 벡터공간의 공식 연산이 아니므로 관심이 없다. 
* **결론:** 벡터공간이 될 수 있다. 
* **모든 3x3행렬을 벡터공간** $$M$$**이라고 하자.** 

#### 다음은 $$M$$의 부분공간이다. \(선형조합에 대해 닫혀있다.\) 

* 모든 3x3 상삼각행렬\(All upper triangular matrices\) $$U$$
* 모든 3x3 대칭행렬\(All symmetric matrices \) $$S$$
* 모든 3x3 대각행렬\(All diagonal matrices\) $$D$$

### 벡터공간$$M$$\(모든 3x3 행렬\)에 대해 알아보자.  

* **기저:** $$\left\{ \begin{bmatrix} \red1&0&0\\0&0&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&\red1&0\\0&0&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&0&\red1\\0&0&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&0&0\\\red1&0&0\\0&0&0\end{bmatrix}, \ \cdots , \ \begin{bmatrix} 0&0&0\\0&0&0\\0&0&\red1\end{bmatrix} \right\}$$
* **차원:**  $$\dim(M)=9$$
* 사실상 9차원의 벡터를 정방행렬의 bracket에 집어넣은 것과 같다. 

### 부분공간$$S$$\(모든 3x3 대칭행렬\)에 대해 알아보자. 

* **기저:** $$\left\{ \begin{bmatrix} \red1&0&0\\0&0&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&0&0\\0&\red1&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&0&0\\0&0&0\\0&0&\red1\end{bmatrix}, \begin{bmatrix} 0&\red1&0\\\red1&0&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&0&\red1\\0&0&0\\\red1&0&0\end{bmatrix} ,\begin{bmatrix} 0&0&0\\0&0&\red1\\0&\red1&0\end{bmatrix}\right\}$$ 
  * 이들 중 처음 3개만$$M$$의 기저에는 단 3개만 포함된다. 
  * 포함관계의 더 큰 벡터공간의 basis가 subspace의 basis를 항상 포함하는 것은 아니다.  
* **차원:** $$\dim(M)=6$$

### 부분공간 $$U$$\(모든 3x3 대칭행렬\)에 대해 알아보자.  

* **기저:** $$\left\{ \begin{bmatrix} \red1&0&0\\0&0&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&\red1&0\\0&0&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&0&\red1\\0&0&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&0&0\\0&\red1&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&0&0\\0&0&\red1\\0&0&0\end{bmatrix} ,\begin{bmatrix} 0&0&0\\0&0&0\\0&0&\red1\end{bmatrix}\right\}$$ 
  * \(운좋게도, 항상 그런 것은 아니지만, accidentally\) 이들 모두$$M$$의 기저에 포함된다.  
* **차원:** $$\dim(M)=6$$

### $$S\cap U$$ \(Intersection\)도 부분공간이다.

* 대칭이면서 동시에 상삼각인 행렬은 **대각행렬**이다.
  * 즉,$$S\cap U=D$$\(모든 3x3 대각행렬\)이다. 
* 그리고, 모든 3x3 대각행렬은 모든 3x3 행렬의 **부분공간**이다. 
* **기저:** $$\left\{ \begin{bmatrix} \red1&0&0\\0&0&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&0&0\\0&\red1&0\\0&0&0\end{bmatrix}, \begin{bmatrix} 0&0&0\\0&0&0\\0&0&\red1\end{bmatrix} \right\}$$ 
* **차원:** $$\dim(S\cap U)=\dim(D)=3 $$

### $$S \cup U$$\(Union\)은 부분공간이 아니다. 

* Lecture 6.에서 배웠듯이, subspace끼리의 union으로는 subspace를 만들 수 없다.  
* 예를 들어, 두 직선의 단순한 합집합으로는 한차원 더 큰 subspace인 평면을 만들 수 없다. 

### $$S+U$$\(Sum\)는 부분공간이다.   

#### 부분공간끼리의 더하기\(plus\)연산은 무엇을 의미하는가? 

* Lecture 6.에서 다뤘던 내용이다. 
* 단순한 두 집합의 합집합과 달리, 두 부분공간의 모든 원소들의 합을 의미한다. 
* 두 집합의 원소들끼리 더해져서 만들어낼 수 있는 모든  가능성이 또 다른 부분공간을 형성하는 것이다. 
* 다음은 subspace간 '$$+$$'연산에 대한 새로운 약속처럼 보인다.  
  * $$S+U:=\{s+u \; | \; s \in S, \; u\in U \}$$
* 그러나, 우리가 기존에 알고있던 벡터합을 통해 자연스럽게 확장가능하다.  
  * $$S=c_1\bm{s_1}+c_2\bm{s_2}$$
  * $$U=c_3\bm{u_1}+c_4\bm{u_2}$$ 
  * $$S+U=c_1\bm{s_1}+c_2\bm{s_2}+c_3\bm{u_1}+c_4\bm{u_2}$$ 
* $$S+T$$는 자연스럽게 4개의 basis\($$\{ \bm{s}_1,\bm{s}_2,\bm{u}_1,\bm{u}_2\}$$\)에 의해 span되는 새로운 선형조합이 된다. 

#### $$S+U$$은 실제로 어떤 공간일까?  

* 대칭인 행렬과 상삼각인 행렬을 더하면 모든 행렬을 만들 수 있다. \($$S+U=M$$\)
  * $$S+U$$= any element of $$S$$ + any element of $$U$$= all 3x3 matrices $$M$$
* **기저:** $$M$$의 기저와 같다. 
* **차원:** $$\dim(S\cup U)=\dim(M)=9$$ 

### 차원들을 정리해보자. 

* $$\dim(S)=6$$
* $$\dim(U)=6$$
* $$\dim(S\cap U)=3$$
* $$\dim(S+U)=9$$

#### 다음 규칙을 발견할 수 있다. 

* $$\dim(S)+\dim(U)=\dim(S+U)+\dim(S\cap U)$$

#### 조금 더 생각해보자. 

* $$\dim(S+U)\leq\dim(S)+\dim(U)$$
* 부분공간의 선형조합의 차원은 각각의 차원을 더한 것보다 더 작을 수 있다. 
* 각, 부분공간이 서로 중복되는 차원\($$\dim(S\cap U)$$\)이 존재할 수 있기 때문이다.  

## 또 다른 벡터공간의 예 

#### 다음 선형 미분방정식을 살펴보자: $$y''+y=0$$

* 여기서는 다루지 않겠지만, 미분도 선형변환으로 볼 수 있다.
* 이 방정식을 푸는 것은 nullspace를 구하는 것과 같다. 

#### 이를 만족하는 특정한 해\(special solution\)는 다음이 있을 것이다. 

* $$y=\cos{x}, \  \sin{x}, \ e^{ix}, \ e^{-ix}$$
* 미분방정식 시간이 아니므로 대입했을때 식이 성립한다는 정도만 확인하자.  

#### 방정식 전체를 만족하는 모든 완전한 해\(complete solution\)은 다음과 같다. 

* **Complete solution:** $$y=c_1\cos{x}+c_2\sin{x}$$
* **Basis:** $$\cos{x}$$, $$\sin{x}$$
* **Dimension:** 2 

#### $$e^{ix}=\cos{x}+i\sin{x}$$\(오일러공식\)이므로 위의 솔루션과 선형종속! 

* **다음 basis로도 표현 가능:** $$e^{ix}, \ e^{-ix}$$ 

#### 정확히 이해가 되지 않아도 괜찮을 듯.

* 선형대수의 개념들이 단순 행렬을 넘어서서 **더 넓은 범위로 확장될 수 있다**는 것이 메세지! 
* $$\sin{x}$$와 $$\cos{x}$$도 서로 더하고 실수배를 해도 여전히 the same kind가 나온다. **\[Fig. 1\]**  
  * **이들도 벡터라는 것!**  

![\[Fig. 1\]](../../.gitbook/assets/image%20%2837%29.png)

## Rank 1 Matrices 

$$A=\begin{bmatrix} 1&4&5 \\ 2&8&10 \end{bmatrix}=\begin{bmatrix} 1 \\ 2\end{bmatrix} \begin{bmatrix} 1 & 4 & 5 \end{bmatrix}$$

* $$dim(\mathcal{C}(A))=rank =dim(\mathcal{C}(A^\top))$$
* 즉, **모든 rank 1 행렬은** $$A=\bm{u}\bm{v}^\top$$**의 꼴로 나타낼 수 있다!** 
* 반대로 **행벡터와 열벡터의 곱\(** $$\bm{u}\bm{v}^\top$$ **\) 의 결과는 반드시 rank 1 행렬이다!** 
* Rank 1 행렬의 determinant나 eigenvalue등은 특별한 속성을 갖는다. 

### Rank 1 행렬은 모든 행렬의 building block이다. 

> "You can produce **every rank 4 matrices** out of **4 rank one matrices**."

* 행렬을 구성하는 가장 최소 정보량의 단위가 된다는 뜻이다. 
* 만약 $$(m\times n)$$행렬이 있고, **rank가** $$r$$이라고 가정해보자. 
  * 이는 크기가 $$(m\times n)$$인 $$r$$**개의 rank 1 행렬**로 break down할 수 있다!   

#### 비유:$$r$$장의 크레페로 이루어진 레인보우 크레페케이크\(rank $$r$$ 행렬\)를 생각해보자. 

* **낱장의 크레페**\(each rank 1 matrices\)는 케이크의 최소구성 단위로써 모두 다른 색깔과 맛을 가진다.
* 우리는 케이크를 먹어보기 전엔 맛이 얼마나 다양하고 깊은지 알 수 없다.  
* 이 케이크가 무슨 맛인지 분해해보고 싶다면, 크레페 layer들을 한장 한장 떼어 늘어놓으면 된다.  

![&#xCD9C;&#xCC98;: https://blog.naver.com/bestacook3/220400887268](../../.gitbook/assets/image%20%2841%29.png)

### Rank $$r$$ 행렬은 \(같은 사이즈의\) 모든 행렬공간의 subspace일까? 

* **그렇지 않다.** rank $$r$$행렬끼리의 덧셈은 항상 rank $$r$$을 만들지 못한다. 
* 반례를 단 하나만 찾아도 위 사실은 확인할 수 있다. 
  * $$\begin{bmatrix} 1&4&5\\2&8&10\\3&7&6\end{bmatrix}+\begin{bmatrix} 3&6&9\\2&4&8\\1&2&8\end{bmatrix}=\begin{bmatrix} 4&10&14\\4&12&18\\4&9&14\end{bmatrix}$$
  * Rank 2 + Rank 2 = Rank 3임을 확인하자. 
  * 출처: [Learn Again! 블로그](https://twlab.tistory.com/27?category=668741)
* 행렬의 합에 대한 rank는 오히려 upper bound를 가진다. \(아래 참조\) 

{% hint style="warning" %}
#### 다음을 증명해보자: $$\text{rank}(A+B)  \leq \text{rank}(A) + \text{rank}(B)$$ 

$$\begin{aligned} &\text{rank}(A+B) \\   &\stackrel{\red{\tiny(1)}}{=}  \dim(\text{span}(\bm{a}_1+\bm{b}_1  , \ \cdots , \ \bm{a}_n+\bm{b}_n))  \qquad  \\   &\stackrel{\red{\tiny(2)}}{\leq}  \dim(\text{span}(\bm{a}_1 , \ \cdots , \ \bm{a}_n)+\text{span}(\bm{b}_1  , \ \cdots , \ \bm{b}_n)) \\   &\stackrel{\red{\tiny(3)}}{\leq}  \dim(\text{span}(\bm{a}_1 , \ \cdots , \ \bm{a}_n))+\dim(\text{span}(\bm{b}_1  , \ \cdots , \ \bm{b}_n)) \\    &\stackrel{\red{\tiny(4)}}{=} \text{rank}(A) + \text{rank}(B) \end{aligned}$$

\(1\): A+B의 rank는 각각의 column들을 더한 것들이 span하는 부분공간의 차원이다. 

\(2\): 이 부분공간의 차원은 A와 B의 column space를 선형조합한 공간의 차원보다 작거나 같다.

* A와 B의 rank가 모두 1이면, 두 행공간에 대응하는 직선\(1d\)들의 선형조합은 평면\(2d\)이다. 
* 만약 매우 드물게 두 직선이 서로 선형종속이면, 선형조합도 \(1d\)일 것이다. 

\(3\): 위에서 얻었던 지식을 활용하자.

* $$\dim(S+U)\leq\dim(S)+\dim(U)$$ 

\(4\): 결국 결론은 다음과 같다. 

* $$\text{rank}(A+B)  \leq \text{rank}(A) + \text{rank}(B) $$ 
{% endhint %}

### Rank $$1$$ 행렬은 \(같은 사이즈의\) 모든 행렬공간의 subspace일까? 

* Rank 1 행렬끼리 더한 결과는 항상 rank 1일까? 
* **그렇지 않다.** 위에서 배운 내용에 따르면, rank 1 행렬 2개를 더하면 rank 2 행렬이 된다.  
  * 단, 두 행렬이 서로 선형종속인 경우 제외. 

## 부분공간의 또 다른 예시 

### 다음 4차원 벡터가 있다고 해보자: $$\bm{v}=\begin{bmatrix} v_1 \\ v_2 \\ v_3 \\ v_4 \end{bmatrix}$$

#### $$v_1+v_2+v_3+v_4=0$$를 만족하는 $$\bm{v}$$의 집합 $$S$$는 부분공간일까? 

* **그렇다.** $$S$$는 다음 행렬 $$A$$**의 nullspace**이기 때문이다!
  * $$A\bm{v}=\begin{bmatrix} 1&1&1&1 \end{bmatrix}\begin{bmatrix} v_1 \\ v_2 \\ v_3 \\ v_4 \end{bmatrix}= \bm{0}$$
* nullspace이 존재하는 벡터끼리 서로 더하거나 실수배를 해도 여전히 nullspace 안에 존재한다. 
* 강의에서는 행렬 $$A$$의 4대 subspace도 구하지만, 중복이고 충분히 쉬우므로 생략하겠다. 
* rank 1 행렬이라 조금 어색할 수 있지만, 이미 소거가 끝난 상태라고 생각하고 기존의 룰을 적용하자. 
* 자세한 설명은 다음 블로그를 참조 
  * [Learn Again! 블로그](https://twlab.tistory.com/27?category=668741) 



