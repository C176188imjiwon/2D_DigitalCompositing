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
