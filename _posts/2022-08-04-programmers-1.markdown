---
layout: post
title:  "[Programmers] 컬러링북"
date:   2022-08-03 10:23:56 +0900
categories: CodingTest Kakao Bfs
---

![Scr2](/img/220804/220804_1Scr2.png)
![Scr3](/img/220804/220804_1Scr3.png)

Note <br>
![note1](/img/220804/220804_1.PNG)

~~~ c
#include <vector>
#include <queue>

using namespace std;


vector<int> solution(int m, int n, vector<vector<int>> picture) {
    int number_of_area = 0;
    int max_size_of_one_area = 0;
    
    int max_x = picture[0].size();
    int max_y = picture.size();
    
    int check[101][101] = {0,};
    int dir[4][2] = {0,1},{0,-1},{1,0},{-1,0};
    int num = 0;
    queue <pair<int,int>> q;
    
    for(int i=0; i<max_y; i++){
        for(int j=0; j<max_x; j++){
            if(check[i][j] == 0 && picture[i][j] != 0){
                q.push(make_pair(i,j));
                check[i][j] = 1;
                num = 1;
                number_of_area++;
                while(!q.empty()){
                    auto tmp = q.front();
                    q.pop();
                    for(int k=0; k<4; k++){
                        int di = tmp.first + dir[k][0];
                        int dj = tmp.second + dir[k][1];
                        if(dj < 0 || di < 0 || dj >= max_x || di >= max_y) continue;
                        if(check[di][dj] == 0 && picture[di][dj] == picture[i][j]){
                            q.push(make_pair(di,dj));
                            num++;
                            check[di][dj] = 1;
                        }
                    }
                }
                if(num > max_size_of_one_area) max_size_of_one_area = num;
            }
        }
    }
    
    vector<int> answer(2);
    answer[0] = number_of_area;
    answer[1] = max_size_of_one_area;
    return answer;
}
~~~

![Scr1](/img/220804/220804_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
