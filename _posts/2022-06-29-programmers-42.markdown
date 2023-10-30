---
layout: post
title:  "[Programmers] 체육복"
date:   2022-06-29 11:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220629/220629_2Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(int n, vector<int> lost, vector<int> reserve) {
    int answer = 0;
    vector<int> s;
    
    for(int i=0; i<n; i++) s.push_back(1);
    for(int i=0; i<lost.size(); i++) s[lost[i]-1]--;
    for(int i=0; i<reserve.size(); i++) s[reserve[i]-1]++;
    for(int i=0; i<n; i++){
        if(s[i] == 0){
            if(i > 0 && s[i-1] > 1){
                s[i]++;
                s[i-1]--;
            }else if(1 < n && s[i+1] > 1){
                s[i]++;
                s[i+1]--;
            }
        }
    }
    for(int i=0; i<n; i++) if(s[i] > 0) answer++;
    
    return answer;
}
~~~

![Scr1](/img/220629/220629_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
