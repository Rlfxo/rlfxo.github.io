---
layout: post
title:  "[Programmers] 3진법 뒤집기"
date:   2022-06-27 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220627/220627_4Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    int k = 1;
    vector<int> v;
    
    while(n > 0){
        v.push_back(n%3);
        n/=3;
    }
    while(!v.empty()){
        answer += k*v.back();
        v.pop_back();
        k *= 3;
    }
    
    return answer;
}
~~~

![Scr1](/img/220627/220627_4Scr1.png)

***
* eMail : <yskl7137@gmail.com>
