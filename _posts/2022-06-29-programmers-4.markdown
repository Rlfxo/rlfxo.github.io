---
layout: post
title:  "[Programmers] K번째 수"
date:   2022-06-29 11:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220629/220629_4Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(vector<int> array, vector<vector<int>> commands) {
    vector<int> answer;
    vector<int> temp;
    
    for(int i=0; i<commands.size(); i++){
        for(int j=commands[i][0]-1; j<commands[i][1]; j++){
            temp.push_back(array[j]);
        }
        sort(temp.begin(), temp.end());
        answer.push_back(temp[commands[i][2]-1]);
        temp.clear();
    }
    
    return answer;
}
~~~

![Scr1](/img/220629/220629_4Scr1.png)

***
* eMail : <yskl7137@gmail.com>
