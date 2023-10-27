---
layout: post
title:  "[Programmers] 2016년"
date:   2022-06-27 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220627/220627_1Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(int a, int b) {
    string answer = "";
    string moon[7] = {"SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT"};
    
    if(a == 1 || a == 4 || a == 7){
        a = 5;
    }else if(a == 2 || a == 8){
        a = 1;
    }else if(a == 3 || a == 11){
        a = 2;
    }else if(a == 5){
        a = 0;
    }else if(a == 6){
        a = 3;
    }else if(a == 9 || a == 12){
        a = 4;
    }else {
        a = 6;
    }
    
    b -= 1;
    b %= 7;
    if(a+b > 6) b -= 7;
    answer = moon[a+b];
    
    return answer;
}
~~~

![Scr1](/img/220627/220627_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
