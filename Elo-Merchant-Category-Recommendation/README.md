## Elo Merchant Category Recommendation
- [대회 링크](https://www.kaggle.com/c/elo-merchant-category-recommendation)

### Overview
- 새로운 지역에서 개인 취향에 따라 레스토랑을 추천받음
- 브라질의 최대 결제 브랜드 중 하나인 Elo
	- 카드 회원에 대한 프로모션 또는 할인 제공
	- 소비자/판매자에게 모두 효과가 있는지?
	- 고객은 이런 경험을 즐기는지?
	- 상인들은 반복적으로 보는지?
	- 개인화!!!
- 개인이나 프로필을 위해 맞춤 설정된 것은 Elo에서 과거에 만든적이 없음 => 캐글에서 진행
- 고객 충성도 측정(loyalty score)

### Evaluation
- RMSE
- card_id별 loyalty score 예측

### 일정
- 2019.2.19까지 대회 참가 및 팀 합병
- 2019.2.19까지 외부 데이터 공개 기한
- 2019.2.26 최종 제출 마감

### Data
```
- train.csv 
- test.csv 
- sample_submission.csv : 예측해야 하는 모든 card_ids 있음
- historical_transactions.csv : 각 card_id에 대한 최대 3개월분의 거래 기록
- merchants.csv : 모든 상인에 대한 추가적인 정보
- new_merchant_transactions.csv : merchant_ids에서 만든 card_id가 모두 포함된 2개월 분량 데이터(historical data에 없는)
```


## 캐글 일지
### 2018-12-09 
```
- 대회 및 데이터 이해
- 커널 보면서 EDA
```

### 2019-01-01 
```
- lightgbm을 사용해 기본 모델링
- score : 3.879
```

### 2019-01-06
```
- 03.Feature-Engineering
- lightgbm을 사용
- Feature 추가
- Sharing of my experinece 읽음 : https://www.kaggle.com/c/elo-merchant-category-recommendation/discussion/75935 
- Score : 3.706
```

### 2019-01-07
```
- 04.Feature-Engineering-2nd
- Feature 추가
- Less is More 커널 읽음 : https://www.kaggle.com/c/elo-merchant-category-recommendation/discussion/73937
- Score : 3.699
```

### 2019-01-13
```
- Stacking 커널 읽음 : MultiModel + RIDGE + STACKING : https://www.kaggle.com/ashishpatel26/rmse-3-66-multimodel-ridge-stacking
- Outlier 제외한 데이터 학습 + Outlier만 따로 학습해서 Concat
- Score : 3.692
```

### 2019-01-14
```
- Outlier 더 잘 학습하기 위한 방법 고민 중
- submission 제일 잘 된 것 2개를 mix해서 제출 (0.6 * submission1 + 0.4 * submission)
- Score : 3.691
- ToDo : StackNet 구현할까.. 조금만 수정해서? => 지금 상황에선 굳이..란 생각도 들긴 함
```
### 2019-01-28
```
- Stacking 결과 실패 => 더 안좋아짐
- 어떻게 개선해야 할까..음... 커널을 보니 후처리를 많이 하는 느낌
```

### 2019-02-11
```
- 그동안 계속 했는데, 일지를 작성하지 않음
- 기존 커널을 사용 => Single Model
- Outlier 예측 모델 => 높은 확률로 나오는 값을 -33으로 설정(포스트세싱)
- 3.678
- 다시 Single Model을 개선해야할 필요가 있을듯.. 
```

### 2019-02-12
```
- Outlier 예측 모델을 조금 더 디벨롭
- 3.670
```

### 2019-02-26
```
- 그동안 진행해서 제일 높았던 점수 : 3.664와 아웃라이어 예측을 조금 보수적으로 한 모델 제출!
- 현재 53등인데 과연 몇등까지 될 것인지 궁금..
```

### 2019-02-27
```
- Public Board 53등 -> Private Board 2690등ㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋ
- 여러분 주의하세요~! :)
- 결과를 돌이켜 보니 최고 좋은 커널은 은메달~동메달권;;
- 큰 Shaking의 원인 : Public에 너무 심취함
```
