---
layout: post
title:  "[Programmers] 음양 더하기"
date:   2022-07-01 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220701/220701_3Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(vector<int> absolutes, vector<bool> signs) {
    int answer = 0;
    
    for(int i=0; i<signs.size(); i++){
        if(signs[i]) answer += absolutes[i];
        else answer -= absolutes[i];
    }
    
    return answer;
}
~~~

![Scr1](/img/220701/220701_3Scr1.png)

***
* eMail : <yskl7137@gmail.com>
