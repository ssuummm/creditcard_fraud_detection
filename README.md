# Credit Card Fraud Detection
Kaggle: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

### I. EDA
1. **Class 분포 확인**: 정상거래(284315건), 사기거래(492건)으로 매우 불균형
2. **결측치 확인**: 결측치 존재하지 않음
3. **변수 유형 확인**  
    - 'V1'\~'V28': PCA된 변수 (연속형 변수)
    - 'Time', 'Amount' (연속형 변수)
    - 'Class': 반응변수 (범주형 변수)
4. **다중공선성 확인**: 큰 상관관계를 보이는 변수 없음
5. **각 변수 분포 확인**
      - 'Amount': 분포가 right-skewed 되어있음 -> log transformation 진행
      - 'Time'변수 -> 'Hour'변수를 추가하여 하루 24시간 기준으로 거래량을 살필 수 있도록 함
      - 'V1'\~'V28': 'V12', 'V14', 'V17' 변수는 정상 거래 분포와 사기 거래 분포가 확연히 다름

### II. Data Preprocessing
1. 'V12', 'V14', 'V17'의 **이상치 제거**
2. 'Amount', 'Time' 변수에 **Standard Scale** 적용
3. 'Class' 반응변수 불균형 해소 위해 **SMOTE** 시도

### III. Modeling
- validation set을 이용하여 최적의 hyperparameter를 찾아 tuning 진행  
- SMOTE는 유의미한 성능 향상을 가져오지 못해 진행하지 않음

1. **이상치 제거 X**
<img width="873" alt="이상치제거X" src="https://github.com/ssuummm/creditcard_fraud_detection/assets/139437305/9b165a48-0038-49c3-a477-dfc623ae6af4">
<br/>
<br/>

2. **이상치 제거 O** (f1 score값)
<img width="859" alt="이상치제거O" src="https://github.com/ssuummm/creditcard_fraud_detection/assets/139437305/e254a313-b61a-487f-9a05-95a1de23563a">

### 정리
- Boosting 기반 모형인 XGBoost, ADABoost, LightGBM이 좋은 성능 보여줌.  
- 이상치 제거 진행 시, 대부분의 경우 성능이 향상됨. 그러나, 이상치 또한 유의미한 정보이기 때문에 과도하게 제거하는 것은 큰 정보 손실을 가져다줄 수 있음.


