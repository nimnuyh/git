# **TIL Linear Regression**

### 선형 회귀
> X값을 이용하여 Y값을 예측하기 위해 선형방정식을 추론하는 통계분석

**단순 선형 회귀 Simple Linear Regression**<br>
: 독립변수 1개

$$ \hat{y} = \theta_0 + \theta_1*x $$

**다중 선형 회귀 Multiple Linear Regression**<br>
: 독립변수 2개 이상

$$ \hat{y} = \theta_0 + \theta_1*x_1 +  \theta_2*x_2 + \cdots + \theta_n*x_n $$

- 회귀분석 <br> : 변수와 변수 사이의 관계를 알아보기 위한 통계적 분석방법
- 독립변수 <br> : 종속변수에 영향을 미치는 변수
- 종속변수 <br> : 분석의 대상이 되는 변수
- 회귀계수 <br> : 회귀식의 절편과 기울기
- 잔차 <br> : 예측값과 실제값 사이의 차이
- 다중공선성 <br> : 독립변수 간 강한 상관관계로 인해 분석 결과를 신뢰할 수 없게 되는 현상
- p-value <br> : 독립변수와 종속변수의 선형 관계에 대한 유의확률 (0.05보다 작을 경우 유의미하다고 판단)

**비용함수 Cost Function**

~~목적함수 Objective Function, 손실함수 Loss Function~~

- 최적의 회귀계수를 찾기 위한 함수, 
- 평균 제곱 오차 Mean Squared Error MSE

$$ MSE = \frac1m * \displaystyle\sum_{i = 1}^{m}(y^i - h_\theta(x^i))^2 $$

**경사하강법 Gradient Descent**

- 비용함수의 최소값을 찾기 위한 최적화 알고리즘 Optimizer
- 0 < Learning Rate < 1