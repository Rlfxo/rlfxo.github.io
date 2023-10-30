---
layout: post
title:  "[Programmers] 최소직사각형"
date:   2022-06-18 11:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220618/220618_3Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(vector<vector<int>> sizes) {
    int answer = 0;
    int wMax = 0;
    int hMax = 0;
    
    for(int i=0; i<sizes.size(); i++){
        if(sizes[i][0] < sizes[i][1]){
            int temp = sizes[i][0];
            sizes[i][0] = sizes[i][1];
            sizes[i][1] = temp;
        }
    }
    
    for(int i=0; i<sizes.size(); i++){
        if(sizes[i][0] > wMax) wMax = sizes[i][0];
        if(sizes[i][1] > hMax) hMax = sizes[i][1];
    }
    
    answer = wMax * hMax;
    return answer;
}
~~~

![Scr1](/img/220618/220618_3Scr1.png)

***
* eMail : <yskl7137@gmail.com>
