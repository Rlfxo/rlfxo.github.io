---
layout: post
title:  "[Programmers] 행렬의 덧셈"
date:   2022-06-08 10:13:36 +0900
categories: CodingTest Vector
---

![Scr2](/img/220608/220608_2Scr2.png)

Note <br>
![noteImg](/img/220608/220608_2.PNG)


~~~ c
#include <string>
#include <vector>

using namespace std;

vector<vector<int>> solution(vector<vector<int>> arr1, vector<vector<int>> arr2) {
    
    for(int i=0; i<arr1.size(); i++){
        for(int j=0; j<arr1[i].size(); j++){
            arr1[i][j] += arr2[i][j];
        }
    }
    
    return arr1;
}
~~~

![Scr1](/img/220608/220608_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
