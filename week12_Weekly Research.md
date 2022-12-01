### <2D 디지털 합성_12주차 Weekly Research>

## 3D compositing in film
가상의 3D 모델링, 렌더링 이미지를 영화 또는 애니메이션과 같은 움직이는 영상에 자연스럽게 합성하는 방식이다.   
주로 VFX기술이 많이 들어간 히어로물, SF, 판타지 실사영화에 필수적으로 사용되며, 2D 및 3D 애니메이션에도 예외없이 3D 합성 기술이 요구된다.
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/205136516-79556022-c548-4d86-b98e-af8162317eeb.png" width="70%" height="70%"/></p>
 <p align="center"><사진 1> '왕자의 게임' 中 VFX 합성과정 (출처:Foundry Korea)   </p> 
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/205139787-331afd6a-d0b8-47f9-bd26-a4e19c669732.png" width="70%" height="70%"/></p>
 <p align="center"><사진 2> '클라우스' 2d 캐릭터와 3D 모델링 배경 합성과정 (출처:insider)   </p> 

- 이미지나 영상과 다르게 3D 모델링 같은 경우는  렌더링 할 때 텍스쳐,알파 채널 등 들이 따로 분리가 가능하다.
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/205132057-19be3305-ef76-4e34-b616-cf75a98119c0.png" width="60%" height="60%"/></p>


- Maya- Render Setting - AOVs 에서 필요한 채널들을 선택해 추출 가능하다.
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/205132447-1dce4a9e-b14d-4cd9-8657-773e81ef00d1.png" width="60%" height="60%"/></p>

- 최근에는 'crytomatte'기능을 주로 사용하는데, 렌더링 시 특수 데이터를 저장하여 멀티 채널 이미지를 생성할 수 있다.
렌더러와 누크에 기본으로 crytomatte가 들어있으며, 장점은 마스크처리로 알파 채널 지정이 손쉽다는 것이다. 이렇게 여러 개의 채널로 분리가 되면 후보정 시 자유도가 높아진다.


---

## 노드 연결 시 유의할 점 
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/205143408-2521f386-53bf-49d3-ae18-81f84c7ff338.png" width="70%" height="70%"/></p>
 <p align="center"> premult 후 color grade (상) 와 color grade 후 premult (하) </p> 
 
- ## premult 하기 전에 color grade를 해야 한다.
여러 레이어를 겹치다 보면 가장자리에 깨지는 부분이 생길 수 있다. 합성을 더 자연스럽게 하기 위해 순서를 지키는 것이 좋다
