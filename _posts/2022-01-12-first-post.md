---
layout: single
title: "Floating and Spinning"
excerpt: "이것은 처음이다"
categories:
 - "Effect"
tags:
  - [NiagaraSystem, UnrealEngine, Effect]

toc: true
toc_sticky: true

date: 2022-01-12
last_modified_at: 2022-01-12
---


Floating and Spinning
===  



---
![image1](/Images/20220112_16.gif){: .align-center}결과  

---


![image1](/Images/20220112_1.png){: .align-center}**Render**에서 **Mesh Render**를 추가 한다.

![image1](/Images/20220112_2.png){: .align-center}**Meshes**의 0번째 **Array**에 원하는 **StaticMesh**로 넣어준다.  

![image1](/Images/20220112_3.png){: .align-center}원하는 **Emitter**를 마우스로 클릭(노란색으로 활성화 된다.)  

![image1](/Images/20220112_4.png){: .align-center}**Emitter**를 활성화 시킨 후 **Parameters**에 보면 **PARTICLES/Position**이 나온다.  

![image1](/Images/20220112_5.png){: .align-center}이 **Position Parameter**를 **Emitter**의 **Particle Update**의 밑으로 **Drag&Drop** 해준다.  

![image1](/Images/20220112_6.png){: .align-center}그럼 이렇게 **Emitter**에 **Position**이 생성됨.  

![image1](/Images/20220112_7.png){: .align-center}이후  **Position**에서 **Make Vector**를 찾아 준다.  

![image1](/Images/20220112_8.png){: .align-center}이후 **Z**값에는 **Sine**을 넣어준다.(상하 움직임을 만들 것이다.)  

![image1](/Images/20220112_9.png){: .align-center}**Period**는 기간. **Scale**은 움직임 범위.  

![image1](/Images/20220112_10.gif){: .align-center}상하 움직임. 

![image1](/Images/20220112_11.png){: .align-center}**Particle Update**에서 **Update Mesh Orientation**을 추가.  

![image1](/Images/20220112_12.png){: .align-center}여기에선 **Rotation Vector**값에서 **Z**를 1로 준다.(**Yaw**축으로 회전을 할 것이다.)  
그리고 **Rotation Rate**에서 **Rate**값을 조절하여 회전 세기를 조절한다.  

![image1](/Images/20220112_13.gif){: .align-center}상하 움직임 과 회전.  

![image1](/Images/20220112_14.png){: .align-center}**Particle Spawn**에서 **Initial Mesh Orientation**을 추가한다.  

![image1](/Images/20220112_15.png){: .align-center}**Rotation Coordicate Spaced**의 **Rotation**값에서 **X**값을 조정해 **Roll**축의 회전을 조절한다.  

![image1](/Images/20220112_16.gif){: .align-center}