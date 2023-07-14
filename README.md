# 데이콘 도서 추천 알고리즘 AI경진대회
Dacon: https://dacon.io/competitions/official/236093/overview/description 

#### PB LB 전체 2위/ 최종 전체 1위
PUBLIC LB 3.25811 
PRIVATE LB: 3.27139 

CatBoostRegressor + Optuna 

* 핵심: 데이터 전처리와 catboost Pool에 명목, 범주형 변수들을 cat_features에 넣는 것, optuna로 best 파라미터 찾기 
* 다양한 변수를 추가(ex. 토픽, 언어구분, 출판연도 구분, 레이팅 카운트 등)해서 나온 결과보다 기본적인 변수들의 전처리가 더 도움이 되었습니다.
* 사람마다 점수 주는 기준이 천차만별이라 User-ID가 점수 예측에 가장 핵심이었습니다.
* 0점으로 처리된 점수가 많아, 0이 아닌 점수를 예측하는 것이 key 중 하나일 것 같습니다.
* fold 수를 5 > 10 > 20으로 늘려가며 확인해본 결과 20일 때 가장 좋은 성과를 보였습니다.
* 최종 예측점수는 각 fold의 예측값을 더하고 fold수로 나눴으며, np.clip으로 점수가 0보다 작거나 10보다 크면 0과 10으로 변환하게 만들었습니다.
