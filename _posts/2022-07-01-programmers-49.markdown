---
layout: post
title:  "[Programmers] 없는 숫자 더하기"
date:   2022-07-01 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220701/220701_4Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(vector<int> numbers) {
    int answer = 0;
    
    for(int i=0; i<10; i++) answer += i;
    for(int i=0; i<numbers.size(); i++) answer -= numbers[i];
    
    return answer;
}
~~~

![Scr1](/img/220701/220701_4Scr1.png)

***
* eMail : <yskl7137@gmail.com>
