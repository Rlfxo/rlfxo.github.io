---
layout: post
title:  "[Programmers] 최대공약수와 최소공배수"
date:   2022-06-09 12:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220609/220609_4Scr2.png)

Note <br>
![noteImg](/img/220609/220609_4.PNG)


~~~ c
#include <string>
#include <vector>

using namespace std;

vector<int> solution(int n, int m) {
    vector<int> answer;
    int r = 0;
    int e = n * m;
    
    while (m != 0) {
        r = n % m;
        n = m;
        m = r;
    }
    
    answer.push_back(n);
    answer.push_back(e/n);
    
    return answer;
}
~~~

![Scr1](/img/220609/220609_4Scr1.png)

***
* eMail : <yskl7137@gmail.com>
