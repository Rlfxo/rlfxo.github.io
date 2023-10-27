---
layout: post
title:  "[Programmers] JadenCase 문자열 만들기"
date:   2022-09-08 10:23:56 +0900
categories: CodingTest String
---

![Scr2](/img/220908/220908_3Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    string answer = "";
    
    answer += toupper(s[0]);
    for(int i=1; i<s.size(); i++){
        if(s[i-1] == ' '){
            answer += toupper(s[i]);
        }else{
            answer += tolower(s[i]);
        }
    }
    
    return answer;
}
~~~

![Scr1](/img/220908/220908_3Scr1.png)

***
* eMail : <yskl7137@gmail.com>
