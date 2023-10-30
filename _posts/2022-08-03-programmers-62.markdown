---
layout: post
title:  "[Programmers] 문자열 압축"
date:   2022-08-03 10:23:56 +0900
categories: CodingTest Kakao
---

![Scr2](/img/220803/220803_1Scr2.png)

Note <br>

~~~ c

#include <string>
#include <vector>
#include <iostream>
#include <algorithm>

using namespace std;

int solution(string s) {
    int answer = s.size();

    for(int i=1; i<=s.size()/2; i++){
        string convert,temp;

        int cnt = 1;
        temp = s.substr(0,i);

        for(int j=i; j<s.size(); j+=i){
        if(temp == s.substr(j,i)) cnt++;
        else{
            if(cnt > 1) convert += to_string(cnt);
            convert += temp;
            temp=s.substr(j,i);
            cnt = 1;
            }
        }

        if(cnt>1) convert+=to_string(cnt);

        convert += temp;
        if(convert.size() < answer) answer = convert.size();
    }
    return answer;
}
~~~

![Scr1](/img/220803/220803_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
