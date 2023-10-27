---
layout: post
title:  "[Programmers] 예산"
date:   2022-06-27 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220627/220627_3Scr2.png)

Note <br>

~~~ c
#include <iostream>
#include <stdio.h>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int solution(vector<int> d, int budget) {
    int answer = 0;
    
    sort(d.begin(), d.end());
    for(int i=0; i<d.size(); i++){
        if(budget < 0){
            break;
        }
        budget -= d[i];
        answer++;
    }if(budget < 0) answer--;
    
    return answer;
}
~~~

![Scr1](/img/220627/220627_3Scr1.png)

***
* eMail : <yskl7137@gmail.com>
