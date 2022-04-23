---
layout: single
title: "Tutorial - Tearing Meat"
categories:
- "Tutorial"
tags:
- [Houdini, Tutorial, Vellum]

toc: true
toc_sticky: true

date: 2022-04-23
last_modified_at: 2022-04-23
---

  
  

# 1.Vellum_Meat

## [Result]

---

![Vellum_Meat5.gif](/Images/Houdini/TearingMeat/Vellum_Meat5.gif)

---

## Start

---

- Sphere 생성

  ![Untitled](/Images/Houdini/TearingMeat/Untitled.png)

- 크기가 작아 Radius를 1로 키운다.

  Primitive Type 은 Polygon으로 변경한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%201.png)

  이후 Frequency를 10으로 변경한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%202.png)

  변경 후 모습.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%203.png)

- 바닥과의 거리를 두기위해 Transform으로 Sphere위치를 옮겨 준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%204.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%205.png)


- Group생성. (필요없을거 같다고 하지만 일단 생성한다.)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%206.png)

- Sphere에 균열을 주기 위해 RBD Material Fracture  생성한다.

  이후 RBD Exploded View를 생성하면 어떤식으로 생성이 되는지 볼 수 있다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%207.png)

- Assemble 추가.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%208.png)

  - Assemble

    [Cleans up a series of break operations and creates the resulting pieces.]

    eg) from Houdini Official Site.

    ![Untitled](/Images/Houdini/TearingMeat/Untitled%209.png)


- 필요한  Nodes를 가져오기 위해 새로운 Sphere를 생성한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2010.png)

  그리고 sphere에 들어가 Vellum Tetrahedral Softbody를 생성한다. (필요한 Nodes가 여기에 들어있다.)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2011.png)

  이후 sphere _object1(임시 Sphere)에 들어가면 또 새로 생성된 Nodes를 볼 수 있다.

  표시한 부분이 필요한 Nodes다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2012.png)

- 먼저 Poly Reduce, Remesh, Tetconform을 복사하여 써야할 Sphere geo안에 For-Each Named Primitive사이에 붙여넣기 한다.

![Untitled](/Images/Houdini/TearingMeat/Untitled%2013.png)

![Untitled](/Images/Houdini/TearingMeat/Untitled%2014.png)

- 붙여넣기 한 각,각의 Nodes는..

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2015.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2016.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2017.png)

- 임시 Sphere에서 Tetrahedral_Constraints를 복사하여 Vellum_meat geo안의 For-Each Named Primitive 밖에 붙여넣기 한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2018.png)

- Also 임시 Sphere에서 NULL[ GEO, CON]을 복사해 Vellum_meat geo안 Tetrahedral_Constraints밑에 붙여넣기하여 연결 시켜준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2019.png)

- Meat Core를 양옆으로 잡아 당길 수 있는 Box를 만들어주고 Animation Frame을 셋팅해준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2020.png)

  Meat Core와 높이를 맟추기 위해 높이는 Core와 같은 3으로 설정.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2021.png)

  약간 겹치게 위치 설정. (Translate X = -1.4)

  이제 Frame별로 Box의 위치를 잡아준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2022.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2023.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2024.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2025.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2026.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2027.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2028.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2029.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2030.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2031.png)

  *[Result]*

  ![Vellum_Meat1.gif](/Images/Houdini/TearingMeat/Vellum_Meat1.gif)

  이제 반대쪽 Box도 만들어준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2032.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2033.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2034.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2035.png)

- Box와 Meat Core의 접촉점을 만들기 위해 Group을 추가하여 Boxes와 Vellum_meat을 연결한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2036.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2037.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2038.png)

- Vellum Attatched Geometry 추가 후 Boxes를 Merge한 Node는 Tetrahedral_Constraints 마지막 input에도 연결시켜 준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2039.png)

  (실질적  collision objects(merge)가 3번째 input 으로 들어간다.)

  *[result]*

  ![Vellum_Meat2.gif](/Images/Houdini/TearingMeat/Vellum_Meat2.gif)

  조각,조각 떨어져야하지만 모든 Primitives가 붙어 있는걸 볼 수 있다.

- 이것들을 떨어뜨리기 위해 Vellum Attach to Geometry의 설정변경이 필요하다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2040.png)

  *[result]*

  ![Vellum_Meat3.gif](/Images/Houdini/TearingMeat/Vellum_Meat3.gif)

  떨어지지만 Boxes가 움직이기 전부터 조각나는걸 볼 수 있다.

- 수정을 위해 Vellum Solver Node안에 Vellum Constraints를 추가하고 설정을 변경해준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2041.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2042.png)

  *[result]*

  ![Vellum_Meat4.gif](/Images/Houdini/TearingMeat/Vellum_Meat4.gif)

- Vellum_meat 의 최종 디테일을 위해서는 밑에 보이는 것과 같은 Stitch(Constraints)가 필요한데 위의 방법 Vellum Solver를 사용했을때는 Stich를 가져올수가 없다. 혹은 모른다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2043.png)

  위에 보이는 Stitch가 필요한 이유는 Strings를 Stitch(Constraints)로부터 만들기 위해서다.

  이를 위해서는 Vellum Solver대신해 DOP Network를 사용한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2044.png)

- 임시 Sphere밑에 생성된 Auto DOP Network안의 모든 노드를 복사하여 Vellum_meat안에 방금만든 DOP Network안에 Vellum Source의 Path들을 바꿔준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2045.png)

- merge와 vellumsolver사이에 Vellum_Constraints를 생성하고 설정을 변경한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2046.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2047.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2048.png)

  - Vellum Constraints → Breaking → Threshold 의 수치를 바꾸면 Breaking강도를 조절할 수 있다.

    ![Untitled](/Images/Houdini/TearingMeat/Untitled%2049.png)


- 임시 Sphere밑의 tetsoftbody_vellum geo안에 모든 Nodes를 복사하여

  Vellum_meat 최하단에 붙여넣기 한 후 2개의 import_geometry가 있는데

  둘다  DOP Network  Path를 바꿔준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2050.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2051.png)

- vellum post process 의 Apply Welds 옵션을 언체크 해준다.

  Apply Welds는 Breaking Points를 String을 만들어 계속 붙여주기 때문에

  만들고자하는 Object에 맞지 않는 옵션이다.

- [Final Result]

  ![Vellum_Meat5.gif](/Images/Houdini/TearingMeat/Vellum_Meat5%201.gif)


# 2.Vellum_Strings

## [Result]

---

![Vellum_Strings3.gif](/Images/Houdini/TearingMeat/Vellum_Strings3.gif)

---

## Start

---

- 먼저 Vellum_strings 를 만들기위해 필요한 부분만 가져오기위한 작업을 한다.

  Vellum_meat 에서  import_constraints를  Null로 추출하고 이름은 OUT_CON으로 설정.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2052.png)

  Vellum_strings에서 object merge 로 위에서 추출한 Null을 Object로 넣어주고 Transform은 Into This Object로 바꿔준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2053.png)

  이제 필요한 부분(Stitch)만 빼기위해 Delete 작업을 해준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2054.png)

  Box부분과 맞닿는 부분을 없애주기 위해 Delete를 하나더 추가한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2055.png)

- DOP Network생성 후 Vellum Hair생성 한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2056.png)

  Vellum Hair생성 후 생성되는 Nodes와 DOP Network안에 생성되는 Nodes를 볼 수 있다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2057.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2058.png)

- 새로운 object_merge생성하여 Object에는 Vellum_meat의 OUT을 넣어준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2059.png)

  필요한것은 inside이기 때문에 outside는 delete한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2060.png)

  그리고 Null로 추출.  이름은 OUT_Meat_Inside로 한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2061.png)

  DOP Network안에 Vellum Constraints를 생성하고 설정변경 후 Target Path에 방금 생성한 OUT_Meat_Inside를 넣어준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2062.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2063.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2064.png)

- *[result]*

  ![Vellum_Strings1.gif](/Images/Houdini/TearingMeat/Vellum_Strings1.gif)


- Strings가 끊어지는걸 원한다.

  DOP Network안에 Vellum Constraint Property 추가 후 설정번경한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2065.png)

  Script는 Stress가 0.5보다 클경우 broken을 1로 변경하여 Strings가 끊어지도록 한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2066.png)

  *[result]*

  ![Vellum_Strings2.gif](/Images/Houdini/TearingMeat/Vellum_Strings2.gif)

- 마지막으로 obj에 보면 hair_vellum이 생성된걸 볼 수 있다.

  이 안의 Nodes를 복사하여 Vellum_strings에 붙여넣기 한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2067.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2068.png)

  마지막 vellumpostprocess의 설정을 바꿔준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2069.png)

- Collision and Ground생성.

  우선 바로전에 만든 object_merge를 복사해서 object_merge를 하나더 생성하고 Null생성. 이름은 OUT_COL.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2070.png)

  그리고 Deforming Object를 생성한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2071.png)

  Deforming Object를 생성하면 생성되는 Nodes를 볼 수 있다.

  또한 DOP Network안에도 새로생성된 Nodes를 볼 수 있다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2072.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2073.png)

  그리고 Static Object 옆에 ground를 생성하고 merge 시켜준다.( 순서는 ground가 첫번째로 간다.)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2074.png)

  *[result]*

  ![Vellum_Strings3.gif](/Images/Houdini/TearingMeat/Vellum_Strings3.gif)


# 3.Vellum_Fur

## Result

---

![Vellum_Fur4.gif](/Images/Houdini/TearingMeat/Vellum_Fur4.gif)

---

## Start

---

- Vellum_fur에 Object Merge 생성 후 Vellum_meat OUT을 Object에 넣어준다.

  그리고 HairGeneration 생성 한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2075.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2076.png)

  안쪽은 필요한 부분이 없기때문에 없애주는 작업을 한다.

- HairGeneration 생성 후 Hair가 Core 안쪽까지 생성된걸 볼 수 있다. 이것은 Fracture 후 안쪽 surface도 생겨서 그부분까지 Hair가 생성이 된 것이다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2077.png)

- Vellum_meat에서 Fraction전에 Null 생성을 하여 이것을 Vellum_fur에 새로운 Object_Merge를 생성해서 넣어준다. 그리고 HairGeneration도 다시 연결해준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2078.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2079.png)

  결과로 외부만 Hair가 생긴것을 볼 수 있다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2080.png)

- For_Each_Primitive 생성 후 Group Create 생성.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2081.png)

  0을가진 모든 points가 선택이 되도록 설정 변경 한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2082.png)

- Null OUT을 생성하고 DOP Network와 Vellum Hair를 생성한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2083.png)

  DOP Network안에는 Gravity 를 생성해준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2084.png)

  그리고  obj Network에 보면 hair_vellum이 생성된걸 볼 수 있는데 안에 Nodes를 복사해서 Vellum_fur에 붙여넣기 한 후 hair_vellum은 지워준다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2085.png)

  *[result]*

  ![Vellum_Fur1.gif](/Images/Houdini/TearingMeat/Vellum_Fur1.gif)

- Hair들을 뜯어지는 부분에만 붙여준다.

  이를위해 처음에 생성했던 object_merge를  Vellum Hair 3번째 input에 연결하고 그밑에 Vellum Attatch to Geometry생성해 설정변경을 한다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2086.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2087.png)

  [result]

  ![Vellum_Fur2.gif](/Images/Houdini/TearingMeat/Vellum_Fur2.gif)

- Vellum_meat and Vellum_strings 다 같이 플레이를 한 경우 fur가 meat외부에 붙어있지 않고 안으로 들어가는걸 볼 수 있다.

  ![Vellum_Fur3.gif](/Images/Houdini/TearingMeat/Vellum_Fur3.gif)

- 위부분 해결은 Vellum_strings의 DOP Network안 3개의 Nodes를 복사해 Vellum_fur의 DOP Network안에 붙여 넣기 해줌으로 해결된다.

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2088.png)

  ![Untitled](/Images/Houdini/TearingMeat/Untitled%2089.png)

  *[result]*

  ![Vellum_Fur4.gif](/Images/Houdini/TearingMeat/Vellum_Fur4.gif)


# 4.Vellum_Blood