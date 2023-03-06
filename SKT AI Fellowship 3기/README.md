# 2D-3D Point matching & Panel Detection
2021.06 - 2021.11

## Project Goal
SKT에서 개발 중인 실내 네비게이션 서비스 내 Camera Pose Estimation 파이프라인 중 back-end model의 성능 향상에 기여하기 위한 프로젝트

## Stack
Python, Pytorch, Docker

## WorkFlow

### 1) 2D-3D Point matching
##### 프로젝트 개요
서버로 들어온 이미지의 2D 특징점과 DB내 3D 특징점의 pair를 만드는 딥러닝 알고리즘 개발 프로젝트

##### Data
- 2D 특징점의 location과 descriptor
- 3D 특징점의 location과 descriptor
=> 2D 특징점과 3D 특징점의 match 정보를 반환

##### Model
- GNN 기반의 2D-2D matching 모델인 SuperGlue 구조를 2D-3D 모델에 맞게 새롭게 변형
- 1) 3D Point 전처리 실행
- 2) Keypoint Encoder 수정 :  2D 특징점의 (x, y)를 embedding하는 encoder와 3D 특징점의 (x, y, z)를 embedding하는 encoder를 각각 사용
- 3) Score Normalization 수정 : (기존) Sinkhorn Iteration -> (변경 후)Softmax 

##### Result
- filtering 적용으로 성능 향상을 보임으로써, filtering 단계의 효과를 입증
- 모델 성능을 **기존 KNN 대비 20~70%** 향상
- 기존 KNN는 모든 2D 특징점에 대해 matching된 결과만을 반환함. 그에 비해 본 연구의 model은 matching이 되지 않는 경우까지 예측하기 때문에, outlier을 제거할 수 있다는 큰 contribution을 가짐
- 대상 수여
- 모델 경량화 이후 **실제 서비스에 적용 예정**

<br/>
<br/>

### 2) Panel Detection
##### 프로젝트 개요
비슷한 광고판이 부정확한 후보군 추출을 일으켜 특징점 matching의 정확도를 저하하기에, 광고판 영역을 실시간으로 검출 및 제거하는 프로젝트

##### Data
- Panel Dataset(512x512, 5884장)
- Synthetic Dataset(640x640, 23,536장)
    -> 2개의 COCO data를 활용
    -> 배경 이미지에 다른 한장의 이미지를 삽입할 때, **시점, 위치, 회전을 랜덤**하게 적용

##### Model
사각형 형태의 간판 영역만을 탐지할 수 있도록 Pytorch를 활용하여 YOLOv5 기반 간판 Point(꼭짓점) Detection 모델 개발

##### Result
- inference time이 50fps로 real-time이 가능한 모델 개발
- 검출률 97% 달성
- mAP@.5:.95 0.979 달성
- 대상 수여
- SKT에서 보유하고 있는 지하철역 데이터에 대해 우수한 성능을 확인하여 **실제 서비스에 적용 예정**

<img src="https://user-images.githubusercontent.com/77380514/223083252-98e79a8f-9b95-414b-9683-1a73783704d6.jpg" width="50%" height="300"></img><img src="https://user-images.githubusercontent.com/77380514/223083269-37b8a8fb-5cd5-4992-899a-719534fec957.jpg" width="50%" height="300"></img>
<img src="https://user-images.githubusercontent.com/77380514/223083276-b4168405-c43f-4f02-9a3f-c6db72cb7c33.jpg" width="50%" height="300"></img><img src="https://user-images.githubusercontent.com/77380514/223083306-3d96ea47-0a17-47a2-a239-6a087301a61a.jpg" width="50%" height="300"></img>
