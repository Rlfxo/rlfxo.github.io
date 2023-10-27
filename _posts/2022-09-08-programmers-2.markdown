---
layout: post
title:  "[Programmers] 최댓값과 최솟값"
date:   2022-09-08 10:23:56 +0900
categories: CodingTest String
---

![Scr2](/img/220908/220908_2Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <sstream>
#include <algorithm>

using namespace std;

string solution(string s) {
    string answer = "";
    string sw;
    vector<int> v;
    
    stringstream ss(s);
    while(ss >> sw) v.push_back(stoi(sw));
    sort(v.begin(), v.end());
    
    answer = to_string(v.front()) + " " + to_string(v.back());
    return answer;
}
~~~

![Scr1](/img/220908/220908_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
