# **TIL Regularized Linear Models**

## 정규화 선형회귀

: 선형회귀의 과적합을 방지하기 위해 회귀계수에 패널티를 부여하여 모델의 복잡도를 낮추고, 일반화 성능을 높이는 방법

### 릿지회귀 Ridge Regression

> $l_2$ penalty

$$ MSE(\theta) + \alpha * \frac12 * \displaystyle\sum_{i=1}^{n}\theta_i^2 $$

- $\alpha$ : Reguralization Parameter
    - Parameter가 가능한 작아지도록 penalty 부여
    - $\alpha$ = 0 : 일반 linear regression과 동일
    - 여러 개의 $\alpha$ 값에 대해 Cross Validation
<br>
<br>
- 비용함수에 $l_2$ norm 적용
- 가중치의 제곱의 합을 최소화
- 가중치가 0에 가까워지면 가까워질수록 업데이트가 작아짐

### 라쏘회귀 Lasso Regression

> $l_1$ penalty

$$ MSE(\theta) + \alpha * \frac12 * \displaystyle\sum_{i=1}^{n}|\theta_i| $$

- 비용함수에 $l_1$ norm 적용
- 가중치의 절대값의 합을 최소화
- 가중치가 0이 될 때까지 기울기가 상수이기 때문에 특정 변수들의 가중치는 0이 됨
- 변수 선택 효과

### 엘라스틱넷 Elastic Net

> Ridge와 Lasso의 중간

$$ MSE(\theta) + r * \alpha * \frac12 * \displaystyle\sum_{i=1}^{n}|\theta_i| + \alpha * \frac{1-r}2 * \displaystyle\sum_{i=1}^{n}\theta_i^2 $$

- $r$ : $l_1$ penalty의 비율
  - $r = 0$ : Ridge
  - $r = 0$ : Lasso