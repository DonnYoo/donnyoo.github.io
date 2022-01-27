---
title:  "[C++]완주하지 못한 선수"

categories:
- ProgrammersCPP

tags:
- [Programmers, C++, CPP, Hash, Sort, Map]

toc: true
toc_sticky: true

date: 2022-01-27
last_modified_at: 2022-01-27
---  
  
문제
---
- 문제설명  
마라톤 참가선수 배열 = participant  
완주한 선수 배열 = completion  
완주하지 못한 선수의 이름을 return
  
- 제한사항  
 completion의 길이는 participant의 길이보다 1 작습니다.  
 참가자 중에는 동명이인이 있을 수 있습니다.
  
- 입출력 예  

|participant|completion|return|  
  |:---|:---|---|  
  |["leo","kiki","eden"]|["eden","kiki"]|"leo"|  
|["mislav","stanko","mislav","ana"]|["stanko","ana","mislav"]|"mislav"|  
  
- 입출력 예 설명  
예제#1 "leo"는 참여자 명단에 있지만, 완주자 명단에는 없기 때문에 완주하지 못했다.  
  예제#2 "mislav"는 참여자 명단에는 두 명이 있지만, 완주자 명단에는 한 명밖에  
  없기때문에 한명은 완주하지 못했다.  
  
- 문제 해석  
완주하지 못한 선수를 찾아라.  
  participant에는 있지만 completion에 없으면 return.  
  participant와 completion의 비교에서 남는것을 return.(동명이인)

풀이 #1 Hash
---
~~~c++
#include <string>
#include <vector>
#include <map>
using namespace std;

string solution(vector<string> participant, vector<string> completion)
{
    string answer = "";
    
    map<string, int> m;
    
    for(auto c : completion)
    {
        m[c] += 1;
    }
    
    for(auto p : participant)
    {
        m[p] -= 1;
        if(m[p] < 0)
        {
            answer = p;
        }
    }
    return answer;
}
~~~  


풀이 #2 Sort
---
~~~c++
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

string solution(vector<string> participant, vector<string> completion)
{
    string answer = "";
    sort(participant.begin(), participant.end());
    sort(completion.begin(), completion.end());
    for(int i=0; i<participant.size(); i++)
    {
        if(participant[i] != completion[i])
        {
            return participant[i];
        }
    }
    return answer;
}
~~~