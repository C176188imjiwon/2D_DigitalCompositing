### <2D 디지털 합성_10주차 Weekly Research>
## 카메라 트래킹

### [1 point traker를 이용해 합성 및 rotopaint]
- 움직이는 영상 에서의 물체를 가려버리거나 추가할 때 사용   
<p align="center"><img src="https://user-images.githubusercontent.com/112764860/208246598-fe082c3c-60ef-4944-80ad-95d88f86f555.png" width="60%" height="60%"/></p>
- Tracker 노드를 추가한 뒤 Add track을 클릭하면 마커를 만들 수 있다   


### [2 point tracking]

- 흔들림이 심한 영상을 덜 흔들려 보이도록 만들어 줄 수 있다.
- 
- 두 트래커를 추출한 다음 선택해 Transform (stabilize,baked)를 생성   

- 두 지점을 기반으로 회전을 역방향을 넣어서 바인드박스가 회전한다.  
(회전이 없는것처럼 보이게 만들어준다)

- 그위에 다른 카메라 트래킹들을 적용한 뒤 stabilize를 다시 얹어주면 원본 플레이트로 다시 돌아오게 된다.   


### [3 point tracking]

- 3개의 포인트로 계산하게 된다. 
-  움직이는 화면 내의 어떤 면에 다른 요소를 집어 넣을 수 있다. 3point tracker는 rotation 과 scale 까지 변화한다

### [4 point tracking]

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
그 위에 3D 오브젝트나 2d 이미지영상을 보다 더 자연스럽게 합성할 수 있게 된다

쓰리디영역을 다시 2D로 렌더링 할려면 scanlineRender를 이용한다
