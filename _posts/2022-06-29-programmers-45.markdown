---
layout: post
title:  "[Programmers] 완주하지 못한 선수"
date:   2022-06-29 11:23:56 +0900
categories: CodingTest Resolve
---

![Scr2](/img/220629/220629_5Scr2.png)

Note <br>
![Img](/img/220629/220629_5.PNG)

~~~ c
#include <string>
#include <vector>
#include <unordered_map>

using namespace std;

string solution(vector<string> participant, vector<string> completion) {
    string answer = "";
    
    unordered_map <string, int> m;
    for(auto& i : participant) m[i]++;
    for(auto& i : completion) m[i]--;
    for(auto& i : m){
        if(i.second > 0){
            answer = i.first;
            break;
        }
    }
    
    return answer;
}
~~~

![Scr1](/img/220629/220629_5Scr1.png)

***
* eMail : <yskl7137@gmail.com>
