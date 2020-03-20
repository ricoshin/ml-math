# Lecture 12. Graphs, Networks, Incidence Matrices

## Introduction

* 이번 lecture에서는 선형대수가 실제로 어떻게 활용되는지 그 application에 대한 예시를 살펴보자. 
* 지금껏 다루기 쉬운 임의로 만든 작은 행렬들을 예로 들었지만, 실전은 다를 것이라는 것은 명백하다. 
* 행렬의 형태는 문제상황에서 이미 주어질 것이고, 우리는 그 행렬을 사용하는 것이 실제 상황이다. 
* 우리가 지금까지 배운 여러 행렬 속성이 실제 application에서 무슨 의미를 가지게 될지 감을 잡아보자! 

### 전기회로를 행렬로 표시하고, 이를 분석함으로써 행렬을 이해해보자. 

#### \(1\) 일단, 전기회로\(electrical network\)를 graph라고 불리는 구조로 나타낸다. 

* 전기회로는 하나의 예시일 뿐이다. 
  * 전류\(current\), 전위차\(potential difference\) 등이 행렬의 입출력이 된다. 
* 유압 네트워크일 수도 있고, 건축물의 [트러스](https://en.wikipedia.org/wiki/Truss) 구조일 수도 있다. 

#### \(2\) Graph는 대응되는 Incidence Matrix로 나타낼 수 있다. 

#### \(3\) 행렬에 대한 우리의 지식을 활용하여 회로를 이해해보자. 

* 키르히호프의 법칙\(Kirchhoff's Law\) 등을 유도. 

## Graph & Incidence Matrix

* 우리가 흔히 생각하는 2차함수의 그래프 등은 여기서 잊자. 
* 앞으로 이산수학이나 머신러닝 등에서 만나는 '그래프'는 대부분 여기서 이야기하는 개념이다. 
* Strang 교수님의 15년전 멘트에 의하면, 그래프는 응용수학의 가장 중요한 모델이라고 말씀하신다. 

### 그래프는 node와 edge로 이루어져 있다. 

![\[Fig. 1\]](../.gitbook/assets/image%20%28159%29.png)

* 위 그래프\[Fig. 1\]에서 파란점들이 **node**\(노드\) 혹은 **vertex**\(정점\)이다.
* 각 node들을 연결하는 선이 **edge**\(간선\)이다. 
* 이렇게 노드간의 연결상태를 시각적으로 나타낸 것을 graph라고 부르는 것이다. 
  * 다른 수많은 종류의 네트워크를 이러한 방식으로 표현할 수 있다. 
* 위 그림에서는 edge가 방향성을 나타내는데, 이를 **directed graph**\(유향그래프\)라고 한다. 

#### 이 그래프와 정확히 동일한 정보를 포함하는 행렬을 만들면?

* 지금까지 배운 모둔 선형대수의 프레임을 동원하여 이 그래프를 분석할 수 있을 것이다. 

### 이 그래프와 동치인 Incidence matrix $$A$$ 를 만들어보자. 

* Edge들이 어떤 두 개의 node를 어떤 방향으로 연결하고 있는지를 행렬에 나타내보자. 
* 각 행은 5개의 edge를 설명하고, 각 열은 4개의 node를 의미하도록 해보자. 
* Edge를 전류의 흐름이라고 보고, 전류의 방출을 -1, 유입을 +1로 기술해보자. 
  * $$A=\begin{bmatrix} -1&1&0&0 \\ 0&-1&1&0 \\ -1&0 &1&0 \\-1&0&0&1 \\ 0&0&-1&1 \\\end{bmatrix}$$
* 이 행렬을 **Incidence matrix**\(근접행렬 or 발생행렬\)라고 한다. 
  * '근접행렬'이라는 번역은 인접행렬\(adjacency matrix\)과 혼동될 뿐더러 직관적이지 않은 것 같다.  
  * 여기서 incidence의 뜻은 _'node간 관계\(사건\)의 발생'_의 의미에 가깝다고 생각한다. 
  * 학계에서 사용되는 잘못된 한글 번역은 오히려 이해를 힘들게 한다. 그냥 영어로 쓰자.
* cf. _Adjacency matrix_\(인접행렬\)이라는 것도 있다. 
  * Incidence matrix: edge vs. node 사이의 관계
  * Adjacency matrix: node vs. node 사이의 관계 

#### 그래프가 매우 커지면 어떻게 될까? 

* 그래프가 클수록 행렬도 커질 것이다. 
* Edge는 두 개의 노드 외에는 연결하지 못하므로 0을 많이 포함할 것이다. 
  * 이렇게 non-zero element가 희소한 행렬을 **sparse matrix\(희소행렬\)**라고 한다.
  * \(참고\) real-world의 행렬들은 sparse한 경우가 많으며, 머신러닝에서도 중요한 이슈이다. 
* Real-world problem에서의 행렬은 이러한 문제의 특성을 반영하는 **특정한 '구조'**를 가지게 된다. 
  * 때로는 이러한 구조에서 문제의 특성을 더 쉽게 파악할 수 있다. 

## 이제 Incidence matrix$$A$$ 를 분석해보자.  

* 시작하기 전에 node와 edge에 각각 symbol $$\bm{x}\in\mathbb{R}^4, \ \bm{y}\in\mathbb{R}^5$$를 부여해주자. \[Fig. 2\] 

![\[Fig. 2\]](../.gitbook/assets/image%20%2860%29.png)

###  $$A\bm{x}$$ 는 어떤 물리적 의미를 가질까? 

* $$\bm{x}$$는 node와 관련된 수량.
  * 서로 연결된 node들의 관계에서 얻을 수 있는 것은 전위차이다. 
* $$A\bm{x}=\begin{bmatrix} -1&1&0&0 \\ 0&-1&1&0 \\ -1&0 &1&0 \\-1&0&0&1 \\ 0&0&-1&1 \\\end{bmatrix}\underbrace{\begin{bmatrix}x_1\\x_2\\x_3\\x_4 \end{bmatrix}}_{\text{input}} =\underbrace{\begin{bmatrix}x_2-x_1\\x_3-x_2\\x_3-x_1\\x_4-x_1\\x_4-x_3 \end{bmatrix}}_{\text{output}} $$
* **입력:** 각 node에서의 전위\(potential\)
* **출력:** 각 edge\(node와 node 사이\)에 걸리는 전위차/전압\(potential difference/voltage\)
  * 단, 화살표 head 방향 node에서 tail 방향 node를 뺀 것을 기준으로 한다. 
* 즉, $$A$$는 **각 node의 전위를 입력**하면 **각 edge에 걸리는 전압\(node간 전위차\)을 출력**하는 행렬이다. 

{% hint style="warning" %}
**전기회로에 대한 약간의 배경지식** 

* **전기회로\(electrical circuit\):** 다른 높이의 수조\(node\)들을 파이프\(edge\)로 연결한 구조물
* 각 node의 **전위\(potential\):** 물의 높이\(위치 에너지\) 
  * 간혹 전위를 전압으로 잘못 이야기하는 경우가 있다. 
* 특정 node의 **접지\(Grounding\):** 특정 수조의 높이를 0으로 기준하여 다른 수조의 높이 표현  
* 각 node 사이의 **전위차/전압\(potential difference/voltage\):** 물의 높이차/수압 
* 각 node 사이에 흐르는 **전류\(current\):** 높은 수조에서 낮은 수조로의 물의 흐름
{% endhint %}

### $$A$$ 의 nullspace는 어떤 의미를 가질까?

* $$A\bm{x}=\begin{bmatrix} -1&1&0&0 \\ 0&-1&1&0 \\ -1&0 &1&0 \\-1&0&0&1 \\ 0&0&-1&1 \\\end{bmatrix}\underbrace{\begin{bmatrix}x_1\\x_2\\x_3\\x_4 \end{bmatrix}}_{\text{input}} =\underbrace{\begin{bmatrix}x_2-x_1\\x_3-x_2\\x_3-x_1\\x_4-x_1\\x_4-x_3 \end{bmatrix}}_{\text{output}} = \begin{bmatrix} 0\\0\\0\\0\\0\end{bmatrix}=\bm{0}$$ 
* 모든 edge의 전위차를 zero가 되게하는\(전류가 흐르지 않는\) 각 node의 전위를 구하는 것이다! 
* 당연히 모든 node의 전위가 0이면 전위차도 0이다. \(nullspace에는 영벡터가 항상 존재한다.\)
* $$\bm{0}$$이 아닌 nullspace의 원소, 즉 special solution은 눈으로도 쉽게 찾을 수 있다.
  * $$\bm{x}=\begin{bmatrix} 1 \\ 1 \\ 1\\ 1\end{bmatrix}$$ : 모든 row에 -1과 1이 하나씩 존재하므로 모든 행을 다 더하면 $$\bm{0}$$이 된다. 
* 잘보면 1, 2, 3번째 행들은 유일한 위치에 0을 가지고 있으므로 선형독립이다.  
  * Rank는 3이고, nullspace의 차원은 1이다. 
  * 즉, 전체 nullspace는 다음과 같다: $$\bm{x}=c\begin{bmatrix} 1 \\ 1 \\ 1\\ 1\end{bmatrix} (\text{any } c \in \mathbb{R})$$ 

#### 이것의 물리적 의미는?

* 각 node의 전위를 모두 같게하면 그 크기\($$c$$\)에 관계없이 전위차는 0이 된다. 
  * 전기회로의 당연한 상식이 수학적으로 드러났다. 

#### 접지\(Grounding\)를 해보자!  

![](../.gitbook/assets/image%20%2829%29.png)

* 접지는 특정 node의 전위를 0으로 기준삼는 것이다. 
* 예를 들어, node 4를 접지하면\[Fig. 3\], $$x_4=0$$로 고정하는 것과 같다. 
  * 다른 node를 접지해도 관계없다. 기준이 필요할 뿐이다. 
* 그러면 미지수가 3개로 줄어들게 되고, incidence matrix의 행도 3개로 줄어든다. 
* 전체 행개수는 3개로 줄었지만 여전히 rank는 3이므로 nullspace의 차원도 0으로 감소하게 된다. 
* 즉, 기준 전위를 고정함으로써 나머지 node들의 전위를 계산할 수 있게 된다. 

### $$A^\top\bm{y}$$는 어떤 물리적 의미를 가질까? 

* $$\bm{y}$$는 edge와 관련된 수량. 
  * 하나의 node에 연결된 edge들의 관계에서 얻을 수 있는 것은 전류의 총량이다. 
* $$A^\top\bm{y}=\begin{bmatrix} -1&0&-1&-1&0\\1&-1&0&0&0\\0&1&1&0&-1\\0&0&0&1&1 \\\end{bmatrix}\underbrace{\begin{bmatrix}y_1\\y_2\\y_3\\y_4\\y_5 \end{bmatrix}}_{\text{input}} =\underbrace{\begin{bmatrix}-y_1-y_3-y_4\\y_1-y_2\\y_2+y_3-y_5\\y_4+y_5 \end{bmatrix}}_{\text{output}} $$
* **입력:** 각 edge를 통해 들어오는/나가는 전류\(current\)
* **출력:** 각 node에 연결된 모든 edge를 통해 들어오는/나가는 전류의 합\(충전/방전량\) 
  * 단, 화살표 방향의 전류 흐름을 positive, 반대방향의 흐름을 negative로 기준한다. 
* 즉, $$A^\top$$는 **각 edge의 전류 흐름을 입력하면, 각 node의 전류 입출 총량을 출력**하는 행렬이다. 

### $$A^\top$$ 의 nullspace는 어떤 의미를 가질까? 

$$A^\top\bm{y}=\bm{0}$$은 **응용수학에서** 아마도\(probably\) **가장 중요한 방정식**이다. \(by Prof. Strang\) 

* $$A^\top\bm{y}=\begin{bmatrix} -1&0&-1&-1&0\\1&-1&0&0&0\\0&1&1&0&-1\\0&0&0&1&1 \\\end{bmatrix}\underbrace{\begin{bmatrix}y_1\\y_2\\y_3\\y_4\\y_5 \end{bmatrix}}_{\text{input}} =\underbrace{\begin{bmatrix}-y_1-y_3-y_4\\y_1-y_2\\y_2+y_3-y_5\\y_4+y_5 \end{bmatrix}}_{\text{output}} =\begin{bmatrix} 0 \\ 0 \\ 0\\ 0\end{bmatrix}=\bm{0}$$
* 모든 node로 흐르는 모든 전류의 총량을 0이 되게하는, 각 edge의 전류흐름이다! 
  * 전류의 in/out의 총량이 동일해야 한다는 conservation law\(보존법칙\)이다. 
  * 즉, 새로 주입되어나 축적되는 전류가 없이 총량이 보존되어 순환한다는 의미. 
* 이 법칙에는 유명한 이름이 있다: **키르히호프의 전류법칙**, i.e. **Kirchhoff's Current Law\(KCL\)**!  
  * Kirchhoff의 영어 발음은 컬\[r\]커프\[f\]에 가깝다. 
  * 혹시 모르더라도 저런 법칙이 있다는 것만 알면 된다. 

#### Elimination을 하지 않고 그래프 구조를 통해 left nullspace를 바로 구할 수 있을까? 

* KCL을 만족한다는 것은 회로에 존재하는 **모든 loop에서 순환하는 전류의 총량이 같다**는 의미다. 
  * Loop를 도는 과정에서 전류가 새나가거나 새로 유입되서는 안된다. 
  * 이러한 loop를 형성하는 벡터 $$\bm{y}$$들은 KCL을 만족\($$A^\top$$의 nullspace에 존재\)할 것이다. 
  * 어떤 loop들을 선택하는 것이 KCL을 만족하는 부분공간의 적절한 기저가 될까? 
* 전체 그래프에는 **3개의 loop**를 가지고 있다. \[Fig. 4\]

![\[Fig. 4\]](../.gitbook/assets/image%20%2810%29.png)

* 그러나 **2개의 loop**\(1 & 2\)의 조합만으로 전체 그래프를 커버할 수 있다. 
  * Loop 1은 Loop 2와 서로 겹치지 않은 부분이 있다. **\(independent\)**  
  * Loop 1과 Loop 2만으로 전체 loop를 표현할 수 있다. **\(span\)**
  * Loop 3는 Loop 1와 Loop 2의 합으로 표현할 수 있다. **\(dependent\)**
* Loop 1 & 2의 전류 순환을 표현하는 $$\bm{y}$$는 **left nullspace의 기저**가 될 수 있다. 
  * **Loop 1 :** $$\begin{bmatrix}y_1\\y_2\\y_3\\y_4\\y_5 \end{bmatrix}=\begin{bmatrix}1 \\ 1 \\ -1 \\0 \\ 0\end{bmatrix}$$ , **Loop 2 :** $$\begin{bmatrix}y_1\\y_2\\y_3\\y_4\\y_5 \end{bmatrix}=\begin{bmatrix}0\\0\\1\\-1\\1\end{bmatrix}$$ 
  * 전류를 1만큼 보냈을때 계속 순환하도록, 보라색 화살표 방향과 같으면 +1, 다르면 -1. 
  * 순환방향은 CCW\(counter clockwise; 반시계방향\)을 기준으로 한다. 
* Loop 3를 확인해보면 위 두 벡터의 선형조합\(Loop 1 + Loop 2\)임을 알 수 있다. \(선형종속\) 
  * **Loop 3:** $$\begin{bmatrix}y_1\\y_2\\y_3\\y_4\\y_5 \end{bmatrix}=\begin{bmatrix}1 \\ 1 \\ 0 \\-1 \\ 1\end{bmatrix}$$ 
  * Loop 1 & 2에서 보라색 화살표의 방향이 반대이므로 $$y_3$$는 상쇄. 

{% hint style="info" %}
그래프의 loop의 개수는 incidence matrix의 left nullspace의 차원과 같다. 
{% endhint %}

{% hint style="info" %}
Loop를 이루는 edge들의 전류가 순환하는 $$\bm{y}$$는 KCL를 만족한다.

* $$A^\top\bm{y}=\bm{0}$$ 이므로 $$A^\top$$의 해당 column과 $$A$$의 해당 row가 선형종속이다. 
* **즉, loop의 구성요소가 되는 edge에 해당하는 행렬의 row끼리는 선형종속이다!** 
{% endhint %}

### $$A$$ 의 row space는 어떤 물리적 의미를 가질까? 

* $$A$$의 row space, 즉, $$A^\top$$의 column space의 basis를 찾아보자. 
  * $$A^\top\bm{y}=\begin{bmatrix} -1&0&-1&-1&0\\1&-1&0&0&0\\0&1&1&0&-1\\0&0&0&1&1 \\\end{bmatrix}\underbrace{\begin{bmatrix}y_1\\y_2\\y_3\\y_4\\y_5 \end{bmatrix}}_{\text{input}} =\underbrace{\begin{bmatrix}-y_1-y_3-y_4\\y_1-y_2\\y_2+y_3-y_5\\y_4+y_5 \end{bmatrix}}_{\text{output}} $$ 
* 위에서 살펴봤듯이, 이 행렬의 rank는 3이고, 처음 3개의 열은 loop를 형성하므로 선형종속이다. 
* 그렇다면, $$A^\top$$의 column space의 기저는 1, 2, 4번째 column이 될 수 있다. 

#### Row space\(edge space\)의 기저들이 그래프에서 갖는 의미를 알아보자. 

* 다음 그래프에서\[Fig. 5\], 빨간 edge들이 row space의 기저를 표시한 것이다. 
  * 더 작지만 loop가 없는 새로운 그래프가 나타냈다. 
* **Loop가 없는 그래프를 tree\(트리\)라고 부른다.** 
  * 그래프에서 선형종속은 loop에 의해서 만들어진다. 
  * Tree에서 단 하나의 edge만 더 연결해도 loop가 생긴다. 

![\[Fig. 5\]](../.gitbook/assets/image%20%2846%29.png)

{% hint style="info" %}
* Loop없이 전체 node를 연결할 수 있는 edge의 집합

  = 선형종속 없이 전체 row space를 span할 수 있는 row vector의 집합\(basis\).
{% endhint %}

### 차원의 공식들은 어떤 물리적 의미를 가질까? 

* **기존의 지식:** $$\text{dim}(\mathcal{N}(A^\top))=m-r$$
* **조금 전 알게된 것:** $$r=n-1$$ \(1은 $$A$$의 nullspace가 이루는 차원이었다.\)
* $$\begin{aligned} &\text{dim}(\mathcal{N}(A^\top))=m-r \\ &= \text{# of loops} - (\text{# of nodes}-1)\end{aligned}$$
* 이를 정리한 것은 **Euler's Formula**\(오일러의 공식\)이라고 한다!  
  * $$\text{# of nodes}-\text{# of edges}+\text{# of loops}=1$$
  * 그래프에서 node는 0차원, edge는 1차원, loop는 2차원 객체 
  * 이는 모든 그래프 형상\(topology\)에 대해서 성립한다. 

## 하나의 그림으로 정리해보자. 

#### 다음 그림\[Fig. 6\]를 통해 4대 부분공간이 실제 전기회로 application이 어떤 의미를 갖는지 음미해보자. 

![\[Fig. 6\]](../.gitbook/assets/image%20%2888%29.png)

#### 회로의 평형상태는 특수한 상황이고, 전위차나 전류의 유입이 발생하는 회로가 더 일반적이다. 

* 예를 들어, node 2와 node 1사이에 12V 배터리를 연결하면 평형은 깨진다. \(전류가 흐른다\) 
  * $$x_2 -x_1 = 12 \neq 0$$
* 이때의 $$\bm{x}$$는 nullspace의 원소가 아니다. 

**다음 두 가지 상황을 보다 일반화된 식으로 표현해보자.** 

* **전위차가 존재할 경우**\(e.g. 전압원\(배터리\)\): $$A\bm{x}=\bm{e}$$\(존재하지 않을 경우: $$\bm{e}=\bm{0}$$\)
* **전류의 유입/유출이 존재할 경우**\(e.g. 전류원, 캐퍼시터\): $$A^\top\bm{x}=\bm{f}$$\(존재하지 않을 경우: $$\bm{f}=\bm{0}$$\)

#### 전압과 전류 사이를 이어주는 법칙은 '옴의 법칙'이다. 

* 둘 사이를 매개하는 변환을 행렬 $$C$$로 나타내고 있다. 
* 옴의 법칙은 너무 유명할 뿐더러\($$I=V/R$$\), 지금 수업 내용과 직접 관련은 없다.  

#### 전체 그림은 다음 식 하나로 요약된다. 

$$
A^\top C A\bm{x}=\bm{f}
$$

* 이 행렬의 형태를 기억하자! 
  * $$A^\top CA$$ 혹은 $$A^\top A$$의 형태
* 실제 공학문제에 적용되는 응용수학은 이와 같은 평형을 다룬다.  
  * Balance equation / equilibrium

