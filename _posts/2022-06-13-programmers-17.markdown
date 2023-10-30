---
layout: post
title:  "[Programmers] 시저 암호"
date:   2022-06-13 10:23:56 +0900
categories: CodingTest String
---

![Scr2](/img/220613/220613_1Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(string s, int n) {
    string answer = "";
    
    for(int i=0; i<s.size(); i++){
        if(s[i]>='A' && s[i]<='Z'){
            s[i]+n > 'Z' ? s[i] += n -'Z'+'A'-1 : s[i] += n;
        }
        
        else if(s[i]>='a' && s[i]<='z'){
            s[i]+n > 'z' ? s[i] += n -'z'+'a'-1 : s[i] += n;
        }
    }
    answer = s;
    
    return answer;
}
~~~

![Scr1](/img/220613/220613_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
