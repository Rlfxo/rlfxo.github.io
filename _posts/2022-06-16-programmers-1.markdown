---
layout: post
title:  "[Programmers] 같은 숫자는 싫어"
date:   2022-06-16 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220616/220616_1Scr2.png)

Note <br>

~~~ c
#include <vector>
#include <iostream>

using namespace std;

vector<int> solution(vector<int> arr) 
{
    vector<int> answer;
    int num = -1;

    for(int i=0; i<arr.size(); i++){
        if(arr[i] != num){
            num = arr[i];
            answer.push_back(arr[i]);
        }
    }

    return answer;
}
~~~

![Scr1](/img/220616/220616_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
