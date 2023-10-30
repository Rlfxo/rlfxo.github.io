---
layout: post
title:  "[Programmers] 성격 유형 검사하기"
date:   2022-09-08 10:23:56 +0900
categories: CodingTest Kakao
---

![Scr2](/img/220908/220908_1Scr2.png)
![Scr3](/img/220908/220908_1Scr3.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <map>

using namespace std;

string solution(vector<string> survey, vector<int> choices) {
    string answer = "";
    int cnt = -1;
    map <char, int> m;
    
    for(auto& i : choices){
        char type;
        int value;
        cnt++;
        
        if(i < 4){
            type = survey[cnt][0];
        }else if(i > 4){
            type = survey[cnt][1];
        }else{
            continue;
        }
        
        if(i == 1 || i == 7) value = 3;
        else if( i == 2 || i == 6) value = 2;
        else value = 1;
        
        m[type] += value;
    }
    
    if(m['R'] >= m['T']) answer += "R";
    else answer += "T";
    
    if(m['C'] >= m['F']) answer += "C";
    else answer += "F";
    
    if(m['J'] >= m['M']) answer += "J";
    else answer += "M";
    
    if(m['A'] >= m['N']) answer += "A";
    else answer += "N";
    
    return answer;
}
~~~

![Scr1](/img/220908/220908_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
