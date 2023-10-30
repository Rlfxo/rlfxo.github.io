---
layout: post
title:  "[Programmers] 모의고사"
date:   2022-06-29 11:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220629/220629_3Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

vector<int> solution(vector<int> answers) {
    vector<int> answer;
    int uno = 0, u = 0;
    int dos = 0, d = 0;
    int tres = 0, t =0;
    
    int unonum[5] = {1,2,3,4,5};
    int dosnum[8] = {2,1,2,3,2,4,2,5};
    int tresnum[10] = {3,3,1,1,2,2,4,4,5,5};
    
    for(int i=0; i<answers.size(); i++){
        if(unonum[u] == answers[i]) uno++;
        if(dosnum[d] == answers[i]) dos++;
        if(tresnum[t] == answers[i]) tres++;
        
        u++;
        d++;
        t++;
            
        if(u > 4) u = 0;
        if(d > 7) d = 0;
        if(t > 9) t = 0;
    }
    
    int max = 0;
    if(max < uno) max = uno;
    if(max < dos) max = dos;
    if(max < tres) max = tres;
    
    if(max == uno) answer.push_back(1);
    if(max == dos) answer.push_back(2);
    if(max == tres) answer.push_back(3);
    return answer;
}
~~~

![Scr1](/img/220629/220629_3Scr1.png)

***
* eMail : <yskl7137@gmail.com>
