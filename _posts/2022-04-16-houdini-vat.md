---
layout: single
title: "VAT [Vertex Animaion Texture]"
categories:
- "VAT"
tags:
- [Houdini, VAT, Vertex Animation Texture]

toc: true
toc_sticky: true

date: 2022-04-16
last_modified_at: 2022-04-16
---


# What are Vertex Animation Textures

---

## VAT [Vertex Animation Textures]

- Only uses textures and shaders to achieve the visuals on the GPU.
- this bakes the animation of a mesh into textures.
  - mesh기반 animation을 texture로 만들어 준다.
- each pixel holds a certain data for geomatry to move on based on vertex

  ![Untitled](/Images/Houdini/VAT/Untitled.png)

  [Texture Animation]


- 보통 bone or controller 를 사용하여 Animation을 만든다.

![Untitled](/Images/Houdini/VAT/Untitled%201.png)

- 하지만 Complex simulations 같은 경우 bone을 이용해서 Animation을 만들기에는 어렵다.

![Untitled](/Images/Houdini/VAT/Untitled%202.png)

- Vertex Animation Textures는 밑에와 같은 complex simulation을 만드는데 유용하다.

![Untitled](/Images/Houdini/VAT/Untitled%203.png)

# How  It Works

- Each Frame has position value.
  - 현재 1 frame 에서는 value 가 없기 때문에 geo는 평면이다.

    ![Untitled](/Images/Houdini/VAT/Untitled%204.png)

  - 2 frame 에서는 value가 들어간것을 볼 수 있다. 이로 인해 geo는 움직인다.

    ![Untitled](/Images/Houdini/VAT/Untitled%205.png)


## Labs Vat Exporter

- 4 Methods
  - Soft-body
  - Rigid-Body Dynamics
  - Dynamic remeshing
  - Particle sprites


![Untitled](/Images/Houdini/VAT/Untitled%206.png)

# Install VAT for Unreal Engine

## Install VAT

- obj→ out 변경

  ![Untitled](/Images/Houdini/VAT/Untitled%207.png)


- out 으로 변경 후 VAT node를 생성할 수 있다.

  ![Untitled](/Images/Houdini/VAT/Untitled%208.png)


- 중간 메뉴바에 Real-Time Shaders 클릭 → 하단부의 Unreal Engine Content Pluhin and Guides클릭을 하면 사용하고자하는 Unreal Engine 버전 폴더의 위치로 이동이 된다.
- 이후 사용하고자 하는 Unreal Engine의 버전안에 들어가면 SideFXLabs Plugin 폴더로 이동된다.

![Untitled](/Images/Houdini/VAT/Untitled%209.png)

![Untitled](/Images/Houdini/VAT/Untitled%2010.png)

- SideFX_Labs 폴더를 복사 후 Unreal Project폴더 안(Contents,Plugins가 있는 폴더)에서 Plugins폴더 안에 붙여 넣기를 한다. (Plugins폴더가 없다면 폴더 생성을 해준다.)

  ![Untitled](/Images/Houdini/VAT/Untitled%2011.png)

- Unreal Engine 안에서 SideFX_Labs Plugin이 잘 들어와 있는것을 확인할 수 있다.

  ![Untitled](/Images/Houdini/VAT/Untitled%2012.png)

- 최종적으로 Material을 생성해 VAT가 들어오는지 확인.

  ![Untitled](/Images/Houdini/VAT/Untitled%2013.png)


# Cloth / Soft Body and Result

## Export

- out Network 에서 VAT node 생성.

  ![Untitled](/Images/Houdini/VAT/Untitled%2014.png)

- Soft-Body 선택

  ![Untitled](/Images/Houdini/VAT/Untitled%2015.png)

- Engine 은 Unreal Engine을 쓸거기 때문에 Unreal Engine으로 셋팅한다.

![Untitled](/Images/Houdini/VAT/Untitled%2016.png)

- Cache를 쓴다면 check, 아니라면 uncheck

![Untitled](/Images/Houdini/VAT/Untitled%2017.png)

- 사용 Engine이 16/32를 사용한다면 HDR로 선택한다.

![Untitled](/Images/Houdini/VAT/Untitled%2018.png)

- Render

  ![Untitled](/Images/Houdini/VAT/Untitled%2019.png)

- 해당 Export 폴더안에 폴더,파일들이 생성된걸 확인할 수 있다.

  ![Untitled](/Images/Houdini/VAT/Untitled%2020.png)


## Import

- Unreal Engine안에 임의 폴더 생성 후 Drag and Drop 으로 export한 폴더를 옮겨 준다.

  ![Untitled](/Images/Houdini/VAT/Untitled%2021.png)


- Import 설정
- Default

![Untitled](/Images/Houdini/VAT/Untitled%2022.png)

![Untitled](/Images/Houdini/VAT/Untitled%2023.png)

- After

![Untitled](/Images/Houdini/VAT/Untitled%2024.png)

![Untitled](/Images/Houdini/VAT/Untitled%2025.png)

- Material 생성 후 기본 셋팅 설정.
  - 체크 해제.

    ![Untitled](/Images/Houdini/VAT/Untitled%2026.png)

  - VAT가 가지고 있는 UV Channal 수 만큼 변경해 준다.

    ![Untitled](/Images/Houdini/VAT/Untitled%2027.png)

    ![Untitled](/Images/Houdini/VAT/Untitled%2028.png)

    ![Untitled](/Images/Houdini/VAT/Untitled%2029.png)

- VAT_SoftBodyDeformation 생성 후 Node연결.

  ![Untitled](/Images/Houdini/VAT/Untitled%2030.png)

- Material Instance 생성 후 Position Texture 와 Rotation Texture에 Import한 Texture들을 할당한다.

  ![Untitled](/Images/Houdini/VAT/Untitled%2031.png)

  ![Untitled](/Images/Houdini/VAT/Untitled%2032.png)

  ![Untitled](/Images/Houdini/VAT/Untitled%2033.png)

- Import된 Static Mesh에 위에서 만든 Material 적용시 바로 Animation이 적용된걸 볼 수 있다.

  ![VAT_Cloth_Tutorial.gif](/Images/Houdini/VAT/VAT_Cloth_Tutorial.gif)

  *[result]*