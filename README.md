RandomForest를 이용해서 [Kaggle](https://www.kaggle.com/prathamtripathi/drug-classification)에서 다운받은 데이터로 분류를 진행하였습니다.

drug.csv 데이터에서 feature들이 숫자형태가 아니기 때문에 각 feature들을 원핫해주어서 차원을 늘려서 숫자로 표현해주었습니다.

3차원으로 늘렸다 함은 BP가 HIGH, NORMAL, LOW 가 있을 때 이거를 0,1,2로 하지 않고, HIGH를 [1,0,0], NORMAL을 [0,1,0], LOW를 [0,0,1]로 설정해주었습니다.

그렇게 진행한 분류 테스트 정확도는 98%가 나왔습니다.


그 후 데이터 feature를 3차원으로 늘리지 않고 그냥 HIGH를 2로 NORMAL을 1으로 LOW를 0으로 간단하게 1차원 형식을 유지하되 숫자로만 바꾸어 데이터를 drug_number.csv에 저장해주었습니다.

그 결과 같은 모델을 사용했지만 데이터 전처리 만으로 분류 테스트 정확도가 100%로 향상되었습니다.

RandomForestClassifier(n_estimators=180, max_features = 9,  max_depth = 100)에서 n_estimator는 크게 해주고, max_features는 실제 데이터의 feature 수로 설정해주었습니다.

랜덤 포레스트의 경우 의사결정트리의 오버피팅 문제를 해결하고자 여러 샘플에서 bagging을 통해 부분 집합을 형성하여 오버피팅을 방지합니다.

서로 다른 방향으로 오버피팅된 트리들을 평균내어서 치우치지 않고 좋은 성능을 내는 것으로 알려져 있습니다.
