---
layout: post
title:  "[Programmers] 오픈채팅방"
date:   2022-08-03 10:23:56 +0900
categories: CodingTest Kakao Unordered_map
---

![Scr2](/img/220803/220803_2Scr2.png)
![Scr3](/img/220803/220803_2Scr3.png)

Note <br>

~~~ c

#include <string>
#include <vector>
#include <unordered_map>

using namespace std;

vector<string> solution(vector<string> record) {
    vector<string> answer;
    vector<pair<string, string>> log;
    unordered_map<string, string> id;
    
    for(auto s: record){
        string cmd1, cmd2, cmd3;
        cmd1 = s.substr(0,s.find(" "));
        cmd2 = s.substr(s.find(" ")+1, s.length());
        
        if(cmd1 == "Enter" || cmd1 == "Change"){
            cmd3 = cmd2.substr(cmd2.find(" ")+1, cmd2.length());
            cmd2 = cmd2.substr(0,cmd2.find(" "));
            if(cmd1 == "Enter"){
                log.push_back(make_pair(cmd2,cmd1));
                id[cmd2] = cmd3;
            }else{//Change
                id[cmd2] = cmd3;
            }
        }else{//Leave
            log.push_back(make_pair(cmd2,cmd1));
        }
    }
    
    for(auto d: id){
        for(int i=0; i<log.size(); i++){
            if(log[i].first == d.first) log[i].first = d.second;
        }
    }
    
    for(auto& l: log){
        string s = "";
        if(l.second == "Enter"){
            s = l.first + "님이 들어왔습니다.";
        }else{
            s = l.first + "님이 나갔습니다.";
        }
        answer.push_back(s);
    }
    
    return answer;
}

//////////////53.2////////////////

#include <string>
#include <vector>
#include <unordered_map>

using namespace std;

vector<string> solution(vector<string> record) {
    vector<string> answer;
    vector<pair<string, string>> log;
    unordered_map<string, string> id;
    
    for(auto s: record){
        vector<string> AIN;
        int start = 0;
        
        for(int i=0; i<s.length(); i++){
            if(s[i] == ' '){
                AIN.push_back(s.substr(start,i-start));
                start = i+1;
            }
        }
        if(AIN[0] != "Leave") id[AIN[1]] = s.substr(start);
        else AIN.push_back(s.substr(start));
        
        log.push_back({AIN[0],AIN[1]});
    }
    
    
    for(auto l: log){
        string action = l.first;
        string user = l.second;
        if(action == "Enter"){
            answer.push_back(id[user] + "님이 들어왔습니다.");
        }else if(action == "Leave"){
            answer.push_back(id[user] + "님이 나갔습니다.");
        }
    }
    
    return answer;
}

~~~

![Scr1](/img/220803/220803_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
