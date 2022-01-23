---
title:  "UnrealEngine C++ TMap 기본"

categories:
- UECPP

tags:
- [TMap, C++, CPP, Unreal Engine]

toc: true
toc_sticky: true

date: 2022-01-22
last_modified_at: 2022-01-22
---

TMap 기본함수
---  
  
### 기본형
- `TMap<int32, FString> map`  

### 추가
- `Add()`: Add(key,value)로 TMap에 추가한다
- `Emplace()`: Add()와 마찬가지로 key와 value를 추가한다  
- `Append()`: 두개의 TMap을 합쳐주며 합쳐진 TMap의 elements들은 사라진다  

~~~c++
TMap<int32, FString> map;

map.Add(5, TEXT("Banana"));
map.Add(2, TEXT("Grapefruit"));
map.Add(7, TEXT("Pineapple"));
/* map == [
    {key: 5, value: "Banana"},
    {key: 2, value: "Grapefruit"},
    {key: 7, value: "Pineapple"}
    ]
*/
map.Add(2, TEXT("Pear");
/* map == [
    {key: 5, value: "Banana"},
    {key: 2, value: "Pear"}, Grapefruit에서 Pear로 바뀌었다
    {key: 7, value: "Pineapple"}
    ]
*/ 
map.Add(4);
/* map == [
    {key: 5, value: "Banana"},
    {key: 2, value: "Pear"},
    {key: 7, value: "Pineapple"},
    {key: 4, value: ""} key값만 초기화 했기때문에 value값이 없다
    ]
*/ 
map.Emplace(3, TEXT("Orange"));
/* map == [
    {key: 5, value: "Banana"},
    {key: 2, value: "Pear"},
    {key: 7, value: "Pineapple"},
    {key: 4, value: ""}
    {key: 3, value: "Orange"}
    ]
*/ 
TMap<int32, FString> map2;
map2.Emplace(4, TEXT("Kiwi"));
map2.Emplace(9, TEXT("Melon"));
map2.Emplace(5, TEXT("Mango"));
map.Append(map2);
/* map == [
    {key: 5, value: "Mango"}, Banana에서 Mango로 바뀜
    {key: 2, value: "Pear"},
    {key: 7, value: "Pineapple"},
    {key: 4, value: "Kiwi"}, 비어있던 Value가 Kiwi로 바뀜
    {key: 3, value: "Orange"},
    {key: 9, value: "Melon"}
    ]
    //map2 is now empty.
*/ 
~~~  
- 만약 TMap에 UPROPERTY()와  
"editable" keywords(EditAnywhere,EditDefaultOnly or EditInstanceOnly)를  
사용한다면 Editor안에서도 elements를 추가하거나 수정 할 수 있다.
~~~c++
UPROPERTY(EditAnywhere, Category = Map)
TMap<int32, FString> map;
~~~  
  
### iteration  
- for(type& v : map){}
~~~c++
for (auto& Elem : map)
{
    FPlatformMisc::LocalPrint
    (*FString::Printf(TEXT("(%d, \"%s\"\n"),Elem.Key, *Elem.Value));
}
/*
Output:
(5, "Mango")
(2, "Pear")
(7, "Pineapple")
(4, "Kiwi")
(3, "Orange")
(9, "Melon")
*/
~~~  
- CreateIterator(), CreateConstIterator()  
~~~c++
for (auto it = map.CreateConstIterator(); it; ++it)
{
    FPlatformMisc::LocalPrint
    (*FString::Printf(TEXT("(%d, \"%s\")\n"), it.Key(), *it.Value()));
}
// it.Key()     Same as it->Key
// *it.Value()  Same as *it->Value
~~~  
  
### Queries  
- `Num()`: 얼마큼의 elements가 있는지 알려준다
~~~c++
int32 count = map.Num();
// count == 6
~~~  
  
- `Contains()`: 지정한 key가 있는지 알려준다
~~~c++
bool bHas7 = map.Contains(7);
bool bHas8 = map.Contains(8);
// bHas7 == true
// bHas8 == false
~~~  
  
- `operator[]`: 지정한 key의 value값을 바로 불러온다
~~~c++
FString val7 = map[7];
// val7 == "Pineapple"
FString val8 = map[8];
// Assert!
~~~  
  
- `Find()`: 만약 특정 key가 map에 포함되어있는지 확실하지 않을때 확인한다
~~~c++
FString* ptr7 = map.Find(7);
// *ptr7 == "Pineapple"
FString* ptr8 = map.Find(8);
// ptr8 == nullptr
~~~  
  
- `FindOrAdd()`: 특정한 key가 있는지 찾아주고 map에 포함되어 있지 않다면 key와 기본 value값을 생성해 추가해준다. non-const에서만 사용가능
- `FindRef()`: 특정한 key의 복사본을 반환한다. 새로 생성하지 않으며 const,non-const모두 사용가능. 찾는 key가 없더라도 문제가 생기지 않는다
~~~c++
FString& ref7 = map.FindOrAdd(7);
/*
ref7 == "Pineapple"
map == [
    {key: 5, value: "Mango"},
    {key: 2, value: "Pear"},
    {key: 7, value: "Pineapple"},
    {key: 4, value: "Kiwi"},
    {key: 3, value: "Orange"},
    {key: 9, value: "Melon"}
    ]*/
FString& ref8 = map.FindOrAdd(8);
/*
ref8 == ""
map == [
    {key: 5, value: "Mango"},
    {key: 2, value: "Pear"},
    {key: 7, value: "Pineapple"},
    {key: 4, value: "Kiwi"},
    {key: 3, value: "Orange"},
    {key: 9, value: "Melon"},
    {key: 8, value: ""} key 8이 없기때문에 새로생성 되었다
    ]*/
FString val7 = map.FinRef(7);
FString val8 = map.FinRef(6);
/*
val7 == "Pineapple"
val6 == ""
map == [
    {key: 5, value: "Mango"},
    {key: 2, value: "Pear"},
    {key: 7, value: "Pineapple"},
    {key: 4, value: "Kiwi"},
    {key: 3, value: "Orange"},
    {key: 9, value: "Melon"},
    {key: 8, value: ""}
    ] key 6이 없기때문에 아무일도 일어나지 않는다
    */
~~~  
  
- `FindKey()`: value값으로 key를 찾는다. 포인터로 반환



