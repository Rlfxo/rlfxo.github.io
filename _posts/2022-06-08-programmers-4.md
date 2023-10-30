---
title: (Programmers) 핸드폰 번호 가리기
author: Rlfxo
date:  2022-06-08 12:53:26 +0900
categories: [Blog, CodingTest]
tags: [String]
pin: false
# render_with_liquid: false
---

![Scr2](/img/220608/220608_3Scr2.png)

Note <br>
![noteImg](/img/220608/220608_3.PNG)


~~~ c
#include <string>
#include <vector>

using namespace std;

string solution(string phone_number) {
    string answer = "";
    for(int i=0; i<phone_number.size(); i++){
        if(phone_number.size()-i > 4){
            answer += "*";
        }else{
            answer += phone_number[i];
        }
    }
    return answer;
}
~~~

![Scr1](/img/220608/220608_3Scr1.png)

***
* eMail : <yskl7137@gmail.com>
