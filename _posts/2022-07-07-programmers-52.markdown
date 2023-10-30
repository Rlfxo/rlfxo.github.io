---
layout: post
title:  "[Programmers] 신고 결과 받기"
date:   2022-07-07 10:23:56 +0900
categories: CodingTest Kakao
---

![Scr2](/img/220707/220707_1Scr2.png)
![Scr3](/img/220707/220707_1Scr3.png)

Note <br>
![Img](/img/220707/220707_1.PNG)

~~~ c
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(vector<string> id_list, vector<string> report, int k) {
    vector<int> answer;
    vector<pair<string, int>> check;
    vector<pair<string, int>> mail;
    
    for(int i=0; i<id_list.size(); i++)
        mail.push_back(make_pair(id_list[i], 0));
    
    for(int i=0; i<id_list.size(); i++)
        check.push_back(make_pair(id_list[i], 0));
    
    sort(report.begin(), report.end());
    report.erase(unique(report.begin(),report.end()), report.end());
    
    for(int i=0; i<report.size(); i++){
        string ban;
        ban = report[i].substr(report[i].find(" ")+1,report[i].length());
        
        for(int j=0; j<check.size(); j++){
            if(check[j].first == ban) check[j].second ++;
        }
    }
    
    for(int i=0; i<report.size(); i++){
        string user;
        string ban;
        
        user = report[i].substr(0,report[i].find(" "));
        ban = report[i].substr(report[i].find(" ")+1,report[i].length());
        
        for(int j=0; j<check.size(); j++){
            if(check[j].first == ban){
                if(check[j].second >= k){
                    for(int l=0; l<mail.size(); l++){
                        if(mail[l].first == user) mail[l].second++;
                    }
                }
            }
        }
    }
    
    for(int l=0; l<mail.size(); l++){
        answer.push_back(mail[l].second);
    }
    
    return answer;
}
~~~

![Scr1](/img/220707/220707_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
