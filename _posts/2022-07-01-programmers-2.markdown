---
layout: post
title:  "[Programmers] 내적"
date:   2022-07-01 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220701/220701_2Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(vector<int> a, vector<int> b) {
    int answer = 0;
    
    for(int i=0; i<a.size(); i++){
        answer += a[i] * b[i];
    }
    
    return answer;
}
~~~

![Scr1](/img/220701/220701_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
