---
layout: post
title:  "[Programmers] 수박수박수박수박수박수?"
date:   2022-06-13 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220613/220613_3Scr1.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(int n) {
    string answer = "";
    int flag = 1;
    
    for(int i=0; i<n; i++){
        if(flag == 1) answer += "수";
        else answer += "박";
        
        flag *= -1;
    }
    
    return answer;
}
~~~

![Scr1](/img/220613/220613_3Scr2.png)

***
* eMail : <yskl7137@gmail.com>
