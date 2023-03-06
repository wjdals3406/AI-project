# AI야,진짜 뉴스를 찾아줘!

#### 대회 개요
광고성 내용의 가짜 뉴스 이진 분류 AI 대회

#### Stack
Python, TensorFlow

#### WorkFlow
- 뉴스의 제목, 본문 내용이 담긴 텍스트 데이터, 기사 내 순서와 날짜 등이 담긴 정형 데이터 활용
- 정형 변수는 정확도 향상에 기여하는 것을 확인하며 총 3가지 종류의 변수 생성(텍스트 관련한 변수, 문법적 특징을 고려한 변수, 정형 데이터 column 변수를 이용한 변수)
- 텍스트의 길이, 뉴스의 제목과 내용 간의 유사도, Mecab tagset을 활용한 형태소 feature 등(수사,특수기호 등의 문법적 특징을 활용) 파생 변수로 13개 생성
- ‘대박’, ‘따상주’ 등 가짜 뉴스의 핵심 단어를 발견하여, 단어를 임베딩한 LSTM과 ‘따상주’ 및 신조어에 강한 Character CNN 사용
- **Character CNN, LSTM과 파생 변수**를 활용한 **새로운 Multimodal 자체 개발**

### Result
- **정확도** **98.74%, inference time 0.119ms** 달성
- **AI부문 192팀 중** **1위**

<img src="https://user-images.githubusercontent.com/77380514/223071573-9fa10730-15f3-4098-8b59-d38860452b63.jpg"></img><img src="https://user-images.githubusercontent.com/77380514/223071746-1e747196-9fc9-44d7-b4de-8cce0fa46b97.jpg"></img>
<img src="https://user-images.githubusercontent.com/77380514/223071764-7f132e06-df98-4310-a03c-89c5be6b95e5.jpg" width="50%"></img><img src="https://user-images.githubusercontent.com/77380514/223071771-8eae1288-f73a-4fd8-8721-8bd0929bc49c.jpg" width="50%"></img>
