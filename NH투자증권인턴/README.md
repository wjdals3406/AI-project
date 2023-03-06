# 해외주식 리포트 키워드 추출 태깅 모델 개발
2021.08 - 2021.08

#### About Project
주식 어플에 주식 종목을 입력하면 관련 키워드가 나오는 서비스 탑재를 위해, 수작업으로 키워드를 추출하고 있던 것을 자동화하는 업무

#### Stack
Python

#### WorkFlow
- 티커(Ticker) 입력 시 해당 종목의 키워드 추출 자동화 및 시각화 진행
- 불용어 제거 후 Mecab 형태소 분석기로 명사 추출
- Counter와 TF-IDF에 대해 빈도수가 높은 단어를 키워드로 선정
- 다수의 단어로 키워드가 분리되어 나오는 문제를 사용자 사전 추가, N-gram(n≤3)을 적용하여 해결

### Result
- 키워드 추출 시간 약 120초에서 약 0.1초로 실행 속도 단축
- 현직자분들의 좋은 평가를 받아, 해당 모델은 실제 현업에서 개발을 구체화 중

<img src="https://user-images.githubusercontent.com/77380514/223089939-3c32494f-8c90-4fd3-a50e-4b2485b2e1ce.jpg" width="50%" height="300"></img><img src="https://user-images.githubusercontent.com/77380514/223089961-9a72f774-133d-49d7-b66b-97f6d54f757d.jpg" width="50%" height="300"></img>
