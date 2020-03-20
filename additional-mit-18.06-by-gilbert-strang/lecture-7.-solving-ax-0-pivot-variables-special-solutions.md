# Lecture 7. Solving Ax=0: Pivot Variables, Special Solutions

### Previously..

#### 우리는 elimination, decomposition, vector space에 대해 배웠다. 

* 그런데 어떻게 vector space안의 모든 원소들을 기술할 수 있을까? 
* 이번 챕터에서는 **nullspace**에 대해 기술해볼 것이다. \($$A\bm{x}=\bm{0}$$을 푼다는 이야기다.\) 

#### 지금까지는 매우 이상적인 상황만 다뤘다. 

* **Invertible**\(역행렬이 존재하는\) **square matrix**\(정방행렬\)만을 다뤘다. 
* 이 경우에는 nontrivial한\($$\bm{x}\neq \bm{0}$$\) nullspace가 존재하지 않았다.  

#### 이제부터는 **rectangular matrix**\(직사각행렬\)을 다룰 것이다. 

* 일부러 nullspace가 존재하는 행렬을 고려하기 위함이다. 
* 물론 직사각행렬도 nullspace가 존재하지 않을 수도 있다. 
* 사실 정사각행렬도 linearly dependent한 column\(=row\)이 있는 경우는 nullspace 존재.  
* 일단 지금은 무슨 소린지 몰라도 괜찮다. 
* 이상적인 상황\(Invertible square matrix\)에서 일반적인 방향으로 확장이라고 생각하자. 

#### 직사각행렬을 다루기 위해서는 기존에 우리가 알고있던 **elimination을 확장**해나가야 한다. 

* \(열 교환을 고려했음에도\) zero pivot을 피할 방법이 없으면 기존에는 진행을 멈췄다\(failed\).
  * 바로 거기서 우리는 더 나아갈 것이다.
* zero pivot이 나타난다는 것은 행렬의 column이 다른 column들에 dependent하다는 것. 
  * elimination의 과정을 통해 이런 것들이 자동적으로 드러나게 될 것 이다. 
* Pivot이 없는 column이 나타나므로 더이상 upper triangular 모양을 만들 수 없다. 
  * 계단의 길이가 달라지는 새로운 모양을 _Row Echelon Form_\(REF\)라고 부른다.
  * 여기서 멈추지 않고 한 단계 더 나아갈 수도 있다: _Reduced Row Echelon Form_\(RREF\) 
* **elimination 과정 중**에 nullspace는 변하지 않는다.\(**solution은 변하지 않는다**.\) 
  * 그러나 column space는 elementary operation을 할때마다 변한다. \(**column은 변한다**.\) 

### **How to solve** $$A\bm{x}=\bm{0}$$ **with REF** 

* 다음 선형방정식계의 해를 구해보자. 
* $$\begin{cases}\begin{aligned}   x_1 + 2x_2 +2x_3 &+ {2x_4} &= 0 \\   2x_1 + 4x_2 +6x_3 &+ {8x_4} &= 0 \\   3x_1+ 6x_2 +8x_3 &+ {10x_4 } &= 0 \\  \end{aligned}\end{cases}$$ 
* $$A\bm{x}=\bm{0}$$의 해를 구하는 것은 직사각행렬 $$A$$의 nullspace를 구하는 것과 같다. 
  * $$A$$의 차원 :$$(m, n) = (3, 4)$$

#### 먼저 가우스 소거법에서 시작해보자. 

* $$A\bm{x}=\bm{0} \; \rightsquigarrow \;U\bm{x}=\bm{0} $$ \(squiggle arrow는 elimination step\(s\)을 의미\)  
* 예시: $$A=\begin{bmatrix} 1&2&2&2 \\ 2&4&6&8 \\ 3&6&8&10 \end{bmatrix}\rightsquigarrow \begin{bmatrix} 1&2&2&2 \\ 0&0&2&4 \\ 0&0&2&4 \end{bmatrix}\rightsquigarrow \begin{bmatrix} \fbox{1}&2&2&2 \\ 0&0&\fbox{2}&4 \\ 0&0&0&0 \end{bmatrix} = U$$
* **Zero pivot이 나오더라도 계속해서 진행**하는 것이 포인트이다. 
* 완전한 모양의 상삼각형 모양 대신에 불규칙한 층계길이를 가지는 계단\(staircase\)모양이 나왔다. 
  * 이 형태를 **Row Echelon Form\(REF\)**라고 한다. 

#### 여기서 zero row의 의미는?

* 그 자리에 있던 row가 다른 row들의 linear combination이었음. 
* linear system에서 새로운 정보를 주지 않는 **redundant한 equation**이라는 의미. 
* 이러한 redundancy가 **elimination에 의해** 시스템적으로 **걸러내진\(knocked out\)** 것임. 
* elimination은 이러한 행렬의 잉여정보를 없애고 꼭 필요한 정보만 남기려는 reducing 과정. 

#### \(잠깐\) **새로운 용어**들을 정의해보자.

* \(중요\) 여기서 pivot의 갯수를 **rank**라고 한다! \($$r=2$$\)
  * **의미있는 equation의 개수는** 4개 중 **2개**라는 의미이다.
* pivot을 포함하는 column을 **pivot column**이라고 한다. \(1, 3번째\)
  * 대응되는 변수들을 **pivot variable**이라고 한다. \($$x_1 , \; x_3$$\)
  * **pivot variable의 개수:** $$r$$\(rank와 같음\) 
* pivot이 없는 column을 **free column**이라고 한다. \(2, 4번째\)
  * 대응되는 변수들을 **free variable**이라고 한다. \($$x_2, \; x_4$$\)
  * **'free' variable인 이유:** 어떤 수든지 자유롭게\(freely\) 할당할 수 있기 때문. 
  * **free variable의 개수:** $$n-r$$ \(전체 column개수 - rank\) 
* $$r$$개의 변수가 고정이고, $$n-r$$개의 변수가 자유롭다는 의미? 
  * 전체 $$n$$차원 공간에서 $$n-r$$차원의 hyperplane\(subspace\)를 구성하고 있다는 것. 

#### \(다시 계속\) 최종 REF를 방정식으로 풀어 써보자.

* $$U=\begin{bmatrix} \fbox{1}&2&2&2 \\ 0&0&\fbox{2}&4 \\ 0&0&0&0 \end{bmatrix} \Rightarrow \; \begin{aligned} x_1 + 2x_2 +2x_3 + 2x_4 = 0 \\ 2x_3 + 4x_4 = 0\end{aligned}$$

#### Free variable\($$x_2, \; x_4 $$\)들은 말 그대로 'freely' 결정해도 된다. \(2차원의 자유도\)

* ..라고 하지만 실제로는, by convention, 정하는 방법이 있다.
* 여러 가능성 가운데 가장 쉽고 간단한 값들을 선택하는 것이다. 

#### 우리가 선택할 특별한 $$(x_2, x_4)$$는 $$(1, 0)$$과 $$(0,1)$$이다.

* 위 선택은 서로 **완전히 orthogonal**하기 때문에 전혀 중첩되는 성분이 없음. 
* 다른 아무 좌표들도 가능하지만, 가장 직관적이면서도 계산하기 편리한 선택!  

#### 이제 우리가 선택한 free variable들을 고정해놓고, pivot variable을 구하면 된다!

* 위 방정식들에 우리가 정한 free variable들을 대입하고 pivot variable에 대해 풀어보자. 
* $$(x_2 , x_4)=(1,0)$$일때는 $$(x_1 , x_3)=(-2,0)$$
* $$(x_2 , x_4)=(0,1)$$일때는 $$(x_1 , x_3)=(2,-2)$$

#### 이로써 확실히 nullspace에 속하는 **두 개의 벡터**\(solution\)를 찾아냈다. 

* $$[-2, 1, 0, 0]^\top$$and $$[2, 0, -2, 1]^\top$$
* 유일한 벡터들이 아니며, 주어진 자유도 안에서 '특별히 선택'한 것들이다.
* 그래서 Strang 교수님은 이 벡터들을 **special solution**라고 부른다. 
* special solution의 개수는 free variable의 개수와 같다. 

#### 다른 벡터들도 찾아낼 수 있을까? 첫번째 벡터를 한번 분석해보자.

* 원래 행렬에서 1행의 2배를 2행에 빼주면 $$A\bm{x}=\bm{0}$$를 만족한다는 의미임을 알 수 있다.
* 결국 두 행의 비율이 **2:1**만 유지한다면 **6:3**이든 **100:50**이든 관계가 없다는 것이다. 
* 따라서 **위 벡터들의 실수배는 모두 solution**이 될 수 있다. \(nullspace안에 있다.\) 
* 이러한 벡터의 실수배\(스칼라곱\)의 집합은 **직선\(subspace\)을 구성**한다. 

#### 이제 확실히 nullspace에 속하는 **두 개의 직선**\(solution\)을 찾아냈다.

* $$c_1\cdot[-2, 1, 0, 0]^\top$$and $$c_2\cdot[2, 0, -2, 1]^\top$$\($$c_1, c_2 \in \mathbb{R}$$\)

#### 또 다른 벡터들은 없을까? 

* _**Lecture 6. Nullspace**_에서 살펴보았듯이 nullspace는 subspace이다. 
* 두 개의 직선이 하나의 subspace안에 공존하기 위해서 필요한 조건은 뭘까?
  * _**Lecture 6.의 Two subspaces**_ $$S$$ _**and**_ $$T$$를 참조하라. 
  * 2개의 직선 안의 가능한 모든 벡터들의 합을 nullspace가 포함하는 것이다.
  * 다른 말로하면, 이들 직선을 대표하는 **2개의 벡터의 모든 선형조합**을 포함하는 것. 

#### 따라서, **최종 solution**은 다음과 같다. 

* $$x=c_1 \begin{bmatrix} -2\\1\\0\\0 \end{bmatrix} + c_2 \begin{bmatrix} 2\\0\\-2\\1 \end{bmatrix}$$
* 위 두 벡터들의 선형조합으로 전체 nullspace를 완전하게 표현될 수 있다.  
  * 2차원 nullspace를 표현하는데 2개의 특정 벡터가 사용됨.  
  * 이 두개의 벡터를 nullspace의 **기저벡터\(basis vector\)**라고 한다. 
* 이렇게 벡터들의 선형조합이 subspace를 커버하는 상태를 동사로 **span**한다고 함. 
* 기저벡터를 다른 말로 하면, subspace를 span하는 서로 선형독립인 벡터의 집합.

### **How to solve** $$A\bm{x}=\bm{0}$$ **with RREF**

#### **여기서 좀 더 나가보자.** 

* REF에서 한단계 더 행렬을 clean up할 수 있다. 
* 그 형태를 _**Reduced**_ ****Row Echelon Form이라고 부른다. 
* 한단계 더 zero-out된, 바짝 졸여진 상태라는 느낌으로 reduced라는 단어를 사용한다. 
* \(참고\) 소거법의 관점에서는 Gauss-Jordan elimination이고 한다. \(조던이 단계를 추가\)  
* 모든 정보를 가능한 한 분명하게 보여주도록 하는 형태이다. \(as clear as it can be\) 
  * solution이 저절로 드러나게 함으로써 back-substitution 절차를 간소화!

#### **Reduced Row Echelon Form**\(RREF\) : \(1\) 기존의 절차\(REF\) + \(2\) 추가적 절차\($$\alpha$$\)

\(1\) 기존의 elimination 절차 

* Row Echelon Form\(REF\)을 만드는 것 까지가 목표
* pivot 아래에 있는 수들을 zero로 만들기 
* 위에 있는 row를 실수배해서 아래 row에 더하거나 빼는 과정 **\(+ 열교환 if needed\)**
* 위에서부터 downward로 진행됨: **Forward phase**

\(2\) 추가적 elimination 절차 

* 완전한 Reduced REF\(RREF\)를 만드는 것 까지가 목표 
* pivot 위에 있는 수들도 zero로 만들기 **\(+ pivot이 1이 되도록 실수곱 if not already\)**
* 아래에 있는 row를 실수배해서 위 row에 더하거나 빼는 과정
* 아래서부터 upward로 진행됨: **Backward phase**

**Note**: 텍스트에 따라 pivot을 1로 만드는 단계가 \(1\) 과정에 포함되는 경우도 있다.

#### 실제 예시를 보자. 

* $$U=\begin{bmatrix} 1&2&2&2 \\ 0&0&2&4 \\ 0&0&0&0 \end{bmatrix}\rightsquigarrow \begin{bmatrix} 1&2&0&-2 \\ 0&0&2&4 \\ 0&0&2&4 \end{bmatrix}\rightsquigarrow \begin{bmatrix} \fbox{1}&2&0&-2 \\ 0&0&\fbox{1}&2 \\ 0&0&0&0 \end{bmatrix}=R$$ 
  * i.e. $$U\bm{x}=\bm{0} \; \rightsquigarrow R\bm{x}=\bm{0} $$
* 이미 배웠던 것처럼 back-substitution으로 똑같이 풀 수 있다. 
* 그런데 직접 해보면 이미 계수가 정리되어 답을 눈으로 그대로 읽을 수 있음을 알 수 있다. 
* 그 과정을 automated된 프로세스로 만들어보자. \(축약된 절차일 뿐이다\) 

#### **RREF에서 nullspace의 기저벡터를 바로 읽어\(read off\)보자!**  

RREF로 나타내고 나면 항상 다음과 같은 꼴이 된다:$$\begin{bmatrix} I & F \\ 0 & 0 \end{bmatrix}$$

* $$I$$: pivot column들이 모인 행렬\(항등행렬\) 
* $$F$$: free column들이 모인 행렬
* 단, column들\($$I$$와 $$F$$\)은 **순서가 뒤섞여 있을 수 있다**.  

전체 시스템은 다음과 같이 나타낼 수 있다: $$RX=\begin{bmatrix} I & F \\ 0 & 0 \end{bmatrix}X=\begin{bmatrix} I & F \\ 0 & 0 \end{bmatrix}\begin{bmatrix}X_{pivot}\\ X_{free}\end{bmatrix}=\bm{0}$$ 

* $$X$$: special solution\($$\bm{x}_1, ...,\bm{x}_{n-r}$$\)들을 column으로 갖는 행렬 
* 한 번에 모든 special solution을 구하기 위한 목적으로 도입 

이를 block matrix multiplication으로 한방에 풀어보면: 

* $$X=\begin{bmatrix}X_{pivot}\\ X_{free}\end{bmatrix}=\begin{bmatrix} -F \\ I \end{bmatrix}$$ , i.e. $$\begin{align*} X_{pivot}&=-F \\ X_{free}&=I \end{align*}$$
* 역시, row들\($$X_{pivot}$$와 $$X_{free}$$\)도 **순서가 뒤섞여 있을 수 있다**.  

Element-level에서 몇가지 형태적 예시를 살펴보면: 

* $$R$$의 pivot column에 대응되는 $$X$$의 행에 음수화한 $$\red F$$를 copy. 
* $$R$$의 free column 대응되는 $$X$$의 행에 행등행 $$\green I$$를 fill up. 
* $$RX=\begin{bmatrix}  \fbox{1}&\red f& \red f& \red f\\ 0&0&0&0\\ 0&0&0&0 \end{bmatrix}  \begin{bmatrix} - \red{f} & -\red{f} & -\red f \\ \green1&\green0&\green0 \\ \green0&\green1&\green0 \\ \green0&\green0&\green1 \end{bmatrix} =\begin{bmatrix} 0&0&0\\ 0&0&0\\ 0&0&0 \end{bmatrix}$$
* $$RX=\begin{bmatrix}  \fbox{1}&0&\red f&\red f\\ 0&\fbox{1}&\red f&\red f\\ 0&0&0&0 \end{bmatrix}  \begin{bmatrix} -\red f & -\red f  \\ -\red f&-\red f \\ \green1&\green0 \\ \green0&\green1 \end{bmatrix} =\begin{bmatrix} 0&0\\ 0&0\\ 0&0 \end{bmatrix}$$ 
* $$RX=\begin{bmatrix}  \fbox{1}&\red f&0&\red f\\ 0& \red 0 &\fbox{1}&\red f\\ 0&0&0&0 \end{bmatrix}  \begin{bmatrix} -\red f & -\red f  \\ \green1 & \green0 \\ \red 0&-\red f \\ \green0&\green1 \end{bmatrix} =\begin{bmatrix} 0&0\\ 0&0\\ 0&0 \end{bmatrix}$$ **\(순서가 뒤섞인 경우\)** 
* $$RX=\begin{bmatrix}  \fbox{1}&0&0&\red f\\ 0& \fbox 1 &0&\red f\\ 0&0&\fbox 1&\red f \end{bmatrix}  \begin{bmatrix} -\red f \\ -\red f \\ -\red f \\ \green1 \end{bmatrix} =\begin{bmatrix} 0\\ 0\\ 0 \end{bmatrix}$$ 

우리의 예시에서는:

* $$R$$의 1열, 3열\(pivot columns\)에 대응되는 $$X$$의 1행, 3행은 음수화한 $$F$$를 copy. 
* $$R$$의 2열, 4열\(free columns\)에 대응되는 $$X$$의 2행, 4행은 항등행렬 $$I$$로 fill up.  
* $$X=\begin{bmatrix} -2&2\\1&0\\0&-2\\0&1 \end{bmatrix} $$ : 약속한 대로 각 column들이 special solution들이다!

위에서 우리가 구한 벡터들과 일치함을 확인! 선형조합형태로 적어주면 끝! 

* $$x=c_1 \begin{bmatrix} -2\\1\\0\\0 \end{bmatrix} + c_2 \begin{bmatrix} 2\\0\\-2\\1 \end{bmatrix}$$ 

#### **다른 방법도 있다!**

* MML 책에서 소개하는 **The minus-1 trick**이 더 간편한 것 같다.
* 위 방법으로 구한 special solution들에 **-1을 곱한 값**으로 나온다. 
  * 기저벡터가 반대 방향이라도 span하는 subspace는 동일. 

### 도대체 왜 이렇게 푸는가? 

* 굉장히 놀랍게도 아무도 왜 nullspace를 저렇게 구하는지 설명해주지 않는다. 
  * 내가 잘 못찾는 건가? 
  * 단지 해를 구하는 과정\(mechanics\)만을 알려주기 바쁘다. 
  * 대부분의 사람들이 그 이유에 대해 관심이 없다는 것이 놀랍다. 
  * 너무 당연하게 느껴서 그러는 걸까? 
* 아마 textbook에는 자세히 나와있을 것 같다. \(나중에 찾아보자.\) 
* 다음은 스스로 생각해본 이유를 정리해본 것이다. 

#### Nullspace의 차원은?  

* 입력의 전체 차원이 $$n=4$$이고, 그 중에서 column space로 선형변환되는 차원은 $$r=2$$이다. 
* 나머지 차원$$n-r=2$$은 어디로 갔을까? 원점으로 빨려들어갔다. \(nullspace\) 
* 즉, nullspace는 4차원\($$n$$\) 공간 안의 2차원\($$n-r$$\) 평면이다. 
* 다시말해, **nullspace를 구하는 일은** $$n$$**차원 공간에서** $$n-r$$**개의 기저벡터를 찾는 일**이다. 
* 기저벡터\(basis vector\):  위에서 잠시 언급했지만, 더 자세한 내용은 문서내 검색을 해보자. 

#### Nullspace의 기저벡터는 어떻게 찾을 수 있을까?

가시화 하기 쉽도록, **3차원 공간안의 어떤 2차원 평면**을 생각해보자. 

* 이 평면의 기저벡터는 2개의 3차원 벡터이다.  \(당연히 평면 위에 존재\) 
* 이 평면 안에서 2개의 좌표를 임의로 고정하면, 가능한 남은 1개의 좌표는 딱 하나 밖에 없다.  
* 이 평면의 자유도는 2차원이므로, 두개의 좌표를 자유롭게 선택하면, 더이상 남은 자유도가 없기 때문.  
* 이 평면의 2개의 좌표가 선형변화하면, 나머지 1개의 좌표도 선형변화한다.\(그림을 상상해보라.\)  

**일반화**해서 생각해보자. 

* Nullspace는 하나의 기저벡터를 지명하기 위해, 자신의 차원만큼의 좌표를 자유롭게 선택할 수 있다. 
  * 나머지 좌표는 제한조건\(선형방정식계\)에 의해 유일하게 결정된다.  
    * pivot variable은 free variable에 의해 유일하게 결정 
* 기저벡터는 nullspace의 차원 수만큼 존재한다. 
* 기저벡터들은 본래의 정의에 따라 서로 선형독립이어야 한다.  
  * 자유롭게 선택한 좌표성분들이 선형종속이면 나머지 좌표성분들 또한 선형종속이다. 
    * pivot variable이 선형종속이면 그에 따라유일하게 결정된 free variable도 선형종속. 
  * 반대로, 자유롭게 선택한 좌표성분들이 선형독립이면 나머지 좌표성분들 또한 선형독립이다.  
  * 즉, **자유 좌표성분을 선형독립으로 결정하면 기저벡터 전체도 선형독립**이 된다. 

위 내용을 **정리하면** 다음과 같다. 

* $$n-r$$차원의 nullspace의 기저벡터 구하는 방법:  
  * 총 $$n-r$$개의 기저벡터를 찾는다. 
  * 각 기저벡터는 $$n-r$$개의 **서로 선형독립**인 좌표성분\(**free variable**\)을 가진다. 
  * 각 기저벡터의 나머지$$r$$개의 좌표성분\(**pivot variable**\)은 방정식에 의해 유일하게 결정된다. 

#### 유의사항!

\(1\) 선형독립인 자유로운 좌표성분 중 가장 간단한 형태는 각 좌표축 위의 단위벡터이다. 

* **2개의 자유성분**$$(x_{free-1}, \ x_{free-2})$$ 의 경우:  $$(1, 0) \text{ and } (0, 1)$$ 

\(2\) **Free variable은 개수를 맞추어주기 위함일뿐, 어떤 좌표 성분인지는 중요하지 않음.** 

* 예를 들기 위해, 위의 상황을 재연해보자: 
  * $$U=\begin{bmatrix} \fbox{1}&2&2&2 \\ 0&0&\fbox{2}&4 \\ 0&0&0&0 \end{bmatrix} \Rightarrow \; \begin{aligned} x_1 + 2x_2 +2x_3 + 2x_4 = 0 \\ 2x_3 + 4x_4 = 0\end{aligned}$$ 
* \(기존과는 반대로\)$$(x_2 , x_4)$$을 pivot variable로, $$(x_1, x_3)$$을 free variable로 취급해보자. 
* **기존 솔루션**:     $$x=c_1 \begin{bmatrix} -2\\1\\0\\0 \end{bmatrix} + c_2 \begin{bmatrix} 2\\0\\-2\\1 \end{bmatrix}$$ 
* **새로운 솔루션**: $$x=d_1 \begin{bmatrix} 1\\-1/2\\0\\0 \end{bmatrix} + d_2 \begin{bmatrix} 0\\-1/2\\1\\-1/2 \end{bmatrix}$$ 
* 새로운 솔루션의 기저벡터는 모두 기존 솔루션 subspace안에 존재함: 
  * 첫번째 벡터는$$(c_1,c_2)=(-\frac{1}{2}, 0) $$ 
  * 첫번째 벡터는$$(c_1,c_2)=(-\frac{1}{2},-\frac{1}{2}) $$
* null space 안에 존재하는 특수한 벡터 $$ \begin{bmatrix} 0 \\1 \\ -2\\1 \end{bmatrix}$$를 두가지 선형결합으로 모두 표현 가능.  
  * $$(c_1,c_2)=(1, \ \ 1)$$
  * $$(d_1,d_2)=(0, -2)$$
* 즉, 두 솔루션은 같은 subspace를 span함. \(일치\)  
* **결론:** pivot/free의 개념은 공간의 차원 자유도와 기저벡터의 개수 등을 맞추려는 trick일 뿐임. 
  * elimination 과정을 통해 찾아진$$n-r$$이라는 차원수를 자연스럽게 활용하게 하는 기계적 장치.
  * 어떤 성분\(몇번째 좌표\)을 선택하느냐는 사실 처음부터 중요하지 않았음. 

### 용어 주의\(Additional\)

* **Forward** elimination $$\leftrightarrow $$ **Back**-substitution
  * 가우스 소거법으로 선형시스템의 해를 구할때의 두 단계를 대비시키는 용어 
  * 위에서 아래로 소거 후, 반대로 아래서 위로 대입하면서 푸는 느낌
* **Backward** substitution $$ \leftrightarrow $$ **Forward** substitution
  * LU decomposition을 이용하여 선형계의 해를 구할때 나오는 개념
  * LU분해\(동시에 소거는 완료\)를 통해 선형계를 표현: $$A\bm{x}=LU\bm{x}=\bm{b}$$
  * $$L\bm{y}=\bm{b}$$, $$U\bm{x}=\bm{y}$$ 를 차례로 대입법을 사용해서 푼다.
    * lower triangular matrix $$L$$ : 위에서 아래로 대입\(forward substitution\)
    * upper triangular matrix $$U$$: 아래서 위로 대입\(backward substitution\)
  * back-substitution과 backward substitution은 사실상 거의 차이가 없음.
    * 그러나 context에 따라 다르게 표기하는 경향이 보임. 
* **Forward** phase $$\leftrightarrow$$ **Backward** phase
  * RREF를 구하기 위한 Gauss-Jordan elimination을 수행하는 과정 자체를 두 단계로 구분 
  * 위에서 아래로 소거 / pivot 아래를 0으로 만드는 과정: forward phase \(REF까지\)
  * 아래에서 위로 소거 / pivot 위를 0으로 만드는 과정: backward phase
    * pivot을 1로 만드는 과정은 위 아래 두 과정 중 하나에 포함된다 \(텍스트마다 다름\)
  * forward phase는 위에서 언급한 forward elimination으로 불리는 과정과 동일함 
  * 그러나 backward phase를 backward elimination이라고 부르는 것은 위험할 수 있음  
    * statistics의 regression에서 같은 용어를 다른 의미로 사용 
* 용어 자체가 중요하다기 보다는 그 방향성을 기준으로 두 단계로 구분됨을 인식하는게 중요.



