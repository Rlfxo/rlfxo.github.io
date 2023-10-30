---
layout: post
title:  "[Programmers] 실패율"
date:   2022-06-28 11:23:56 +0900
categories: CodingTest Hash Kakao Resolve
---

![Scr2](/img/220628/220628_Scr2.png)
![Scr3](/img/220628/220628_Scr3.png)

Note <br>
![Img](/img/220628/220628.PNG)

~~~ c
#include <string>
#include <vector>
#include <map>
#include <algorithm>

using namespace std;

bool cmp(pair<double,int> a, pair<double,int> b){
    if(a.first == b.first) return a.second < b.second;
    else return a.first > b.first;
}

vector<int> solution(int N, vector<int> stages) {
    vector<int> answer;
    vector<pair<double,int>> per;
    map<int, double> ma;
    
    for(int i=0; i<stages.size(); i++){
        ma[stages[i]]++;
    }
    
    double minus_mem = 0;
    for(int i=1; i<=N; i++){
        if(ma[i] == 0){
            per.push_back({0,i});
            continue;
        }
        per.push_back({ma[i]/(stages.size()-minus_mem),i});
        minus_mem += ma[i];
    }
    sort(per.begin(), per.end(), cmp);
    for(auto o: per){
        answer.push_back(o.second);
    }
    
    return answer;
}
~~~

![Scr1](/img/220628/220628_Scr1.png)

***
* eMail : <yskl7137@gmail.com>
