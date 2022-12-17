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


## [3D이미지에 Sharpen 효과를 입힐 때: slog3 ]
* linear 상태의 3D 이미지를 log2Lin1 노드로 log 이미지로 만들어 중간톤 상태로 만든다음,  
sharpen 노드를 적용한다. 그다음 다시 log를 linear로 바꿔준다.
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208229596-be365439-80e6-44b4-876c-656a9db6050d.png" width="60%" height="60%"/></p>
 <p align="center"><그림 3> slog3과의 차이점 (출처:GeorgeKhelashvili) </p>   

 <p align="center"><img src="https://user-images.githubusercontent.com/112764860/208229751-a5bcf8c4-cf9e-4955-b557-00c6f3506d6b.png" width="40%" height="40%"/></p

  log노드로 바꾸고 sharpen를 적용해야 색보정을 할 때 이미지가 열화 될 경우가 적어지고 선명하게 잘 들어간다.
  
  * Shuffle 노드  
: rbga 채널이 있어서 연결을 통해 색을 바꿀수도 있고, 투명하게 만들 수도 있다   


#### [노드 프리셋 만들기]
프리셋으로 등록하고 싶은 노드 묶음 전체 선택 후 랜지 아이콘 클릭- create 클릭 후 이름정해서 등록하기  
  이렇게 등록을 하면 컴퓨터내에서도 파일이 생성된다. 다른 컴퓨터로 이동을 해야할때 사용하면 유용
  
## [쓰리디 렌더링을 불러오면 얻을 수 있는 이점들]

- 시간이 없는 상황에서 3D 화면에 추가 2D 합성을 해야하는 경우, 누크에서 3D를 불러올 수 있다면 위치를 찾은 다음 합성이 가능하다 (ex- 3D오브젝트에 표시판 붙이기)   


- UV 패스를 안다면 UV 영역에 맞게 텍스쳐를 추가해 애니메이션을 넣을 수도 있다.(ex-쓰리디 모델링 위 슬라임 애니메이션 연출)    

- depth 맵 -  카메라 렌즈 효과를 줄 때, 포커스 블러 정도 조절도 가능    

- 모양 있는 보케 생성도 가능   

- 빠르게 후보정을 하는 데에 유용
  
 ## PostionToPoints 노드  


  <p align="center"><img src="https://user-images.githubusercontent.com/112764860/208231153-4f22727c-1ae9-4e6d-9355-0934dc2bb2ba.png" width="60%" height="60%"/></p>
  
- 2D이미지의 픽셀정보를 3D 포인트 클라우드로 만들 수 있다.(3D카메라 트래킹 추출과도 비슷하다)  
- 기본 rgb, positon패스, normal world 인풋 3개 필요   
- 정확한 3D공간에 넣어야 할 때, 그위에 3D오브젝트를 추가해야할때 유용   
- 렌더링할때 뒷면의 정보는 없기 때문에 앞면의 형태만 생성이 된다 
  

