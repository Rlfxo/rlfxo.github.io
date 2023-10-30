---
layout: post
title:  "[Programmers] 소수 만들기"
date:   2022-07-01 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220701/220701_1Scr2.png)

Note <br>

~~~ c
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

int solution(vector<int> nums) {
    int answer = 0;
    vector<int> v;
    
    for(int i=0; i<nums.size(); i++){
        for(int j=i+1; j<nums.size(); j++){
            for(int k=j+1; k<nums.size(); k++){
                v.push_back(nums[i]+nums[j]+nums[k]); 
            }
        }
    }
    sort(v.begin(), v.end());
    
    for(int i=0; i<v.size(); i++){
        bool flag = true;
        for(int j=2; j<v[i]; j++){
            if(v[i] % j == 0)flag = false;
        }
        if(flag) answer++;
    }

    return answer;
}
~~~

![Scr1](/img/220701/220701_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
