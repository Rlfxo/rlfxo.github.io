---
layout: post
title:  "[Programmers] 정수 내림차순으로 배치하기"
date:   2022-06-10 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220610/220610_3Scr1.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

bool cmp(int a, int b) { 
  return a > b; 
}

long long solution(long long n) {
    long long answer = 0;
    vector<int> v;
    
    while(n != 0){
        v.push_back(n%10);
        n = n/10;
    }
    sort(v.begin(),v.end(),cmp);
    
    for(int i=0; i<v.size(); i++){
        answer = (answer*10) + v[i];
    }
    
    return answer;
}
~~~

![Scr1](/img/220610/220610_3Scr2.png)

***
* eMail : <yskl7137@gmail.com>
