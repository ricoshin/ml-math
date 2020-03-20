# \(Recitation\) Plane Equation

## Introduction

* 이 추가자료는 다음 [recitation resource](https://www.youtube.com/watch?v=3cMyj8EKFGo&list=PL221E2BBF13BECF6C&index=18)를 기반으로 작성되었다. 
* 우리가 배웠던 벡터를 이용하는 방법과, 고등학교때 배웠던\(?\) **평면의 방정식**을 연결해보자. 
* Homogeneous\($$A\bm{x}=\bm{0}$$\)와 Non-homogeneous solution\($$A\bm{x}=\bm{b}$$\)간의 관계를 알아보자. 

## **다음 방정식을 살펴보자:** $$x-5y+2z=0$$\*\*\*\*

* 3차원에 공간에 constraint가 1개 존재하면, 그 결과는 3-1=2차원의 자유도를 가진다.  
* 방정식의 형태가 선형이므로, 위 식은 2차원 flat한 점들의 집합을 표현하고 있음을 알 수 있다. 
* 즉, 평면\(plane\)을 나타내는 **평면의 방정식**이라는 이야기다. 
* 또하나의 특징은$$(0, \ 0, \ 0)$$를 해로 갖는다는 것이다\(즉, **원점을 지나는 평면**이다.\) 
* 이 평면은 $$\mathbb{R}^3$$안의 2차원 subspace이므로, 2개의 기저벡터로 표현할 수도 있을 것이다. 

### 이 평면을 벡터들의 선형조합으로 표현해보자. 

#### 이 평면의 방정식은 **방정식이 하나뿐인 선형방정식계**로 나타낼 수 있다. 

* $$\begin{bmatrix} \fbox1 & {-5} & 2 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix}= [0]$$
* 즉, 행렬 $$\begin{bmatrix} \fbox 1 &{-5} &2 \end{bmatrix} $$의 nullspace가 바로 우리가 원하는 평면이다. 
* 같은 평면을 벡터들의 combination으로 나타낼 수 있다는 이야기.

#### 기존에 배운 방법대로 nullspace를 구해보자. 

* 방정식이 한개인 경우, elimination이 이미 되어있는 것이나 마찬가지다. 
* 첫번째 pivot을 1이 되도록 scaling만 해주면 된다. \(이 경우는 그마저도 필요없다.\) 
* Nullspace는 Lecture 8.에서 배운 방법 등을 사용하여 쉽게 구할 수 있다. 

### 즉, 평면의 방정식 $$x-5y+2z=0$$ 를 벡터공간으로 나타내면: 

* $$\begin{bmatrix} x \\ y \\ z \end{bmatrix} = c_1\begin{bmatrix} \red{5} \\ \green 1 \\ \green0 \end{bmatrix} + c_2\begin{bmatrix} \red{-2} \\ \green0 \\ \green1 \end{bmatrix}$$
* **상수항이 0인 평면의 방정식은 어떤 선형계의 nullspace와 같은 form을 가진다.**

{% hint style="warning" %}
**이 평면의 법선벡터\(normal vector\)는?**

* **법선벡터:** 평면에 수직\(orthogonal/perpendicular\)인 벡터 
* 위 평면의 법선벡터는 매칭되는 선형계의 행렬을 transpose한 $$\begin{bmatrix} 1 \\-5 \\2 \end{bmatrix}$$가 된다. 

아래 내용들은 아직 배우지 않았지만, 참고하자. 

* **\(참고 1\)** 아래 자세히 보면 법선벡터와 nullspace간의 dot product가 zero임을 알 수 있다.
  *  $$\begin{bmatrix} 1 & {-5} & 2 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix}= [0] \ \Leftrightarrow \ \begin{bmatrix} 1 \\ {-5} \\ 2 \end{bmatrix} \cdot \begin{bmatrix} x \\ y \\ z \end{bmatrix}= 0$$ **\(orthogonal\)**
* **\(참고 2\)** 법선벡터는 행렬 $$\begin{bmatrix} \fbox 1 &{-5} &2 \end{bmatrix} $$의 **row space**이기도 하다. 
  * row space와 nullspace는 orthogonal함을 나중에 배울 것이다. 
{% endhint %}

## 그렇다면 이 녀석은? $$x-5y+2z=9$$

* 이것도 역시 평면이지만, 원점을 지나지는 않는다.
* 위에서 본 평면\($$x-5y+2z=0$$\)에서 우변만 달라졌다.   

### 둘이 무슨 관계가 있을까? 

* 두 평면은 다음 두 관계 중 하나를 갖는다: **교차** or **평행**.

#### 교차하는가? 

* 교차하려면 두 방정식을 동시에 만족하는 해가 있어야 한다. 
* 좌변은 같은데 우변은 다르니 동시에 만족하는 해는 없다. 
  * 두 방정식을 선형계로 묶어 elimination을 해봐도 해가 없음을 알 수 있다. 
  * zero row에 대응하는 $$\bm{b}$$의 성분이 0이 아님. \(모순\) 

#### 그럼 평행하겠지! 

* 그러므로 이 방정식이 나타내는 평면은 **위 평면과 평행한다!** 

### 원점을 통과하는 subspace의 평행이동을 벡터로 나타내기 위해서는:

* \(평행이동 후 평면\) = \(팽행이동을 서술하는 벡터\) + \(팽행이동 전 원점을 통과하는 평면\) 
* \(평행이동 전 원점을 통과하는 평면\)은 위에서 이미 구했다. 
* \(평행이동을 서술하는 벡터\)는 평행이동 후 평면 위의 '아무 점'이나 가리켜도 무방하다. 
  * 이 '아무 점'만 하나 찾으면 끝!

### 그렇다면,$$x-5y+2z=9$$ 위의 점 중에 가장 쉬운 점을 골라보자. 

* 2차원 평면에서는 좌표 2개를 아무렇게나 고르면 나머지 한 점은 평면 방정식에 의해 자동결정된다. 

#### 좌표 2개는 기왕이면 0으로 고르는 것이 계산하기에 편하다. 

* $$x$$의 계수가 1이니 대입하기에 역시 편하다. 나머지 2개의 변수를 모두 0으로 두자.  
* \(Lecture 8.에서 배운 일반적 풀이법과 억지로 매칭시키려다 보니 다소 개연성이 부족해보인다.\)
* \(확실한 설명은, elimination한 후에 free variable을 0으로 두고, pivot variable을 구하라는 것이다.\) 
* $$ y= z=\green 0$$일때, $$x=\red 9$$임을 단박에 알 수 있다. 

#### 평면 위의 가장 쉬운 점은 다음과 같다: $$\begin{bmatrix} \red 9 \\ \green 0 \\ \green0\end{bmatrix}$$ 

### 즉, 평면의 방정식 $$x-5y+2z=9$$ 를 벡터공간으로 나타내면: 

* $$\begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} \red 9 \\ \green 0 \\ \green0\end{bmatrix}+c_1\begin{bmatrix} \red5 \\ \green 1 \\ \green0 \end{bmatrix} + c_2\begin{bmatrix} \red {-2} \\ \green0 \\ \green1 \end{bmatrix}$$\($$A\bm{x}=\bm{b}$$의 완전해와 같은 꼴\) 

#### 0이 아닌 상수항을 가진 평면의 방정식은 어떤 선형계의 complete solution과 같은 form을 가진다.

