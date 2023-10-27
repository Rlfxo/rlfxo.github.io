---
layout: post
title:  "[Programmers] 이상한 문자 만들기"
date:   2022-06-10 10:23:56 +0900
categories: CodingTest String
---

![Scr2](/img/220610/220610_6Scr2.png)

Note <br>
![noteImg](/img/220610/220610_6.PNG)

~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    string answer = "";
    int Big = 1;
    
    for(int i=0; i<s.size(); i++){
        if(s[i] == ' '){
            answer += toupper(s[i]);
            Big = 1;
            continue;
        }
        if(Big == 1){
            answer += toupper(s[i]);
            Big *= -1;
        }else{
            answer += tolower(s[i]);
            Big *= -1;
        }
    }
    
    return answer;
}
~~~

![Scr1](/img/220610/220610_6Scr1.png)

***
* eMail : <yskl7137@gmail.com>
