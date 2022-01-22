---
title:  "STL Vector 기본"

categories:
- CPP

tags:
- [Vector, C++, CPP]

toc: true
toc_sticky: true

date: 2022-01-22
last_modified_at: 2022-01-22
---

Vector 기본함수  
---

**추가 및 삭제**  
- `push_back(element)`: vector 제일 뒤에 원소를 추가  
- `pop_back()`: vector 제일 뒤에 원소를 삭제  
  
**조회**  
- `[i]`: i번째 원소를 반환
- `at(i)`: i번째 원소를 반환
- `front()`: 첫번째 원소를 반환
- `back()`: 마지막 원소를 반환  
  
**기타**  
- `empty()`: vector가 비어있으면 true 아닐경우 false를 반환  
- `size()`: vector 원소들의 수를 반환  

**Iterator**
- `begin()`: beginning iterator를 반환
- `end()`: end iterator를 반환
  
구현  
---
~~~c++
#include<iostream>
#include<vector>
using namespace std;

int main()
{
    vector<int> v;
    
    //push_back
    v.push_back(1);
    v.push_back(2);
    v.push_back(3);
    // 1,2,3
    
    //pop_back
    v.pop_back();
    // 1,2
    
    //front and back
    cout<<"vector front value:"<<v.front()<<'\n';
    cout<<"vector end value:"<<v.back()<<'\n';
    // vector front value: 1
    // vector end value: 2
    
    //[i] and at[i]
    cout<<"vector operator[]:"<<v[1]<<'\n;
    cout<<"vector at:"<<v.at(1)<<'\n';
    // vector operator[1]: 2
    // vector at 1: 2
    
    //size
    cout<<"vector size:"<<v.size()<<'\n';
    // vector size: 2
    
    //empty
    cout<<"Is it empty?:"<<(v.empty()?"Yes":"No")<<'\n';
    // Is it empty?: No
    
    //iterator
    vector<int>::iterator begin_iter = v.begin();
    vector<int>::iterator end_iter = v.end();
    // auto begine_iter, auto end_iter도 가능
    
    //get value by iterator
    cout<<"vector begin value:"<<*begin_iter<<'\n';
    cout<<"vector end value:"<<*end_iter<<'\n';
    // vector begin value: 1
    // vector end value: 3
    
    //for statement iteration using iterator
    for(vector<int>::iterator iter = v.begin(); iter != v.end(); iter++)
    {
        cout<<*iter<<'';
    }
    // 1 2
    cout<<endl;
    
    return 0;
    
 }
~~~

