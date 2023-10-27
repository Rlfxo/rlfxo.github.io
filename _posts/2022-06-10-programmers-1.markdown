---
layout: post
title:  "[Programmers] 제일 작은 수 제거하기"
date:   2022-06-10 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220610/220610_1Scr2.png)

Note <br>
![noteImg](/img/220610/220610_1.PNG)

~~~ c
#include <string>
#include <vector>

using namespace std;

vector<int> solution(vector<int> arr) {
    vector<int> answer;
    int small = 0;
    
    for(int i=0; i<arr.size(); i++){
        if(i == 0) small = arr[i];
        else{
            if(small > arr[i]) small = arr[i];
        }
    }
    
    for(int i=0; i<arr.size(); i++){
        if(arr[i] == small) continue;
        answer.push_back(arr[i]);
    }
    
    if(answer.size() < 1) answer.push_back(-1);
    
    return answer;
}
~~~

![Scr1](/img/220610/220610_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
