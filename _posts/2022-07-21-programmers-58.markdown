---
layout: post
title:  "[Programmers] N으로 표현"
date:   2022-07-21 10:23:56 +0900
categories: CodingTest DP
---

![Scr2](/img/220721/220721_1Scr2.png)

Note <br>

~~~ c

#include <string>
#include <vector>
#include <unordered_set>

using namespace std;

int solution(int N, int number) {
    int answer = 0;
    int sum = 0;
    unordered_set <int> s[8];
    
    for(int i=0; i<8; i++){
        sum = 10 * sum + N;
        s[i].insert(sum);
    }
    
    for (int i=1; i<8; i++){
        for(int j=0; j<i; j++){
            for(auto a : s[j]){
                for(auto b : s[i - j - 1]){
                    s[i].insert(a + b);
                    s[i].insert(a - b);
                    s[i].insert(a * b);
                    if(b != 0) s[i].insert(a / b);
                }
            }
        }
    }
    
    for(int i=0; i<8; i++){
        if(s[i].find(number) != s[i].end()){
            answer = i + 1;
            break;
        }  
    }
    if(!answer) answer = -1;
    
    return answer;
}

~~~

![Scr1](/img/220721/220721_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
