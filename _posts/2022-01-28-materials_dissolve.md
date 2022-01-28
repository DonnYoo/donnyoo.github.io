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
  
- 먼저 기본 셋팅을 해준다.
  * Dissolve되는 부분의 반투명 느낌을 위해 Translucent를 해준다.
  * Translucency에서 Lighting Mode를 Surface TranslucencyVolume으로 바꿔줘야 검은색 부분에 Metallic, Specular 그리고 Roughness를 줄 수 있다.
  
![1](/Images/Material&Texture/M_Dissolve1.png){: .align-center}
![2](/Images/Material&Texture/M_Dissolve2.png){: .align-center}  
  
---  
  
- Mesh에 UV를 만들어 준다.
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
  
- 중간 core 라인을 만들어보자.
  * 3ColorBlend를 추가한다.
![3](/Images/Material&Texture/M_Dissolve8.png){: .align-center}  
    
  * Mask와 3ColorBlend사이에 CheapContrast를 추가하고 Parameter를 Constrast에 연결한다.
  * Parameter를 thickness_core로 하고 값을 수정하여 core 라인의 크기를 조절 할 수 있다.
    ![3](/Images/Material&Texture/M_Dissolve9.png){: .align-center}  
      
