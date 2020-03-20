# Lecture 15. Projections onto Subspaces

## Introduction

### 만약 $$A\bm{x}=\bm{b}$$의 해가 해가 존재하지 않는다면?

* Real-world problem에서는 매우 자주 있는 일이다. 
* 선형방정식계에서 해가 존재하지 않는 케이스와 실제 예시를 살펴보자. 
* 그리고 이 문제를 어떻게 해결할 수 있을지 생각해보자. 
  * \(스포\) projection! 

#### 선형방정식계에 해가 없는 경우, 즉, $$\bm{b}$$가 column space 안에 없는 경우는?  

1. 선형종속인 column들이 충분히 존재하여 column space가 출력차원\($$m$$\)보다 작아져 버린 경우.
2. 모두 선형독립인 column들을 가지고 있지만\(full column rank\), 출력차원\($$m$$\)이 너무 큰 경우.  

{% hint style="danger" %}
앞으로 다룰 내용은 해가 존재하지 않으면서 full column rank인 경우\(2번\)에만 적용가능하다.
{% endhint %}

#### 실제 우리가 자주 만나게 될 상황은? 

* 대부분의 real-world problem에서는 예측할 변수에 비해 데이터의 수가 충분히 많다. \(2번에 해당\) 
* 즉, full column rank를 가지는 것은 쉽지만, 방정식의 개수\($$m$$\)가 더 많은 것이 문제이다. 
* 많은 데이터\(충분한 정보량\)를 고려함으로써 측정오차를 줄이고자 하기 때문이다. 
* 그러나, 예컨데, 3차원에서 100개의 평면이 한점에서 만나는 것은 거의 불가능하다. 
* 이때, **100개의 평면과 '평균적'으로 거리오차가 가장 작은\(가장 가까운\) 점**을 찾으면 어떨까?  

### 예를 들어보자. 

#### 센서데이터의 측정을 통해 어떤 실제 물리량을 예측한다고 가정해보자. 

* **방정식의 개수:** 테이터 획득 횟수 
* **변수의 개수:** 예측하고자 하는 물리량의 개수 
* $$A$$**:** 물리량과 데이터간의 선형관계 
* \*\*\*\*$$\bm{x}$$**:** 물리량 변수
* $$\bm{b}$$**:** 측정 결과 

#### 많은 real-world scenario에서는 변수의 개수에 비해 방정식의 개수가 많다. \($$m>n$$\)

* 인공위성의 위치예측을 위한 센서데이터\(방정식\)는 매우 많다.
* 그러나 위치를 특정하는 파라미터\(변수\)는 몇 개에 불과.
* 그렇다고 단순히 데이터 샘플링 수를 줄이는 것은 만족스럽지 않은 전략이다. 
  * 수많은 데이터셋에서 어떤 데이터 샘플이 좋은지 모르기 때문이다. 
  * 단순히 간단한 풀이를 위해서 정보를 버리는 것이 좋은 해결책이 아니다. 
* 최대의 정보량을 활용하면서도 가장 최적에 가까운 해를 구할 순 없을까? 

#### 또한 measurement\(측정\)의 결과인 $$\bm{b}$$에는 노이즈가 있다. 

* 똑같은 상황에서 다른 센서데이터가 관측될 수 있음. 
* 데이터에는 노이즈도 있지만 정보도 있다. 
  * 정보의 양화를 통해 노이즈의 영향을 최소화할 수 있을까? 

#### 이런 경우에는 모든 상황에 들어맞는 해가 존재할 확률은 거의 제로이다. 

* 그러므로 우리는 이런 상황에서 가능한 최선의 해\(**best possible solution**\)을 찾아야 하는 것이다. 
* 노이즈가 많은 측정 샘플들을 단순히 버리는 것은 만족스럽지 않은 전략이다. 

## 어떻게 Best possible solution을 찾을 수 있을까? 

![\[Fig. 1\]](../.gitbook/assets/image%20%2887%29.png)

### Projection을 이용해보자! 

#### $$\bm{b}$$ 대신에 가장 가까운 column space 안의 벡터 $$\bm{p}$$에 대해서 방정식을 푸는 것이다. 

* 벡터 $$\bm{b}$$와의 오차를 가장 최소화하는\(거리가 가까운\) $$\bm{p}$$는 **projection**이다! 
* $$A\bm{x}=\bm{b}$$의 해가 존재하지 않을때, 대신 $$A\hat{\bm{x}}=\bm{p}$$의 해를 구하는 것이다. 

#### Projection을 구하게 되면 다음의 꼴을 만들 수 있다. 

* 실제 방법은 조금 뒤에 알아보자. 
* 일단 아래의 꼴만 기억해두자. \(눈에만 익혀두고 넘어가자\) 
  * $$A^\top A\hat{\bm{x}}=A^\top \bm{b}$$ 

#### 이 상황을 타개해줄 착한 행렬: $$A^\top A$$

* Square, symmetric 
* Lec 5.에서 잠깐 다뤘었다. 
* **Normal matrix**라고 부른다! 

{% page-ref page="lecture-5.-transposes-permutations-space-r-n.md" %}

#### $$A^\top A$$가 invertible이라면?

* 다음과 같이 best possible solution을 구할 수 있을 것이다. 
  * $$\hat{\bm{x}}=(A^\top A)^{-1}A^\top \bm{b}$$ 

{% hint style="danger" %}
#### $$A^\top A$$가 역행렬이 존재할 조건

* $$A^\top A$$는 $$A$$의 row\($$\in \mathbb{R}^n$$\)들의 선형재조합으로 이루어진 행렬 
  * $$A$$가 원래 가지고 있던 rank를 그대로 갖되, 사이즈는 $$n\times n$$으로 만든 것. 
  * 즉, 열의 개수는 맞추면서 불필요한 행은 제거한 것이다. 
* $$A^\top A$$는 다음을 만족한다. 
  * $$\text{Rank}(A^\top A)=\text{Rank}(A)$$
  * $$\mathcal{N}(A^\top A)=\mathcal{N}(A)$$
* $$A^\top A $$ **의 역행렬은 다음 상황에서 존재** 
  * $$A$$의 모든 column들이 선형독립일때\(full column rank\)
  * \(= nullspace가 영벡터만을 포함할때\)
* 정식 증명은 Lec 16.을 참조. 
{% endhint %}

### 한줄\(+@\) 요약?  

#### $$A\bm{x}=\bm{b}$$의 해를 구할 수 없을때는$$A^\top A\hat{\bm{x}}=A^\top \bm{b}$$의 꼴로 만들어라. 

* 이 식은 기하학적으로 projection과 관련이 있다! 
* 해가 없다 = $$R$$의 zero-row의 우변이 0이 아니다. 
* 단,$$A$$는 full column rank이어야 한다.  \($$A^\top A$$의 역행렬을 구하기 위해\) 
* 한마디로 RREF가 이런 모양: $$R=\begin{bmatrix} I \\ \bm{0} \end{bmatrix}$$

## 1차원의 subspace에 대한 projection

### 먼저 벡터$$ \bm{a}$$가 span하는 1차원 직선에 벡터 $$ {\bm{b}}$$를 projection 해보자. 

![\[Fig. 2\]](../.gitbook/assets/image%20%2813%29.png)

* Projection된 포인트 $$ {\bm{p}}$$는 $$\bm{a}$$의 실수배\($$x$$\)로 표현할 수 있다. 
* 벡터 $$ {\bm{b}}$$ 와 projection $${\bm{p}}$$ 사이의 차이\(error\)를 $$\bm{e}$$라고 하자. 

### Projection의 직교성\(orthogonality\)을 이용하여 $$x$$를 구해보자. 

*  $$\bm{a}\cdot\bm{e}=\bm{a}^\top (\bm{b}-x\bm{a})=0$$
* $$x\bm{a}^\top \bm{a}=\bm{a}^\top \bm{b}$$ \(dot product는 그냥 숫자\) 

#### **Answer:** $$x=\dfrac{\bm{a}^\top \bm{b}}{\bm{a}^\top \bm{a}}$$ \(역시 그냥 숫자\) 

### $$\bm{p}$$를 구하는 과정을 projection matrix $$P$$로 나타내보자. 

#### $$\bm{p}=x\bm{a}=\bm{a}x=\bm{a}\dfrac{\bm{a}^\top \bm{b}}{\bm{a}^\top \bm{a}}$$

* $$\bm{b}$$를 실수배하면 $$\bm{p}$$도 실수배만큼 길어진다. 
* $$\bm{a}$$를 실수배해도 $$\bm{p}$$는 그대로 유지된다. 
* \[Fig. 1\]에서 관찰되는 바와 일치한다. 

#### $$\bm{p}=\red{\bm{a}}\dfrac{\red{\bm{a}^\top} \bm{b}}{\red{\bm{a}^\top \bm{a}}} \ \Rightarrow \ \bm{p}=\red{P}\bm{b}$$

#### **Projection matrix:**$$P=\dfrac{\bm{a} \bm{a}^\top}{\bm{a}^\top \bm{a}}$$ 

* 분자: rank 1 matrix / 분모: number
* $$\text{rank}(P)=1$$ 
  * rank 1 matrix를 실수로 나눠줘도 여전히 rank 1 matrix.
* $$\mathcal{C}(P)=\text{line through } \bm{a}$$,
  * Rank 1 행렬 $$\bm{a}\bm{a}^\top$$의 basis는 $$\bm{a}$$이다. 

### $$P$$의 성질을 알아보자. 

#### Symmetric matrix\(대칭행렬\): $$P=P^\top$$

*  $$P^\top=\left(\dfrac{\bm{a}\bm{a}^\top}{\bm{a}^\top\bm{a}}\right)^\top= \dfrac{\bm{a}\bm{a}^\top}{\bm{a}^\top\bm{a}}=P$$

#### 이미 projection을 한 상태에서 한번 더해도 같은 효과: $$P^{2}=P$$

{% hint style="info" %}
**Projection matrix** $$P$$

* $$P^\top=P, \ P^{2}=P$$
{% endhint %}

## 2차원 이상의 subspace에 대한 projection 

* 2차원 subspace에의 projection을 예시로 살펴보자. 
* 2차원부터는 행렬로 나타낼 수 있게되며, 이를 기반으로 **N차원으로 일반화 가능**하다. 

### 행렬 $$A$$의 column space 위로 벡터 $$\bm{b}$$를 projection해보자. 

![\[Fig. 2\]](../.gitbook/assets/image%20%2853%29.png)

* $$A$$가 다음과 같이 2개의 선형독립인 column을 갖는다고 해보자: $$A=\begin{bmatrix} |&|\\a_1 & a_2 \\ | & | \end{bmatrix}$$
* Projection $$\bm{p}$$는 $$A$$의 column space 안에 존재하므로 어떤 combination $$\hat{\bm{x}}$$으로 표현할 수 있다. 
  * $$\bm{p}=\hat{x}_1\bm{a_1}+\hat{x}_2\bm{a_2}=A\hat{\bm{x}}$$
* 벡터 $$ {\bm{b}}$$ 와 projection $${\bm{p}}$$ 사이의 차이\(error\)를 $$\bm{e}$$라고 하자. 

### **Projection의 직교성\(orthogonality\)을 이용하여** $$\hat{\bm{x}}$$**을 구해보자.** 

* $$\bm{e}$$$$A$$의 basis인 두 벡터 $$a_1, \ a_2$$에 대해 동시에 수직이다.  
  * $$\begin{cases}\bm{a_1}\cdot\bm{e}=\bm{a_1}^\top (\bm{b}-A\hat{\bm{x}})=0 \\ \bm{a_2}\cdot\bm{e}=\bm{a_2}^\top (\bm{b}-A\hat{\bm{x}})=0\end{cases}$$
* 이를 행렬로 쓰면 다음과 같다. 
  * $$\begin{bmatrix} \text{--- }\bm{a}_1^\top\text{--- }\\\text{--- }\bm{a}_2^\top\text{--- }\end{bmatrix}  \bigg( \bm{b}-A\hat{\bm{x}} \bigg)=A^\top(\bm{b}-A\hat{\bm{x}})=\bm{0}$$
* 분배법칙으로 풀면 다음과 같다.
  * $$A^\top A\hat{\bm{x}}=A^\top\bm{b}$$
* $$A$$는 full column rank 행렬이므로 $$A^\top A$$는 역행렬이 존재한다. 

#### **Answer:** $$\hat{\bm{x}}=(A^\top A)^{-1}A^\top\bm{b}$$\*\*\*\*

{% hint style="warning" %}
* $$A^\top\underbrace{(\bm{b}-A\hat{\bm{x}})}_{\bm{e}}=\bm{0}$$에서 $$\bm{e}$$는 $$A$$의 left nullspace 안에 있음을 알 수 있다. 
* 우리는 이미 left nulspace는 column space에 orthogonal하다는 것을 배웠다. 
* **우리의 가정과 일치한다:**$$\bm{e} \perp \mathcal{C}(A)$$
{% endhint %}

{% hint style="info" %}
$$A\bm{x}=\bm{b}$$이 주어졌을 때,  $$A^\top A\hat{\bm{x}}=A^\top\bm{b}$$를 **normal equation**\(정규방정식\)이라고 부른다.  

* 다음 두 공간이 서로 수직\(normal\)이기 때문이다: $$\mathcal{C}(A) \perp(\bm{b}-A\hat{\bm{x}})$$ 
* 이를 만족하려면 $$A\hat{\bm{x}}$$는 $$\bm{b}$$의 projection이어야 하며, $$(\bm{b}-A\hat{\bm{x}})$$길이가 최소여야 한다.
* 여기서, $$A^\top A$$는 [normal matrix](https://en.wikipedia.org/wiki/Normal_matrix)\(정규행렬\)이다. 
{% endhint %}

### $$\bm{p}$$**를 구하는 과정을 projection matrix** $$P$$**로 나타내보자.** 

* $$\bm{p}=A\hat{\bm{x}}=\red{A(A^\top A)^{-1}A^\top}\bm{b}=\red{P}\bm{b}$$

#### **Projection matrix:**$$P=A(A^\top A)^{-1}A^\top$$

{% hint style="warning" %}
**여기서** $$A$$**가 invertible square matrix였다면?** 

* $$A$$의 row space 역시 full rank이며, $$A^\top$$ 역시 invertible이다. 
* 그러므로 **개별적으로 inverse**를 취해줄 수 있다. **\(rectangular matrix의 경우는 불가능\)** 
  * $$P=A(A^\top A)^\red{-1}A^\top=AA^\red{-1}(A^\top)^\red{-1}A^\top=I$$ 
  * 항등행렬로의 선형변환, 즉, 아무 것도 하지 않은 것과 같음.
* 즉, 전체 공간을 span하는 column space에서의 projection은 입력벡터 자신이다. 
{% endhint %}

### 1차원에서 알아봤던$$P$$의 성질을 여전히 만족하는지 알아보자. 

#### Symmetric matrix\(대칭행렬\): $$P=P^\top$$

* Symmetric matrix\($$S=S^\top$$\)의 역행렬도 역시 symmetric이다. 
  * $$(S^{-1})^\top=(S^\top)^{-1}=S^{-1}$$
* $$A^\top A$$는 symmetric\(Lec. 5 참조\)이므로 $$(A^\top A)^{-1}$$ 도 symmetric이다. 
  *  $$P^\top=(A\underbrace{(A^\top A)^{-1}}_{symmetric}A^\top)^\top=A\underbrace{(A^\top A)^{-1}}_{((A^\top A)^{-1})^\top}A^\top=P$$**\(확인\)** 

#### 이미 projection을 한 상태에서 한번 더해도 같은 효과: $$P^{2}=P$$

* $$P^2=A(A^\top A)^{-1}A^\top=A(A^\top A)^{-1}\cancel{A^\top A(A^\top A)^{-1}}A^\top=P$$ **\(확인\)**

