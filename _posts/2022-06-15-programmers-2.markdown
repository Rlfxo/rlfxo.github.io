---
layout: post
title:  "[Programmers] 문자열 내 p와y의 개수"
date:   2022-06-15 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220615/220615_2Scr2.png)

Note <br>

~~~ c
#include <string>
#include <iostream>
using namespace std;

bool solution(string s)
{
    bool answer = true;
    int cntP = 0;
    int cntY = 0;
    
    for(int i=0; i<s.size(); i++){
        if(s[i] == 'p' || s[i] == 'P') cntP++;
        if(s[i] == 'y' || s[i] == 'Y') cntY++;
    }
    if(cntP != cntY) answer = false;

    return answer;
}
~~~

![Scr1](/img/220615/220615_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
