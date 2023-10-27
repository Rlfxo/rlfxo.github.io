---
layout: post
title:  "[Programmers] 자연수 뒤집어 배열로 만들기"
date:   2022-06-10 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220610/220610_4Scr2.png)

Note <br>
![noteImg](/img/220610/220610_4.PNG)

~~~ c
#include <string>
#include <vector>

using namespace std;

vector<int> solution(long long n) {
    vector<int> answer;
    
    while(n != 0){
        answer.push_back(n%10);
        n /= 10;
    }
    
    return answer;
}
~~~

![Scr1](/img/220610/220610_4Scr1.png)

***
* eMail : <yskl7137@gmail.com>
