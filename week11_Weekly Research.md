### <2D 디지털 합성_11주차 Weekly Research>

## 10주차 피드백 

- camera tracking 3d 공간안에 오브젝트를 바닥면에 제대로 위치 시키도록 한다. 설정하다보면 바닥보다 아래에 위치 할 수도 있다.  

- 4point tracker를 설정 할 때 픽셀 중간에 위치시키도록 설정하는 것이 좋다. 그래야 제대로 트래킹이 잡힌다.  

- 오브젝트의 가장자리를 뿌옇게 처리해야할 경우, Blur 또는 Edgeblur 노드를 사용해 뿌옇게 만든다 ( 하는 법을 모른다면 직접 검색해보는 습관 더 갖기!)   

- premult 한 후에 색상 보정을 하면 원본 이미지에 왜곡이 생길 수 있으니 주의  

- 원본 영상이 흐릿할때는 sharpen 노드를 먼저 적용 후에 tracker를 적용하면 보다 더 선명하게 트래킹을 잡을 수 있다.   



## 4point- cornerpin2D tracking 

### [10주차에 배운 4 point tracking에서 cornerpin을 옮겨서 사용하는 방법]

우선 사용하고싶은 영상/이미지를 4point tracker를 이용해 화면에 붙일려면 
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208282194-576760ed-8b43-4c01-8a99-058ed1d5a669.png" width="40%" height="40%"/></p>

Form 창에서 set to input를 눌러 아래와 같이 맞출 수 있다 

<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208282084-c14bf560-373c-4216-b0bc-3a2aa953f312.png" width="60%" height="60%"/></p>

- 그러나 카메라 트래킹 마커가 표시된 화면을 사용하다보면 합성을 하고싶은 가장자리까지 합성이 되지 않는 경우가 생긴다   

<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208282384-f611875f-862b-4462-a333-1d1ad1637f6b.png" width="70%" height="70%"/></p>

- cornpin2d 노드를 하나 더 생성 한 뒤 연결, form 창에서 ' set to input ' 클릭 후 cornerpin 창에서 Copy form 클릭  
 
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208282436-e3918d9a-ef48-4f03-aaef-c3d724eb949b.png" width="60%" height="60%"/></p>

- 영상/이미지 가장자리에 꼭짓점이 생기면서 이동 시킬 수 있게 된다. 화면에 맞춰 가장자리를 맞춰주면 된다.

- 손가락만 딴 roto를 merge로 합성 or 합성하는 이미지에 손가락 이동에 따라  
  roto 따기로  원본 영상과 합성하는 이미지를 겹치게 합성할 수 있다. 

## 2.5D 합성 
- 2D 이미지가 3D화가 되어서 공간감이 나도록 만드는 합성 

- 좋아하는 2.5D 합성 찾아보기 


### [ 매트 페인팅을 이용한 2.5D 합성 ]

- photoshop에서 매트 페인팅한 psd 파일을 누크로 불러오면 레이어별로 불러올 수 있다.  
  'breakout layers'로 psd파일 순서 그대로 불러오기가 가능

- 레이어가 분리된 파일을 누크로 가져온다면 레이어 간 각각의 색보정이 손쉽게 가능하다. 

  레이어 사이에 날아다니는 물체를 넣을 수 있다.  

#### [ 포토샵과 누크의 차이점] 

- 포토샵은 알파를 투명으로 보고 누크는 채널의 데이터로 본다.  


.
#### [card 생성]

- 레이어 사이로 카메라가 들어갈 수 있도록 card라는 plane object를 만들어 레이어간 간격을 만들어 준다.   


- shuffle 노드 : 기본으로 rbga로 되어 있는 레이어이미지를 shuffle기능을 사용하여
premult를 해주면 알파가 투명화된 card 파일로 만들어진다 

- 레이어 별로 shuffle로 카드 오브젝트로 변환시켜 배치한다.
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208284984-30ff6faf-3ddb-415a-88b8-a7975b024b32.png" width="60%" height="60%"/></p>


#### [누크에서 자주사용하는 log expression]
- 노드 별 라벨이 일일히 이름을 입력하기 귀찮을 때, label 칸에 {value int} 를 입력 
  -> 그러면 psd파일에 들어있는 레이어 이름으로 자동 라벨링이 된다. 

#### [카메라 구성] 
- 멀리 보내는 레이어 들은 크기들을 조절해 배치한다 
- 카메라에 키프레임을 줘서 화면안으로 공간을 들어가도록 한다. 화면 안으로 들어갈 수록 깊이감이 잘 느껴지게 된다 

### [ZDefocus]
- ZDefocus 노드는 point를 이용해 깊이감을 낸 화면에 포커스블러를 자동으로 생성시켜준다 점에 멀어질수록 블러처리가 된다. 
- 카메라로 직접 많이 찍어보면서 포커스의 감을 익히는 것이 좋다.
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208285474-61905785-c732-4340-ab81-45d8bc41a330.png" width="60%" height="60%"/></p>

***
### [ 평면 이미지 하나를 이용한 2.5D 합성 ]
2.5D 카메라 트래킹



