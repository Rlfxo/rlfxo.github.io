---
layout: post
title:  "[Programmers] 폰켓몬"
date:   2022-06-29 11:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220629/220629_1Scr2.png)

Note <br>
![Img](/img/220629/220629_1.PNG)

~~~ c
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<int> nums)
{
    int answer = 0;
    int num = 0;
    
    sort(nums.begin(), nums.end());
    for(int i=0; i<nums.size(); i++){
        if(nums[i] != num){
            answer++;
            num = nums[i];
        }
    }
    if(answer > nums.size()/2) answer = nums.size()/2;
    
    return answer;
}
~~~

![Scr1](/img/220629/220629_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
