### <2D 디지털 합성_11주차 Weekly Research>

## 10주차 피드백 

- camera tracking 3d 공간안에 오브젝트를 바닥면에 제대로 위치 시키도록 한다. 설정하다보면 바닥보다 아래에 위치 할 수도 있다.  

- 4point tracker를 설정 할 때 픽셀 중간에 위치시키도록 설정하는 것이 좋다. 그래야 제대로 트래킹이 잡힌다.  

- 오브젝트의 가장자리를 뿌옇게 처리해야할 경우, Blur 또는 Edgeblur 노드를 사용해 뿌옇게 만든다 ( 하는 법을 모른다면 직접 검색해보는 습관 더 갖기!)   

- premult 한 후에 색상 보정을 하면 원본 이미지에 왜곡이 생길 수 있으니 주의  

- 원본 영상이 흐릿할때는 sharpen 노드를 먼저 적용 후에 tracker를 적용하면 보다 더 선명하게 트래킹을 잡을 수 있다.   



## 4point- cornerpin2D tracking 

10주차에 배운 4 point trabking에서 cornerpin을 옮겨서 사용하는 방법 





## 2.5D tracking 
2.5D 카메라 트래킹
