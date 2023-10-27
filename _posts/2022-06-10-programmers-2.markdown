---
layout: post
title:  "[Programmers] 정수 제곱근 판별"
date:   2022-06-10 10:23:56 +0900
categories: CodingTest Cmath
---

![Scr2](/img/220610/220610_2Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <cmath>

using namespace std;

long long solution(long long n) {
    long long answer = 0;
    long long root = sqrt(n);
    
    if(root*root == n){
        answer = (root+1) * (root+1);
    }else {
        answer = -1;
    }
    
    return answer;
}
~~~

![Scr1](/img/220610/220610_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
