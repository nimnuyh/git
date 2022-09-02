# **TIL Logistic Regression**

> 범주형 변수를 종속변수로 가지는 회귀분석

종속변수가 범주형이므로 정규분포를 따르지 않음<br>
따라서, 결정계수가 매우 낮고 F 검정, T-검정을 사용하여 유의성 검정을 하는데 문제가 있음

#### Logistic Function (Sigmoid Function)

$$ g(x) = \frac{e^x}{1 + e^x} $$ 

- 출력 결과가 항상 0 ~ 1 사이의 값

#### Odds Ratio

$$odds = \frac{P(A)}{1 - P(A)}$$

- 임의의 사건이 발생(성공)할 확률
- 0 ~ $\infty$ 의 범위를 가짐
- Odds Ratio의 해석
  - 연속형 변수 : 변수의 값이 1 증가할 때, 증가하는 종속변수의 크기
  - 범주형 변수 : 변수가 참일 때, 증가하는 종속변수의 크기

#### Logistic Model

$$ logit(p) = ln(\frac{p}{1-p}) = \alpha + \beta_0x_0 + \cdots + \beta_ix_i $$

$$ p = Pr(y = 1 | x) = \frac{e^\alpha+\beta x}{1 + e^{\alpha+\beta x}} $$

#### 혼동행렬 Confusion Matrix

![confusionmatrix](https://miro.medium.com/max/712/1*g5zpskPaxO8uSl0OWT4NTQ.png)

- 정확도 Accuracy <br>= $\frac{TP+TN}{TP+FP+TN+FN}$
- 민감도 Sensitivity <br>= $\frac{TP}{TP+FN}$
- 특이도 Specificity <br>=$\frac{TN}{FP+TN}$

**! Threshold에 따라 결과가 달라짐**

#### 정규화
> 일정 규칙에 따라 데이터를 변형하여 이용하기 쉽게 하는 것

변수를 예측하는데 도움이 되지 않는 변수들은 제거하여 로지스틱 회귀를 다시 구성하는게 일반적인 방법<br>
하지만, p-value를 이용하여 변수를 제거하는 방식은 최적의 회귀식을 도출해주는 방법은 아님<br>
따라서 정규화를 통해 변수 선택

- 최상의 부분집합 선택법
- 점진 단계적 선택법
- 후진 단계적 선택법
- Ridge 회귀 모형
- Lasso 회귀 모형