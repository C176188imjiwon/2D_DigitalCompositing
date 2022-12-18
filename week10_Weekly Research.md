### <2D 디지털 합성_10주차 Weekly Research>
## 카메라 트래킹

### [1 point tracker를 이용해 합성 및 rotopaint]
- 움직이는 영상 에서의 물체를 가려버리거나 추가할 때 사용   
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208246598-fe082c3c-60ef-4944-80ad-95d88f86f555.png" width="60%" height="60%"/></p>
- Tracker 노드를 추가한 뒤 Add track을 클릭하면 마커를 만들 수 있다   

#### [ 트래킹 마커를 찍는 기준] 
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208280500-b7dcae06-2739-4afd-b783-fcc08867fbe3.png" width="60%" height="60%"/></p>
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208280587-964ac642-ff11-4a04-8477-956d50702a0e.png" width="60%" height="60%"/></p>

- 주변과의 대비가 심한 곳의 픽셀 4개의 중간 사이에 트래킹 마커를 찍는 곳이 좋다   
  픽셀이 불분명한 부분에 트래커를 찍으면 제대로 추출이 안 될 수 있다. 

-  또한 빠르게 화면 전환이 될 경우를 대비해 가운데 영역이 바뀌지않도록 바깥 영역 표시를 늘려 추출 범위계산에 포함되도록 한다.   
   변화가 많이 생기는 쪽으로 길이를 늘리면 된다.

(ex- 가로로 움직임이 많다면 가로로 길이를 늘려주기)
  
- tracking이 시작되면 왼쪽 상단에 뜨는 화면을 통해 트래킹이 잘 따라가고있는지 확인할 것
  
- 에러수치를 확인하여 에러난 곳부터 트래킹을 시작해 오류를 수정할 수 있다. 
(무조건 에러가 난다고 사용못하는 것은 아니다. 쓸 수 있다고 생각되면 사용 가능) 

#### [ tracking export 유형 ]
### -  match move : 원본 플레이트 자체가 움직인다   
### -  stabilize: 원본 플레이트와 역방향으로 움직인다   

-->> 1point tracking의 경우 transform(match move)를 사용해 export 



#### [ baked 된 것과 아닌 것의 차이점 ] 
- baked 되지 않은 노드는 초록색 선이 연결되어 있다. tracker의 위치가 바뀌면 export 노드의 위치도 변화된다.  

- baked 된 것은 tracker에서 분리되어 자기의 키프레임을 가지게 된다. tracker의 값이 바뀌어도  처음 설정된 값에서 변하지 않는다  


#### [rotopaint 사용]
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208281001-f4203f11-753e-4c5e-9ded-6f8193349b00.png" width="60%" height="60%"/></p>
- rotopaint를 사용해 특정 지점을 복사 후 1point traker에 적용하여 다른 위치로 옮겨 
그 위에 덮을 수 있다

***
### [2 point tracking]

- 흔들림이 심한 영상을 덜 흔들려 보이도록 만들어 줄 수 있다.

- 두 개의 트래커를 선택해 average track를 눌러주면 두 트래커의 평균값을 잡을 수 있다.  

- 두 트래커를 추출한 다음 선택해 Transform (stabilize,baked)를 생성   

- 두 지점을 기반으로 회전을 역방향을 넣어서 바인드박스가 회전한다.  
(회전이 없는것처럼 보이게 만들어준다)

- 그위에 다른 카메라 트래킹들을 적용한 뒤 stabilize를 다시 얹어주면 원본 플레이트로 다시 돌아오게 된다.   

#### [ 설정할 때 유의점]
-  2point track 생성시 뚜렷한 대비가 보이는 픽셀 가운데에 위치시킬 것.  
   트래킹이 잘 따라갈수 있도록 넓은 영역을 충분히 잡아줄 것 
(ex- 물체의 그림자가 지는 모서리 사이 )




***
### [3 point tracking]

-3 개의 포인트부터는 면으로 계산하게 된다. 
- 움직이는 화면 내의 어떤 면에 다른 요소를 집어 넣을 수 있다.  
- 3point tracker는 rotation 과 scale 까지 변화한다. transform노드 사용. 
  match move 를 export 해 사용

(ex.거미줄 붙이기)



***
### [4 point tracking]
- 4 point를 사용하여 꼭짓점인 4개인 이미지를 화면 안에 갔다붙일 수 있다.  
꼭 사각형이 아니여도 된다. 4개의 꼭짓점이 움직이는 방향,크기,회전에 따라서 frame by frame으로 움직이게 할 수 있다.  

- export 노드에서 cornerpin2D 사용. 꼭 트래커가 정확히 4개여야 사용이 가능하다  
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208281554-dd184458-9587-4dd9-a71f-ab576e537afe.png" width="40%" height="40%"/></p>

- cornerpin2D 노드를 연결 후 form 창에서 'set to input'를 눌러 트래커의 위치에 합성할 이미지가 맞춰지도록 만든다 


- 4개의 트래커가 둥근 모서리에 위치해도 트래커가 생성된다.
***
### [3D camera tracker로 3d공간 만들기]

- track추출 전에 영상을 촬영한 카메라의 소스,렌즈 길이를 설정  
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208241512-ec58a070-89db-4731-ba46-010e788d02d2.png" width="60%" height="60%"/></p>
track 클릭-  frame by frame 으로 추적이 됨 
- 기본적으로2번 앞으로, 뒤로 트래킹이 진행된다.  

solve- 추출된 트래커가 사용가능한지 아닌지 계산하기   
초록색- 해결됨 / 주황색-  해결안됨 / 빨간색- 오류 

<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208241552-6b9a141c-7746-453f-9948-41923b7d631a.png" width="60%" height="60%"/></p>
- track 클릭-  frame by frame 으로 추적이 됨   
AutoTracks 창에서 사용할 트래커들을 조절 한 뒤 delete unsolved, delete rehected 

그 다음 update solve를 하면 사용할 초록색 트래커들만 남는다 


#### [ 사람 시점에서 보는 카메라 워크가 필요할 때]

- 추출된 3D camera traker에서 바닥면을 설정하면 된다   
(shift를 누른 채 초록색 마커들을 드래그 및 클릭-> 노란색으로 표시된다)

- 선택된 마커들을 우클릭-> ground plane -> set to selected (분홍색으로 표시된다)   

- scene을 생성하면 3d화면내에서 바닥면이 설정된 포인트들로 나타난다.  
위치,방향,색상을 추출해 가상으로 3D공간이 나타나게 된다 

<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208241568-dcf3a087-5539-467a-9588-4787d637207e.png" width="60%" height="60%"/></p>


- 그 위에 3D 오브젝트나 2d 이미지영상을 보다 더 자연스럽게 합성할 수 있게 된다  

  쓰리디영역을 다시 2D로 렌더링 할려면 scanlineRender를 이용한다
