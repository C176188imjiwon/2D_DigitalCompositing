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

<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208282384-f611875f-862b-4462-a333-1d1ad1637f6b.png" width="60%" height="60%"/></p>

- cornpin2d 노드를 하나 더 생성 한 뒤 연결, form 창에서 ' set to input ' 클릭 후 cornerpin 창에서 Copy form 클릭  
 
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208282436-e3918d9a-ef48-4f03-aaef-c3d724eb949b.png" width="60%" height="60%"/></p>

- 영상/이미지 가장자리에 꼭짓점이 생기면서 이동 시킬 수 있게 된다. 화면에 맞춰 가장자리를 맞춰주면 된다.

- 손가락만 딴 roto를 merge로 합성 or 합성하는 이미지에 손가락 이동에 따라  
  roto 따기로  원본 영상과 합성하는 이미지를 겹치게 합성할 수 있다. 

## 2.5D 합성 
- 2D 이미지가 3D화 되어서 공간감이 낼 수 있도록 만드는 합성 

- 좋아하는 2.5D 합성 찾아보기 


#### [ 매트 페인팅을 이용한 2.5D 합성 ]


#### [ 평면 이미지 하나를 이용한 2.5D 합성 ]
2.5D 카메라 트래킹
