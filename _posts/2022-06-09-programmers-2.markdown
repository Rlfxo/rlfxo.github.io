---
layout: post
title:  "[Programmers] 평균 구하기"
date:   2022-06-09 08:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220609/220609_2Scr2.png)

~~Note <br>~~


~~~ c
#include <string>
#include <vector>

using namespace std;

double solution(vector<int> arr) {
    double answer = 0;
    double sum = 0;
    
    for(int i=0; i<arr.size(); i++){
        sum += arr[i];
    }
    
    answer = sum / arr.size();
    
    return answer;
}
~~~

![Scr1](/img/220609/220609_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
