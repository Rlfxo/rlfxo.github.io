---
layout: post
title:  "[Programmers] 로또의 최고 순위와 최저 순위"
date:   2022-07-07 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220707/220707_2Scr2.png)
![Scr3](/img/220707/220707_2Scr3.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

vector<int> solution(vector<int> lottos, vector<int> win_nums) {
    vector<int> answer;
    int zero = 0;
    int cons = 0;
    
    for(int i=0; i<lottos.size(); i++){
        if(lottos[i] == 0){
            zero++;
            continue;
        }
        for(int j=0; j<win_nums.size(); j++){
            if(lottos[i] == win_nums[j]) cons++;
        }
    }
    int big = 7 - (zero + cons);
    if(big > 6) big = 6;
    answer.push_back(big);
    
    int small = 7 - cons;
    if(small > 6) small = 6;
    answer.push_back(small);
    
    return answer;
}
~~~

![Scr1](/img/220707/220707_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
