---
layout: post
title:  "[Programmers] 여행경로"
date:   2022-07-22 10:23:56 +0900
categories: CodingTest DFS
---

![Scr2](/img/220722/220722_1Scr2.png)

Note <br>

~~~ c

#include <string>
#include <vector>
#include <iostream>
#include <algorithm>

using namespace std;
vector<string> answer;
bool visited[10001] = {false, };
int max_count = 0;

void dfs(vector<vector<string>> tickets, vector<string> tmp, string start, int count){
    tmp.push_back(start);
    
    if(max_count < count){
        max_count = count;
        answer = tmp;
    }
    
    for(int i=0; i<tickets.size(); i++){
        if(tickets[i][0] == start && visited[i] == false){
            visited[i] = true;
            dfs(tickets, tmp, tickets[i][1], count+1);
            visited[i] = false;
        }
    }
    tmp.pop_back();
}

vector<string> solution(vector<vector<string>> tickets) {
    vector<string> tmp;
    sort(tickets.begin(), tickets.end());
    
    dfs(tickets, tmp, "ICN", 0);
    
    return answer;
}return answer;

~~~

![Scr1](/img/220722/220722_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
