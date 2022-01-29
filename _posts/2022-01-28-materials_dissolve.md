---
layout: single

title: "Dissolve"

categories:
- "Materials"

tags:
- [UnrealEngine, Materials, Dissolve]

toc: true
toc_sticky: true

date: 2022-01-27
last_modified_at: 2022-01-27
---  
  
Result
---  
![gif](/Images/Material&Texture/M_Dissolve_gif.gif){: .align-center}{: width="70%", height="70%"}
  
---  
  
### 기본 셋팅
  * Dissolve되는 부분의 반투명 느낌을 위해 Translucent를 해준다.
  * Translucency에서 Lighting Mode를 Surface TranslucencyVolume으로 바꿔줘야 검은색 부분에 Metallic, Specular 그리고 Roughness를 줄 수 있다.
  
![1](/Images/Material&Texture/M_Dissolve1.png){: .align-center}
![2](/Images/Material&Texture/M_Dissolve2.png){: .align-center}  
  
---  
  
### UV생성
  * BoundingBoxBased Function를 추가 한다.
  * 그리고 Mask를 해줌으로 어느 방향으로 Dissolve를 할지 정한다.
    
![3](/Images/Material&Texture/M_Dissolve3.png){: .align-center}
![3](/Images/Material&Texture/M_Dissolve4.png){: .align-center}  

- RGB에 따라 방향이 달라진다.(방향: 검은색 -> 흰색)
  * B Mask시 (턱->머리)
![3](/Images/Material&Texture/M_Dissolve5.png){: .align-center}  
    
  * G Mask시 (뒷통수 -> 앞)
![3](/Images/Material&Texture/M_Dissolve6.png){: .align-center}  
    
  * R Mask시 (우측 귀 -> 좌측)
![3](/Images/Material&Texture/M_Dissolve7.png){: .align-center}  
      
---  
  
### Core 라인
  * 3ColorBlend를 추가한다.
![3](/Images/Material&Texture/M_Dissolve8.png){: .align-center}  
    
  * Mask와 3ColorBlend사이에 CheapContrast를 추가하고 Parameter를 Constrast에 연결한다.
  * Parameter를 thickness_core로 하고 값을 수정하여 core 라인의 크기를 조절 할 수 있다.
    ![3](/Images/Material&Texture/M_Dissolve9.png){: .align-center}  
    
  * thickness_core를 1에서 10으로 수정 후 모습. 중간 core 라인이 줄어든 것을 볼 수 있다.
  ![10](/Images/Material&Texture/M_Dissolve10.png){: .align-center}
      
  * core라인에 noise를 추가해 직선이었던 core라인에 새로운 라인을 넣어준다.  
    Multiply로 noise 값을 수정해 원하는 모양으로 변경가능.
    ![11](/Images/Material&Texture/M_Dissolve11.png){: .align-center}  
    
  * 여기서 필요한 라인은 Green라인으로, Green라인만 value를 1로 주면서 White로 바꿔준다.
    ![12](/Images/Material&Texture/M_Dissolve12.png){: .align-center}  
    
  * core라인의 색상만 원하는 색상으로 바꿔주기 위해 3Vector를 Multiply해준다.  
    V값 변경으로 밝기를 조절해주면 된다.
    ![13](/Images/Material&Texture/M_Dissolve13.png){: .align-center}  
    
  * core라인을 움직이게 하기 위해서는 Mask와 CheapContrast사이에 Subtract를 추가해  
offset값으로 조절하면 core라인을 움직이게 할 수 있다.
    ![14](/Images/Material&Texture/M_Dissolve14.png){: .align-center}  
    
  * 노드는 최종적으로 Emissive Color로 간다. 결과는
    ![gif2](/Images/Material&Texture/M_Dissolve_gif2.gif){: .align-center}  
    
---  
  
### Dissolve 파트 만들기  
  * Dissolve 파트를 만들기위해 3ColorBlend를 하나더 추가한다.  
여기서 Red라인을 Dissolve를 할 것이다.
    ![15](/Images/Material&Texture/M_Dissolve15.png){: .align-center}  
    
  * Green과 Blue채널에는 Dissolve가 들어가지 않기에 값에 1을 넣어준다.
  * Red값에 Parameter(opacity_of_dissolve)를 만들어 1보자 작은 값을 주고 조절하여 Dissolve의 세기를 조절할 수 있다.
    ![16](/Images/Material&Texture/M_Dissolve16.png){: .align-center}  
    
  * 노드는 최종적으로 Opacity로 간다. 결과는
    ![gif3](/Images/Material&Texture/M_Dissolve_gif3.gif){: .align-center}
