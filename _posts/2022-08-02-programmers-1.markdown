---
layout: post
title:  "[Programmers] 신규 아이디 추천"
date:   2022-08-02 10:23:56 +0900
categories: CodingTest Kakao String
---

![Scr2](/img/220802/220802_1Scr2.png)

Note <br>

~~~ c

#include <string>
#include <vector>

using namespace std;

string solution(string new_id) {
    
    for(int i=0; i<new_id.length(); i++)
        if (new_id[i] >= 'A' && new_id[i] <= 'Z') 
            new_id[i] = tolower(new_id[i]);
    
    for(int i=0; i<new_id.length(); ) {
        if ((new_id[i] >= 'a' && new_id[i] <= 'z') || (new_id[i] >= '0' && new_id[i] <= '9') 
            || new_id[i] == '-' || new_id[i] == '_' || new_id[i] == '.'){
            i++;
            continue;
        }else{
            new_id.erase(new_id.begin() + i);
        }
    }
    
    for(int i=1; i<new_id.length(); ){
        if (new_id[i] == '.' && new_id[i - 1] == '.'){
            new_id.erase(new_id.begin() + i);
            continue;
        }
        else i++;
    }
    
    if (new_id.front() == '.') new_id.erase(new_id.begin());
    if (new_id.back() == '.') new_id.erase(new_id.end() - 1);
    
    if (new_id.length() == 0) new_id = "a";
    
    if (new_id.length() >= 16){
        while(new_id.length() != 15){
            new_id.erase(new_id.begin() + 15);
        }
    }
    if (new_id.back() == '.') new_id.erase(new_id.end() - 1);
    
    if (new_id.length() <= 2){
        while(new_id.length() != 3){
            new_id += new_id.back();
        }
    }
    
    
    return new_id;
}

~~~

![Scr1](/img/220802/220802_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
