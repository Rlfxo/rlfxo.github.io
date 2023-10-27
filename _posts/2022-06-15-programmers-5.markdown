---
layout: post
title:  "[Programmers] 나누어 떨어지는 숫자 배열"
date:   2022-06-15 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220615/220615_5Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(vector<int> arr, int divisor) {
    vector<int> answer;
    int cnt = 0;
    
    for(int i=0; i<arr.size(); i++){
        if(arr[i] % divisor == 0){
            answer.push_back(arr[i]);
            cnt++;
        }
    }
    if(cnt == 0) answer.push_back(-1);
    sort(answer.begin(), answer.end());
    
    return answer;
}
~~~

![Scr1](/img/220615/220615_5Scr1.png)

***
* eMail : <yskl7137@gmail.com>
