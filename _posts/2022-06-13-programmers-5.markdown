---
layout: post
title:  "[Programmers] 서울에서 김서방 찾기"
date:   2022-06-13 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220613/220613_5Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(vector<string> seoul) {
    string answer = "김서방은 ";
    
    for(int i=0; i<seoul.size(); i++)
        if(seoul[i] == "Kim"){
            answer += to_string(i);
            break;
        }
    
    return answer + "에 있다";
}
~~~

![Scr1](/img/220613/220613_5Scr1.png)

***
* eMail : <yskl7137@gmail.com>
