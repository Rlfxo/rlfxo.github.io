---
layout: post
title:  "[Programmers] 키패드 누르기"
date:   2022-07-01 10:23:56 +0900
categories: CodingTest Kakao
---

![Scr2](/img/220705/220705_1Scr1.png)
![Scr3](/img/220705/220705_1Scr2.png)

Note <br>
![Img](/img/220705/220705_1.PNG)

~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(vector<int> numbers, string hand) {
    string answer = "";
    int leftNum = 10;
    int rightNum = 12;
    int temp = 0;
    
    for(int i=0; i<numbers.size(); i++){
        if(numbers[i] == 1 || numbers[i] == 4 || numbers[i] == 7){
            leftNum = numbers[i];
            answer += "L";
        }
        else if(numbers[i] == 3 || numbers[i] == 6 || numbers[i] == 9){
            rightNum = numbers[i];
            answer += "R";
        }
        else{
            int leftCost = 0;
            int rightCost = 0;
            
            if(numbers[i] == 0) numbers[i] = 11;
            if(leftNum == 1 || leftNum == 4 || leftNum == 7 || leftNum == 10){
                leftCost++;
                leftNum++;
            }
            temp = (leftNum - numbers[i])/3;
            leftCost += abs(temp);
            
            if(rightNum == 3 || rightNum == 6 || rightNum == 9 || rightNum == 12){
                rightCost++;
                rightNum--;
            }
            temp = (rightNum - numbers[i])/3;
            rightCost += abs(temp);
            
            if(leftCost == rightCost){
                if(hand == "left"){
                    answer += "L";
                    leftNum = numbers[i];
                }
                else {
                    answer += "R";
                    rightNum = numbers[i];
                }
            }else if(leftCost < rightCost){
                answer += "L";
                leftNum = numbers[i];
            }else{
                answer += "R";
                rightNum = numbers[i];
            }
        }
    }
    return answer;
}

~~~
//실패하는 경우 거리 계산 공식 아해 적용시 해결//
~~~ c

int tmp_l = abs(leftHand - numbers[i]);
int tmp_r = abs(rightHand - numbers[i]);

leftDist = (tmp_l / 3) + (tmp_l % 3);
rightDist = (tmp_r / 3) + (tmp_r % 3);

~~~

![Scr1](/img/220705/220705_1Scr3.png)

***
* eMail : <yskl7137@gmail.com>
