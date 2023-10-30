---
layout: post
title:  "[Programmers] 부족한 금액 계산하기"
date:   2022-06-18 11:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220618/220618_1Scr2.png)

Note <br>
![Img](/img/220618/220618_1.PNG)

~~~ c
using namespace std;

long long solution(int price, int money, int count)
{
    long long answer = 0;
    
    for(int i=1; i<count+1; i++) answer += i*price;
    
    answer -= money;
    if(answer < 0) answer = 0;

    return answer;
}
~~~

![Scr1](/img/220618/220618_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
