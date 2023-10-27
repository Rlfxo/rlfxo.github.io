---
layout: post
title:  "[Programmers] 가운데 글자 가져오기"
date:   2022-06-16 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220616/220616_2Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    string answer = "";
    
    if(s.size()%2 == 0){
        answer = s[(s.size()/2)-1];
        answer += s[s.size()/2];
    }else answer = s[(s.size()/2)];
    
    return answer;
}
~~~

![Scr1](/img/220616/220616_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
