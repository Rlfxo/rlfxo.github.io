---
layout: post
title:  "[Programmers] 두 개 뽑아서 더하기"
date:   2022-06-27 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220627/220627_2Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(vector<int> numbers) {
    vector<int> answer;
    
    for(int i=0; i<numbers.size(); i++){
        for(int j=i+1; j<numbers.size(); j++){
            answer.push_back(numbers[i]+numbers[j]);
        }
    }
    sort(answer.begin(), answer.end());
    answer.erase(unique(answer.begin(), answer.end()), answer.end());
    
    return answer;
}
~~~

![Scr1](/img/220627/220627_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
