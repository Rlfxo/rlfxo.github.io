---
layout: post
title:  "[Programmers] 약수의 개수와 덧셈"
date:   2022-06-27 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220627/220627_5Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(int left, int right) {
    int answer = 0;
    int count = 0;
    
    for(int i=left; i<=right; i++){
        count = (i == 1) ? 1:2;
        for(int j=2; j<=i/2; j++){
            if(i % j == 0) count++;
        }
        answer += (count % 2 == 0) ? i : -i;
    }
    
    return answer;
}
~~~

![Scr1](/img/220627/220627_5Scr1.png)

***
* eMail : <yskl7137@gmail.com>
