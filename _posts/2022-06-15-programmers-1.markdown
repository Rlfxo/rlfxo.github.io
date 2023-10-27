---
layout: post
title:  "[Programmers] 문자열 내림차순으로 배치하기"
date:   2022-06-15 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220615/220615_1Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

string solution(string s) {

    sort(s.rbegin(), s.rend());

    return s;
}
~~~

![Scr1](/img/220615/220615_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
