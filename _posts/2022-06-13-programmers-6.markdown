---
layout: post
title:  "[Programmers] 문자열 다루기 기본"
date:   2022-06-13 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220613/220613_6Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

bool solution(string s) {
    bool answer = true;
    
    if(s.size() != 4 && s.size() != 6) return false;
    
    for(int i=0; i<s.size(); i++){
        if(s[i] <= 47 || s[i] >= 58) answer = false;
    }
 
    return answer;
}
~~~

![Scr1](/img/220613/220613_6Scr1.png)

***
* eMail : <yskl7137@gmail.com>
