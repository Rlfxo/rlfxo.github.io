---
layout: post
title:  "[Programmers] x만큼 간격이 있는 n개의 숫자"
date:   2022-06-08 08:23:56 +0900
categories: CodingTest Vector
---

![Scr2](/img/220608/220608_1Scr2.png)

Note <br>
![noteImg](/img/220608/220608_1.PNG)


~~~ c
#include <string>
#include <vector>

using namespace std;

vector<long long> solution(int x, int n) {
    vector<long long> answer;
    
    for(int i=1; i<n+1; i++){
        answer.push_back(x * i);
    }
    
    return answer;
}
~~~

![Scr1](/img/220608/220608_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
