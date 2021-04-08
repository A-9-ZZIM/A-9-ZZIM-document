### 1. Filtering Method  
> 통계적인 측정 방법을 이용하여 피처들의 상관관계를 알아내고 적합한 피처만 선택하는 알고리즘
> - t-Test
> - Chi-square Test
> - Information Gain

### 2. Wrapper Method  
> 예측 모델을 사용하여 피처들의 부분 집합을 만들어 계속 테스트 하여 최적화된 피처들의 집합을 만드는 방법. 여러 모델을 생성하고 성능을 테스트하기 때문에 시간이 많이 필요하다. 
> - Forward Greedy
> - BackWard Greedy
> - Genetic Search
> - Local Search

### 3.Embedded Method
> Filtering과 Wrapper의 장점을 결합한 방법.
> - LASSO
> - RIDGE

---

Filter는 항상 최적의 Feature Selection을 보장할 수 없지만 Wrapper는 최적의 Feature Selection이 가능하다.
대신 Wrapper는 오래 걸린다.

결론 : Filter Method로 가자  

---

### T-test 조건
1. 표본이 독립적인가?
2. 수집된 데이터가 정규 분포를 따르는가?
3. 집단이 두 개 인가?

우리 데이터의 경우 일단 표본은 독립적 이지만 집단이 두 개가 아니다.  
Binary 값을 갖는 속성이 아니라면 분화를 시켜야하고, 분화 후 세그먼트의 개수가 대부분 두 개 이상일 것이다.  
이럴 경우 t-test 대신 **ANOVA**를 사용한다.

---

### 카이제곱검정이 가능한 조건
- 독립변수 : 범주형(2수준 이상) -> 분화 한 세그먼트  
- 종속변수 : 범주형(2수준) -> 당뇨 여부

---

### 데이터별 상관관계 비교 
1. 연속형-연속형  
> - Pearson Correlation : 두 자료가 정규 분포일 때
> - Kendall Correlation : 정규분포가 아니어도 됨
> - Spearman Correlation : Kendall 이랑 비슷한거 같음

2. 범주형-범주형
> - Phi Correlation : 비교대상 범주가 2개 ex) 남, 녀
> - Cramer's V : 비교대상 범주가 3개 ex) 연령대코드

3. 연속형-범주형
> - Point biserial Correlation : 두 변수중 하나는 범주형(Binary), 다른 하나는 연속형 변수일 때
> - Biserial Correlation : 두 변수중 하나는 인위적 범주형, 다른 하나는 연속형
> - Polyserial Correlation : 두 변수중 하나는 비인위적 범주형, 다른 하나는 연속형