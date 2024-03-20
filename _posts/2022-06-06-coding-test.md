---
title: unordered_map
author: Rlfxo
date: 2022-06-06 16:23:34 +0900
categories: [CodingTest]
tags: [HASH]
pin: false
# render_with_liquid: false
---

Note <br>
![noteImg](/img/220606/220606.PNG)


~~~ c
//std::map - binary search tree
//std::unordered_map - hash table
#include <string>
#include <vector>
#include <unordered_map>

using namespace std;

string solution(vector<sting> participant, vector<sting> completion) {
    string answer = "";

    unordered_map<string, int> d;
    for (auto& i : participant) d[i]++;
    for (auto& i : completion) d[i]--;
    for (auto& i : d){
        if(i.second > 0){
            answer = i.first;
            break;
        }
    }
    return answer;
}
~~~

***
* eMail : <yskl7137@gmail.com>
