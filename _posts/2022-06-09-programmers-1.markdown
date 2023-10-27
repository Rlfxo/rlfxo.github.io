---
layout: post
title:  "[Programmers] 하샤드 수"
date:   2022-06-09 08:23:56 +0900
categories: CodingTest While
---

![Scr2](/img/220609/220609_1Scr2.png)

Note <br>
![noteImg](/img/220609/220609_1.PNG)


~~~ c
#include <string>
#include <vector>

using namespace std;

bool solution(int x) {
    bool answer = true;
    
    int sum = 0;
    int temp = x;
    
    while(temp != 0){
        sum += temp % 10;
        temp = temp / 10;
    }
    
    if(x % sum != 0) answer = false;
    
    return answer;
}
~~~

![Scr1](/img/220609/220609_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
