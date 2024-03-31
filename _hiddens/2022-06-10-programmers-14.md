---
title: (Programmers) 자릿수 더하기
author: Rlfxo
date:  2022-06-10 10:23:56 +0900
categories: [CodingTest]
tags: [STRING]
pin: false
# render_with_liquid: false
---

![Scr2](/img/220610/220610_5Scr2.png)

Note <br>

~~~ c
#include <iostream>

using namespace std;
int solution(int n)
{
    int answer = 0;

    while(n != 0){
        answer += n%10;
        n /= 10;
    }

    return answer;
}
~~~

![Scr1](/img/220610/220610_5Scr1.png)

***
* eMail : <yskl7137@gmail.com>
