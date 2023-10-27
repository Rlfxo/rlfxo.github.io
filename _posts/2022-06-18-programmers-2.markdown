---
layout: post
title:  "[Programmers] 나머지가 1이 되는 수 찾기"
date:   2022-06-18 11:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220618/220618_2Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    
    for(int i=1; i<n+1; i++){
        if(n % i == 1){
            answer = i;
            break;
        }
    }
    
    return answer;
}
~~~

![Scr1](/img/220618/220618_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
