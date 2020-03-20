# Lecture 9. Independence, Basis, and Dimension

### Background\(recap\) 

* 아래 내용의 이해를 돕기 위해, free variable과 nullspace의 관계에 대해 생각해보자.  

행렬$$A$$의 크기가 $$m\times n$$이고, $$m<n$$이라고 가정해보자. 

* 방정식의 개수보다 변수의 수가 더 많다. \(옆으로 긴 행렬\) 
* $$A\bm{x}=\bm{0}$$에 대하여 $$\bm{x}\neq\bm{0}$$인 해가 존재한다. \(1차원 이상의 nullspace가 존재\)
* **이유**: 항상 최소한 $$n-m$$개의 free variable이 존재하니까! 

### Linear Independence

#### 벡터들의 집합이 선형독립\(linearly dependent\)하다는 것?

* 어떤 선형조합도 영벡터\($$\bm{0}$$\)를 만들지 않는다.  
* $$c_1\bm{x}_1+c_2\bm{x}_2+\cdots +c_n\bm{x}_n\neq \bm{0}$$ 
* \(단, 모든 벡터를 0의 실수배한 경우를 제외. i.e, $$\text{all } c_i=0$$\)

#### 이 정의를 행렬의 꼴\($$X$$\)로 해석해보자. 

* 행렬의 column들이 선형독립일 조건?
  * $$\begin{bmatrix} | & | & & | \\ \bm{x}_1& \bm{x}_2&\cdots &\bm{x}_n \\ | & | && |  \end{bmatrix}\begin{bmatrix} c_1 \\ c_2 \\ \vdots \\c_m \end{bmatrix} \neq\begin{bmatrix} 0 \\  \vdots \\ 0 \end{bmatrix}$$
  * \(단, 다음의 경우는 제외 : $$\bm{c}=\bm{0}$$\)
* **Nullspace와 비슷한 모양이 나온다!**
  * 선형독립의 개념과 nullspace의 개념을 연결해보자. 

#### Column들의 선형독립성\(Linear independence\)

* **선형종속:** Column들의 선형조합\(전부 0을 곱한 경우를 제외\)으로 $$\bm{0}$$를 만들 수 있을때. 
  * 즉, $$\bm{0}$$이 아닌 nullspace가 존재
* **선형독립:** Column들의 선협조합에 전부 0을 곱한 경우에만 $$\bm{0}$$를 만들 수 있을때.
  * 즉, nullspace의 원소는 오직 $$\bm{0}$$.
* 이는 이미 알고 있던 내용이지만, 선형독립의 정의와 관계가 있다는 점이 새롭다. 

#### 기존에는 다음의 논리전개에 의해 위 내용을 추론할 수 있었다. 

1. **Column vector들이 서로 선형종속관계이다.** \(출발\)
2. 종속성에 의한 redundancy가 elimination에 의해 knocked-out된다. 
3. Pivot column이 없어진 만큼 free column이 생긴다. 
4. Free variable의 갯수만큼 nullspace의 기저벡터, 즉, 차원이 존재한다. 
5. **영벡터 이외의 nullspace가 존재한다**. \(도착\) 

* 이제는 선형종속의 정의에 의해 위의 단계를 건너뛸 수 있다. \($$1\rightarrow5$$\)

#### 임의의 벡터 집합의 선형독립성이 궁금하다면?

* _**그들을 행렬의 column으로 집어넣고 nullspace가 존재하는지 보라!**_ 
  * row에 넣어도 관계는 없다. 이유는 다른 lecture에서 알게된다. 
* Nullspace를 끝까지 구할 필요는 없다. Elimination을 해서 free variable이 나타나는지 보면 된다. 

### Spanning a space

이미 이전 lecture들에서 활용되고 있었던 개념에 이름을 붙여보자. 

* 좀 더 일찍 등장했으면 좋았을 것 같다. 
* 커리큘럼상으론 아직 안배운 상태인데, 지난 설명에서 이미 span이라는 표현을 쓴 것 같기도..

행렬의 column들의 모든 선형조합이 나타내는 subspace를 column space라고 한다. 

* column vector들은 column space를 _span한다_. 

Nullspace는 special solution들을 기저벡터로 하며, 이들의 모든 선형조합이 나타내는 subspace이다. 

* special vector들은 nullspace를 _span한다_.
* 기저벡터들은 특정 subspace를 _span한다_.

즉, **벡터들이 벡터공간을** _**span한다**_는 것은 **벡터공간이 그들의 선형조합으로 이루어져 있음**을 의미. 

* 이 강의에서는 동사로 주로 사용한다. 
* 다른 텍스트에서는 **span한 결과**를 나타내기 위해 **명사로 사용**하기도 한다. 

### Basis for a space

#### 어떤 공간의 기저\(basis\)는 다음 두가지 성질을 가지는 벡터의 리스트를 말한다. 

1. 서로 선형독립이다.  
2. 그 공간을 span한다. 

#### $$\mathbb{R}^n$$에서 $$n$$개의 벡터들이 기저를 형성할 조건은?

* 그 벡터들을 열벡터로 하는 행렬\($$n\times n$$\)의 nullspace는 오직 영벡터. 
* 즉, 행렬의 역행렬이 존재\(invertible\)해야 한다.  
* 위에서 알아본 사실과 다를게 없다. 그냥 복습. 

### Dimension of a space

* 한 공간의 기저는 무한개가 존재한다.
* 그러나 **모든 기저들이 가지는 벡터의 총 개수는 전부 같다**. 
  * 이 개수를 그 공간의 **차원\(dimension\)**이라고 한다! 
* 기저의 벡터 수는 딱 공간의 차원만큼 필요하다. 
  * 더 많으면 선형종속이 되어버린다. _\(조건 1 위반\)_
  * 더 적으면 전체공간을 span할 수 없다. _\(조건 2 위반\)_ 

### 정리해보자. 

\(1\) Number of **pivot** columns **=** $$r$$ **=**  dimension of $$\mathcal{C}(A)$$

\(2\) Number of **free** columns **=** $$n-r$$**=** dimension of $$\mathcal{N}(A)$$

* $$r$$: rank of$$A$$
* $$n$$: number of columns of $$A$$
* $$\mathcal{C}(A)$$: column space of $$A$$
* $$\mathcal{N}(A)$$: nullspace of $$A$$
* 지금까지의 개념을 잘 이해를 하고 있으면 사실 뻔한 내용이다.  

다음 디테일에 유의하자. 

* _rank_ of **matrix** = _dimension_ of **column space** of that matrix 
* rank는 행렬이 가지는 속성, 차원은 subspace가 가지는 속성! 
* 반대로, subspace의 rank라던지, matrix의 dimension 따위는 없다. 

