---
layout: post
title:  "[Programmers] 가장 큰 수"
date:   2022-07-09 10:23:56 +0900
categories: CodingTest Programmers
---

![Scr2](/img/220709/220709_1Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>
#include <algorithm>
#include <functional>

using namespace std;

string solution(vector<int> numbers) {
    string answer = "";

    sort(numbers.begin(), numbers.end(), greater<int>());

    for(int k=9; k>0; k--){
        for(int i=0; i<numbers.size(); i++){
            int num = 0;
            if(numbers[i] < 0) continue;

            if(numbers[i] > 999) num = numbers[i] / 1000;
            else if(numbers[i] > 99) num = numbers[i] / 100;
            else if(numbers[i] > 9) num = numbers[i] / 10;
            else num = numbers[i];

            if(num == k){
                string s = to_string(numbers[i]);
                numbers[i] = -1;
                answer += s;
            }
        }
    }

    return answer;
}
~~~

~~~ c
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

bool cmp(string a, string b) {
    return a + b > b + a;
}

string solution(vector<int> numbers) {
    string answer = "";
    vector<string> strings;

    for(int i=0; i<numbers.size(); i++){
        strings.push_back(to_string(numbers[i]));
    }

    sort(strings.begin(), strings.end(), cmp);

    if(strings.front() == "0") answer = "0";
    else{
        for(int i=0; i<strings.size(); i++){
            answer += strings[i];
        }
    }
    
    return answer;
}
~~~

![Scr1](/img/220709/220709_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
