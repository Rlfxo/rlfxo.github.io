---
layout: post
title:  "[Programmers] 더 맵게"
date:   2022-07-20 10:23:56 +0900
categories: CodingTest PriorityQueue
---

![Scr2](/img/220720/220720_1Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int solution(vector<int> scoville, int K) {
    int answer = 0;
    
    while(1){
        if(scoville.size() <= 1){
            answer = -1;
            break;
        }
        sort(scoville.begin(), scoville.end());
        
        int check = 0;
        for(int i=0; i<scoville.size(); i++){
            if(scoville[i] >= K) check++;
        }
        if(check == scoville.size()) break;
        
        int first = scoville[0];
        int second = scoville[1];
        
        scoville[1] = first + (second * 2);
        scoville.erase(scoville.begin());
        answer++;
    }
    
    return answer;
}

//효율성 실패후 수정//

#include <string>
#include <vector>
#include <queue>

using namespace std;

int solution(vector<int> scoville, int K) {
    int answer = 0;
    priority_queue<int, vector<int>, greater<int>> q;
    for(auto v: scoville) q.push(v);
    
    while(q.size() > 1 && q.top() < K){
        answer++;
        int small = q.top();
        q.pop();
        
        int mix = small + (2*q.top());
        q.pop();
        
        q.push(mix);
    }if(q.top() < K) return -1;
    
    return answer;
}
~~~

![Scr1](/img/220720/220720_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
