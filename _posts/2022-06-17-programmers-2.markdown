---
layout: post
title:  "[Programmers] 비밀 지도"
date:   2022-06-17 10:23:56 +0900
categories: CodingTest Kakao
---

![Scr2](/img/220617/220617_2Scr2.png)
![Scr3](/img/220617/220617_2Scr3.png)
![Scr4](/img/220617/220617_2Scr4.png)

Note <br>
![Img](/img/220617/220617_2.PNG)

~~~ c
#include <string>
#include <vector>
#include <iostream>

using namespace std;

vector<string> solution(int n, vector<int> arr1, vector<int> arr2) {
    vector<string> answer;
    
    for(int i=0; i<n; i++){
        string s = "";
        arr1[i] = arr1[i] | arr2[i];
        
        for(int j=0; j<n; j++){
            if(arr1[i] % 2 == 0) s = " " + s;
            else s = "#" + s;
            arr1[i] >>= 1;
        }
        answer.push_back(s);
    }
    
    return answer;
}
~~~

![Scr1](/img/220617/220617_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
