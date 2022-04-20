# Project in data mining class (2021 Spring) - Regression

## autompg data regression

### 분석 목표: 자동차의 특성을 나타내는 값들로 해당 자동차의 연비를 예측

#### data (autompg.csv)
- 자동차의 속성을 나타내는 변수(독립변수)로 구성 
  -  cylinders: 실린더 (4기통, 6기통, 8기통)
  -  displacement: 배기량
  -  horsepower: 마력
  -  weight: 자동차의 무게
  -  acceleration: 가속도
  -  model year: 자동차 출시 년도
  -  origin: 자동차 생산지 (1-미국, 2-유럽, 3-일본)
  -  car name: 자동차 이름
- 독립변수에 따른 종속변수: 연비(mpg)

#### process
1. 자동차 이름을 제거하고 분석 진행
2. 자동차 이름을 반영하여 분석 진행

- 사용 모델
  - Linear Regression
  - Regression Tree
  - Random Forest
  - Gradient Boosting

#### conclusion
- Gradient Boosting의 성능이 가장 우수 (특히, 변수가 많은 경우에 잘 작동함을 알 수 있음)
- 일반적인 상식대로 실린더가 작을수록, 마력이 작을수록, 무게가 낮을수록 연비가 높음을 알 수 있음
- 출시년도는 늦게 출시될 수록 연비가 높음
- RT에서는 무게 변수가 주요변수로 여겨지지 않았음
- 이후 대부분의 모델에서 중요도가 높은 변수가 비슷, 순서에 약간 차이가 있음
- Gradient Boosting에서 자동차 이름이 유의미한 경우 발견, 그러나 그 중요도가 아주 낮음

한계) 일반적인 결과가 도출되었음, 추후 무게 범위에 따라 나누어서 분석하는 것도 유의미할 것 같음
