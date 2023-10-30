---
layout: post
title:  "[Programmers] 두 정수 사이의 합"
date:   2022-06-15 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220615/220615_4Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

long long solution(int a, int b) {
    long long answer = 0;
        
    if(a == b) answer = a;
    else{
        if(a > b){
            int temp = b;
            b = a;
            a = temp;
        }
        for(int i=a; i<b+1; i++){
            answer += i;
        }
    }
    
    return answer;
}
~~~

![Scr1](/img/220615/220615_4Scr1.png)

***
* eMail : <yskl7137@gmail.com>
