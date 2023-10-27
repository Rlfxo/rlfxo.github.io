---
layout: post
title:  "[Programmers] 가장 큰 수 만들기"
date:   2022-07-09 10:23:56 +0900
categories: CodingTest Programmers
---

![Scr2](/img/220709/220709_2Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(string number, int k) {
    string answer = "";
    bool flag = true;

    for(int i=0; i<number.size(); i++){
        flag = true;
        for(int j=0; j<k+1; j++){
            if(number[i] < number[i+j]){
                k--;
                flag = false;
                break;
            }
        }
        if(flag) answer += number[i];
    }

    if(k > 0) answer = answer.substr(0, number.size() - k);

    return answer;
}
~~~

![Scr1](/img/220709/220709_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
