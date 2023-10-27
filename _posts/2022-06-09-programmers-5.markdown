---
layout: post
title:  "[Programmers] 짝수와 홀수"
date:   2022-06-09 16:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220609/220609_5Scr2.png)

~~Note <br>~~


~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(int num) {
    string answer = "";
    
    num % 2 ? answer = "Odd" : answer = "Even";
    
    return answer;
}
~~~

![Scr1](/img/220609/220609_5Scr1.png)

***
* eMail : <yskl7137@gmail.com>
