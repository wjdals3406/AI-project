# 2D-3D Point matching & Panel Detection
2021.06 - 2021.11

## Project Goal
SKT���� ���� ���� �ǳ� �׺���̼� ���� �� Camera Pose Estimation ���������� �� back-end model�� ���� ��� �⿩�ϱ� ���� ������Ʈ

#### Stack
Python, Pytorch, Docker

#### WorkFlow

##### 1) 2D-3D Point matching
###### ������Ʈ ����
������ ���� �̹����� 2D Ư¡���� DB�� 3D Ư¡���� pair�� ����� ������ �˰��� ���� ������Ʈ

###### Data
- 2D Ư¡���� location�� descriptor
- 3D Ư¡���� location�� descriptor
=> 2D Ư¡���� 3D Ư¡���� match ������ ��ȯ

###### Model
- GNN ����� 2D-2D matching ���� SuperGlue ������ 2D-3D �𵨿� �°� ���Ӱ� ����
- 1) 3D Point ��ó�� ����
- 2) Keypoint Encoder ���� :  2D Ư¡���� (x, y)�� embedding�ϴ� encoder�� 3D Ư¡���� (x, y, z)�� embedding�ϴ� encoder�� ���� ���
- 3) Score Normalization ���� : (����) Sinkhorn Iteration -> (���� ��)Softmax 

###### Result
- filtering �������� ���� ����� �������ν�, filtering �ܰ��� ȿ���� ����
- �� ������ **���� KNN ��� 20~70%** ���
- ���� KNN�� ��� 2D Ư¡���� ���� matching�� ������� ��ȯ��. �׿� ���� �� ������ model�� matching�� ���� �ʴ� ������ �����ϱ� ������, outlier�� ������ �� �ִٴ� ū contribution�� ����
- ��� ����
- �� �淮ȭ ���� **���� ���񽺿� ���� ����**

##### 2) Panel Detection
###### ������Ʈ ����
����� �������� ����Ȯ�� �ĺ��� ������ ������ Ư¡�� matching�� ��Ȯ���� �����ϱ⿡, ������ ������ �ǽð����� ���� �� �����ϴ� ������Ʈ

###### Data
- Panel Dataset(512x512, 5884��)
- Synthetic Dataset(640x640, 23,536��)
    -> 2���� COCO data�� Ȱ��
    -> ��� �̹����� �ٸ� ������ �̹����� ������ ��, **����, ��ġ, ȸ���� ����**�ϰ� ����

###### Model
�簢�� ������ ���� �������� Ž���� �� �ֵ��� Pytorch�� Ȱ���Ͽ� YOLOv5 ��� ���� Point(������) Detection �� ����

###### Result
- inference time�� 50fps�� real-time�� ������ �� ����
- ����� 97% �޼�
- mAP@.5:.95 0.979 �޼�
- ��� ����
- SKT���� �����ϰ� �ִ� ����ö�� �����Ϳ� ���� ����� ������ Ȯ���Ͽ� **���� ���񽺿� ���� ����**

<img src="https://user-images.githubusercontent.com/77380514/223083252-98e79a8f-9b95-414b-9683-1a73783704d6.jpg" width="50%" height="300"></img><img src="https://user-images.githubusercontent.com/77380514/223083269-37b8a8fb-5cd5-4992-899a-719534fec957.jpg" width="50%" height="300"></img>
<img src="https://user-images.githubusercontent.com/77380514/223083276-b4168405-c43f-4f02-9a3f-c6db72cb7c33.jpg" width="50%" height="300"></img><img src="https://user-images.githubusercontent.com/77380514/223083306-3d96ea47-0a17-47a2-a239-6a087301a61a.jpg" width="50%" height="300"></img>