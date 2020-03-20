---
description: '2장: 선형대수 (17-19.p)'
---

# Chapter 2: Linear Algebra

* 어떤 개념을 formalizing\(공식화\)할 때는 보통 다음 두가지를 구성한다: 
  * 객체들 \(심벌, 부호로 나타내지는\)
  * 그리고 그 객체들을 다룰 수 있는 규칙의 집합
* 그렇다면 **선형대수**\(Linear algebra\)는 무엇이라고 할 수 있을까?
  * 다음 두 가지에 대한 연구이다!
    * 벡터들
    * 벡터들을 조작하는 규칙들
* 고등학교때 배웠던 벡터
  * 기하벡터\(Geometric vectors\):  $$\vec{x}, \vec{y}$$
* 이 책에서 논하게 될 벡터
  * 보다 일반화된 벡터 개념: $$\mathbf{x}, \mathbf{y}$$
* **벡터**의 개념 
  * 다음을 만족하는 object는 모두 벡터이다.
    * **Addition**: object끼리 더할 수 있으며, 그 결과 같은 종류의 object가 나온다.
    * **Scaling**: object에 scalar를 곱할 수 있으며, 그 결과 같은 종류의 object가 나온다. 
      * scalar는 고등학교때 배운 '스칼라'이며, 실제 발음은 '스케일러'. 
  * 즉, 벡터끼리 더하거나 스칼라 곱을 했을때 그 결과가 벡터이면 된다.
  * 예시: 벡터의 instance
    * 기하벡터 Geometric vectors
    * 다항식 Polynomials
    * 오디오 신호 Audio signals
    * $$\mathbb{R}^n$$**의 원소 \(**$$n$$**개의 원소를 갖는 튜플\)**
      * 이 책에서 주로 사용하는 벡터의 개념 
      * 예시:$$\mathbf{a}= \begin{bmatrix} 1 \\ 2 \\ 3 \end{bmatrix} \in \mathbb{R}^3$$ 
      * 벡터인 이유: 아래 두가지 조건 만족 
        * $$\mathbf{a}, \mathbf{b} \in \mathbb{R}^n, \lambda\in\mathbb{R}$$일때,
          * $$\mathbf{a}+\mathbf{b}= \mathbf{c}\in\mathbb{R}^n$$\(Addition\)
          * $$\lambda\mathbf{a}\in\mathbb{R}^n$$\(Scaling\)
      * 장점: 많은 프로그래밍 언어들이 array연산을 지원
        * 주의: vector 연산과 해당 언어의 array 연산이 다를 수 있음
* 선형대수는 벡터들간의 유사성\(similarity\)에 집중함
* 선형대수에서의 대부분의 알고리즘은 $$\mathbb{R}^n$$안에서 표현되어 있음.
  * 우리가 주로 $$\mathbb{R}^n$$에 집중하는 이유
  * 즉, 유한 차원의 백터공간을 다룸 \(모든 벡터는$$\mathbb{R}^n$$안에서 1:1 대응관계\)
  * 필요할때는 기하벡터나 직관을 얻고, array기반 알고리즘을 고려할 것
* 선형대수에서 활용한 가장 중요한 개념
  * **벡터공간\(Vector space\)**
    * 어떤 벡터 집합의 두가지 연산\(Addition & Scaling\)에 대해서 닫혀있는\(closed\) 공간 
      * 어떤 벡터집합의 원소들끼리 더하거나 스케일링을 해서 얻을 수 있는 모든 벡터들의 집합
    * 머신러닝의 많은 부분의 기저를 이루고 있음 
* 이 챕터가 대부분 참고한 자료들 중 online으로 접근 가능한 것들 
  * [Pavel Grinfeld's series on linear algebra](http://tinyurl.com/nahclwm)
  * [Gilbert Strang's course on linear algebra](http://tinyurl.com/29p5q8j)
  * [3Blue1Brown series on linear algebra](https://tinyurl.com/h5g4kps)
    * \(editor\) 나도 많은 도움을 받았던 매우 잘 알려진 컨텐츠들이다
    * \(editor\) 텍스트북이 YouTube을 참조하는 시대가 왔다
* 이 챕터에서 배운 개념은 다음 후속 챕터들에서 사용됨
  * Chapter 3\(**Analytic Geometry**\): 벡터와 그 연산의 개념을 기하\(geometry\)의 아이디어로 확장
  * Chapter 5\(**Vector Calculus**\): 행렬 연산을 벡터 미적분에서 활용
  * Chapter 9\(**Linear Regression**\): least-squares 문제를 풀때 선형대수 활용
  * Chapter 10\(**Dimensionality Reduction**\): PCA를 하면서 projection 개념사용





