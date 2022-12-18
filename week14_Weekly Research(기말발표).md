### <2D 디지털 합성_14주차 Weekly Research>

[기말 발표 때 사용했던 누크과정 기록]

## 반짝이는 파티클 만들기
크리스마스 장식에 반짝거리는 효과를 넣으면 좋을것 같아 Particle 이펙트를 찾아보았다.
 
 <p align="center"><img src="https://user-images.githubusercontent.com/112764860/208290970-39240b31-582f-41c8-8b37-a85219d40e66.png" width="50%" height="50%"/></p>

<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208291011-bd69df3d-46f1-4791-9019-a010209c88f9.png" width="50%" height="50%"/></p>
 
- Color wheel 노드 불러온 뒤 - 백색으로 변경  
- card로 3D내에 파티클의 구역을 지정 , color wheel에 transform, crop을 적용해 작은 원으로 만든다.  
- ParticleEmitter 노드를 불러와 card와 colorWheel을 연결   
- ParticleDrag, ParticleTurbulence, ParticleWhind 노드를 연결해 빛의 양, 랜덤 seed, 속도, 방향 등을 조절   
- scanlineRender로 3D 공간 위 card에 불러와짐 
- glow 효과 적용 
- 화면 포맷에 맞게 reformat 
- card 노드로 sence에 다시 연결해 hallway 화면 안에 배치 (이렇게밖에 방법을 찾지 못해서 ..연결 하였다)



## 2.5 복도식 화면을 만든 뒤 그 안에 소스들을 배치 
- 안에서 밖으로 빠져나오면서 공간감을 내보려고 하였다.
- 200프레임을 뽑아야 해서 카메라 이동 속도를 비교적 느리게 진행 
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208291494-b9036d71-aac9-493d-9ae2-a98b06668f0a.png" width="50%" height="50%"/></p>

<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208291341-d2bd43de-b80e-4728-9b02-c412166551a7.png" width="50%" height="50%"/></p>


## 소스 프레임 설정 및 루프 기능 
- 작업을 하다보니 정해둔 원본 프레임에 맞춰 이미 프레임이 정해진 소스들을 배치할때, 소스의 프레임이 끝나지않고 반복되었으면 할 때가 있었는데 
소스파일의 프레임 설정을 이것저것 만져보니 해결되었다.
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208292204-e66e89a2-ff8d-45ab-af67-3ba55a13ddb4.png" width="50%" height="50%"/></p>

- Frame Range 에서 프레임의 설정을 loop 로 바꾸면 프레임이 끝나도 1부터 다시 시작하여 계속 진행된다.
(다만 처음과 끝의 연결이 자연스러운지 잘 보고 설정해야 한다) 

- Frame 에서 start at 으로 설정을 바꾸면 원본 프레임위에 이 소스파일이 언제 시작할 것인지 설정이 가능하다
- Frame 에서 offest 설정으로 바꾸면 나오는 프레임의 구간을 설정할 수 있다


## 4포인트 트래커를 사용해 노트북 화면 합성 
- 대비가 있는 픽셀사이에 트랙 포인트를 추출해도 초점이 나가는 부분에 트래킹이 빗나가는 경우가 있어 이 부분은 수동으로 설정하는 것이 좋은것 같다 
- 연두색 화면이 보이지 않도록 최대한 cornerpin 꼭짓점을 넓게 잡기 

<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208292560-278ba88b-4ad9-4bef-8c84-2d45e482eadf.png" width="50%" height="50%"/></p>

## 3D camera tracking 을 이용해 2D를 3D공간에 합성 

- camera traking을 추출한 뒤 바닥면을 표시해 소스파일들이 배치될 수 있도록 만든다 

-  노트북 뒤에 가려지는 부분은 로토를 이용해 가려지도록 만든다 


<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208293147-d4f5ea78-20db-453b-bff0-b38a53bf41d3.png" width="50%" height="50%"/></p>
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208293171-24e2bb7c-b8a5-42f6-bf14-edca45741791.png" width="50%" height="50%"/></p>

<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208293126-dc1f0263-8ba8-4344-b2d8-19c8ef1d4c5d.png" width="50%" height="50%"/></p>

## 그림자 만들기


- roto로 그림자를생성후 blur처리  
- 산타 ,트리의 그림자를 만들어 배치시킨다.  
- 그림자를 안 넣은 것보다는 좀 더 자연스럽게 보이게 한다  


<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208293072-b3bb123b-e328-48b4-b7d0-e89fc4bbdf1e.png" width="50%" height="50%"/></p>
