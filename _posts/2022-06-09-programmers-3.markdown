---
layout: post
title:  "[Programmers] 콜라츠 추측"
date:   2022-06-09 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220609/220609_3Scr2.png)

Note <br>
![noteImg](/img/220609/220609_3.PNG)


~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(int num) {
    int answer = 0;
    long long n = num;
    
    while(n != 1){
        if(answer > 500){
            answer = -1;
            break;
        }
        
        if(n % 2 == 0){
            n /= 2;
        }else{
            n *= 3;
            n++;
        }
        
        answer++;
    }
    
    return answer;
}
~~~

![Scr1](/img/220609/220609_3Scr1.png)

***
* eMail : <yskl7137@gmail.com>
