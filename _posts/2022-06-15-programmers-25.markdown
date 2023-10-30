---
layout: post
title:  "[Programmers] 문자열 내 마음대로 정렬하기"
date:   2022-06-15 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220615/220615_3Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int N = 0;
bool cmp(string a, string b){
    if(a[N] == b[N]){
        return a < b;
    }
    else{
        return a[N] < b[N];
    }
}

vector<string> solution(vector<string> strings, int n) {
    N = n;
    sort(strings.begin(), strings.end(), cmp);
    
    return strings;
}
~~~

![Scr1](/img/220615/220615_3Scr1.png)

***
* eMail : <yskl7137@gmail.com>
