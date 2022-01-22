---
title:  "STL Map 기본"

categories:
- CPP

tags:
- [Map, C++, CPP]

toc: true
toc_sticky: true

date: 2022-01-22
last_modified_at: 2022-01-22
---
  
  
Map 기본함수
---
  
**기본형태**  
- `map<key,value>`: key와 value를 pair형태로 선언한다.  
  
**iterator**  
- `begin()`: beginning iterator를 반환
- `end()`: end iterator를 반환  
  
**추가 및 삭제**  
- `insert(make_pair(key,value))`: map의 원소를 pair형태로 추가한다
- `erase(key)`: map에서 key값에 해당하는 원소를 삭제한다
- `clear()`: map의 모든원소를 삭제한다  
  
**조회**  
- `find(key)`: key값에 해당하는 iterator를 반환
- `count(key)`: key값에 해당하는 value들의 개수를 반환
  
**기타**  
- `empty()`: map이 비어있으면 true 아니면 false를 반환
- `size()`: map 원소들의 수를 반환  
  
구현 코드
---
~~~c++
#include <iostream>
#include <map>
#include <string>
using namespace std;

int main()
{
    //map
    //<string,int> -> <key,value>
    map<string, int> m;

    //insert(key, value)
    m.insert(make_pair("a",1));
    m.insert(make_pair("b",2));
    m.insert(make_pair("c",3));
    m.insert(make_pair("d",4));
    m.insert(make_pair("e",5));
    m["f"] = 6; //also possible
    
    //erase(key)
    m.erase("d");
    m.erase("e");
    m.erase(m.find("f")); //also possible
    
    //empty(), size()
    if(!m.empty())
    {
        cout<<"m size:"<<m.size()<<'\n';
    }
    //m size: 3
    
    //find(key)
    cout<<"a:"<<m.find("a")->second<<'\n';
    cout<<"b:"<<m.find("b")->second<<'\n';
    //a: 1
    //b: 2
    
    //begin(), end()
    cout<<"travers"<<'\n';
    for(auto it = m.begin(); it != m.end(); it++)
    {
        cout<<"key"<<it->first<<""<<"value:"<<it->second<<'\n';
    }
    //key value: 1
    //key value: 2
    //key value: 3
     
  return 0;
}
~~~
