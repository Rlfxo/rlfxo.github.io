---
layout: post
title:  "[Programmers] 크레인 인형뽑기 게임"
date:   2022-07-01 10:23:56 +0900
categories: CodingTest Kakao
---

![Scr2](/img/220701/220701_5Scr2.png)
![Scr3](/img/220701/220701_5Scr3.png)
![Scr4](/img/220701/220701_5Scr4.png)

Note <br>
![Img](/img/220701/220701_5.PNG)

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(vector<vector<int>> board, vector<int> moves) {
    int answer = 0;
    vector<int> v;
    
    for(int i=0; i<moves.size(); i++){
        for(int j=0; j<board[0].size(); j++){
            int check = moves[i]-1;
            if(board[j][check] != 0){
                if(!v.empty()){
                    if(v.back() == board[j][check]){
                        v.pop_back();
                        answer+=2;
                    }else{
                        v.push_back(board[j][check]);
                    }
                }else{
                    v.push_back(board[j][check]);
                }
                board[j][check] = 0;
                break;
            }
        }
    }
    return answer;
}
~~~

![Scr1](/img/220701/220701_5Scr1.png)

***
* eMail : <yskl7137@gmail.com>
