---
title:  "STL Stack 기본"

categories:
- CPP

tags:
- [Stack, C++, CPP]

toc: true
toc_sticky: true

date: 2022-01-22
last_modified_at: 2022-01-22
---  
  
Stack 기본함수
---

**추가 및 삭제**  
- `push(element)`: top에 원소를 추가
- `pop()`: top에 있는 원소를 삭제
  
**조회**  
- `top()`: top에 있는 원소를 반환  
  
**기타**  
- `empty()`: stack이 비어있으면 true 아니면 false를 반환
- `size()`: stack 사이즈를 반환  
  
구현
---
~~~c++
#include <iostream>
#include <stack>
using namespace std;

int main()
{
    //stack 생성
    stack<int> s;
    
    //push
    s.push(3);
    s.push(2);
    s.push(1);
    
    //top
    cout<<"top element:"<<s.top()<<'\n';
    // top element: 1
    
    //pop
    s.pop(); // 1 삭제
    s.pop(); // 2 삭제
    // 가장 마지막부터 순서대로 삭제
    
    //size
    cout<<"stack size:"<<s.size()<<'\n';
    // stack size: 1
    
    //empty
    cout<<"Is it empty?:"<<(s.empty() ? "Yes" : "No")<<'\n';
    // Is it empty?: No
    
   return 0;
 }
 ~~~