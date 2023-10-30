---
layout: post
title:  "[Programmers] 다트 게임"
date:   2022-06-17 10:23:56 +0900
categories: CodingTest Kakao
---

![Scr2](/img/220617/220617_1Scr2.png)
![Scr3](/img/220617/220617_1Scr3.png)

Note <br>
![Img](/img/220617/220617_1.PNG)

~~~ c
#include <string>

using namespace std;

int solution(string dartResult) {
    int answer = 0;
    int score[3] = {0,0,0};
    int maxIndex = dartResult.size();
    int index = -1;
    
    for(int i=0; i<maxIndex; i++){
        if(dartResult[i] >= '0' && dartResult[i] <= '9'){
            index++;
            if(dartResult[i] == '1'){
                if(dartResult[i+1] == '0'){
                    score[index] = 10;
                    i++;
                }else score[index] = 1;
            }else score[index] = dartResult[i] - '0';
        }
        else{
            if(dartResult[i] == 'S' || dartResult[i] == 'D' || dartResult[i] == 'T'){
                if(dartResult[i] == 'D'){
                    score[index] = score[index] * score[index];
                }else if(dartResult[i] == 'T'){
                    score[index] = score[index] * score[index] * score[index];
                }
            }
            else{
                if(dartResult[i] == '#'){
                    score[index] *= -1;
                }else if(dartResult[i] == '*'){
                    score[index] *= 2;
                    if(index > 0) score[index-1] *= 2;
                }
            }
        }
    }
    
    for(int i=0; i<3; i++) answer += score[i];
    return answer;
}
~~~

![Scr1](/img/220617/220617_1Scr1.png)

***
* eMail : <yskl7137@gmail.com>
