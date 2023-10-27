---
layout: post
title:  "[Programmers] 124 나라의 숫자"
date:   2022-07-12 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220712/220712_1Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(int n) {
    string answer = "";
    int res = 0;

    while(n != 0){
        res = n % 3;
        n /= 3;
        switch(res){
            case 0 :
                res = 4;
                n--;
                break;
            case 1 :
                res = 1;
                break;
            case 2 :
                res = 2;
                break;
        }
        answer = to_string(res) + answer;
    }
    
    return answer;
}
~~~

![Scr1](/img/220712/220712_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
