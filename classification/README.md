# Project in data mining class (2021 Spring) - Classification

## Ionosphere data classification
* Ionosphere: 전리층 (전파를 지구에서 보낼 때 전리층에 의해 반사되어 한 지역에서 다른 지역까지의 통신이 가능해 짐)

### 분석 목표: 전파를 보냈을 때 그 전파들이 반사되어 각 관측소를 통해 다시 측정되는지 그렇지 않은지를 분류

#### data (ionosphere.csv)
- Goose Bay system의 고주파 안테나로부터 수신된 신호
- 수신된 신호를 시간과 빈도를 인수로 하는 자기상관함수를 이용하여 처리
- 17개의 pulse number, 각각 2개의 attribute로 구성됨 → 총 34개의 attribute(독립변수) 
  - attribute의 값들은 전자기신호를 입력 받는 함수가 반환한 값
- target(종속변수): 0과 1로 표시
  - 0이면 “good” radar return → 전리층 내부 구조의 형태를 설명할 수 있는 전파 반사
  - 1이면 “bad” radar return → 전리층을 뚫고 지나간 신호

#### process
- 상관관계 매트릭스를 통해 확인해 본 결과 홀수 번째는 홀수 번째끼리, 짝수 번째는 짝수 번째끼리 높은 상관관계를 띔
- 4가지로 나누어서 분석 실시
  ① 전체 변수 사용 
  ② 관측소 평균 값 사용 (홀수 번째와 짝수 번째의 평균)
  ③ 함수1 반환 값만 사용 (홀수 번째)
  ④ 함수2 반환 값만 사용 (짝수 번째)
- 사용 모델
  - Logistic Regression
  - Decision Tree (30번 반복 시행, train:test = 8:2, Gini 지수 사용, 트리 깊이 = 4)
  - Random Forest (train:test = 8:2, Gini 지수 사용, 트리 깊이 = 4)
  - Gradient Boosting
  - KNN

#### conclusion
- Gradient Boosting의 성능이 가장 우수 (특히, 분석④에서 두드러진 향상을 보임)
- 대부분의 모델에서 중요도가 높은 변수가 비슷하며, 함수1 반환 값이 함수2 반환 값보다 더 중요하게 여겨짐
- 결과를 통해 16개의 관측소 중 중요한 관측소 파악 가능 → 관측소1, 관측소2, 관측소3, 관측소13, 관측소16

한계) 각 관측소 별 분류를 하는 데 있어 유의미한 기준 값이 있기는 하지만 물리적인 배경지식 없이는 그 값의 의미를 파악하기 어려움

