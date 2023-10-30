---
layout: post
title:  "[Programmers] 숫자 문자열과 영단어"
date:   2022-08-02 10:23:56 +0900
categories: CodingTest Kakao Regex
---

![Scr2](/img/220802/220802_2Scr2.png)

Note <br>

~~~ c

#include <string>
#include <vector>

using namespace std;

int answer = 0;

void add(int number){
    answer = answer*10 + number;
}

int solution(string s) {
    
    for(int i=0; i<s.size(); ){
        if(s[i] == 'z'){
            add(0);
            i += 4;
        }else if(s[i] == 'o'){
            add(1);
            i += 3;
        }else if(s[i] == 't'){
            if(s[i+1] == 'w'){
                add(2);
                i += 3;
            }else{
                add(3);
                i += 5;
            }
        }else if(s[i] == 'f'){
            if(s[i+1] == 'o'){
                add(4);
                i += 4;
            }else{
                add(5);
                i += 4;
            }
        }else if(s[i] == 's'){
            if(s[i+1] == 'i'){
                add(6);
                i += 3;
            }else{
                add(7);
                i += 5;
            }
        }else if(s[i] == 'e'){
            add(8);
            i += 5;
        }else if(s[i] == 'n'){
            add(9);
            i += 4;
        }else{
            int num = s[i] - '0';
            add(num);
            i++;
        }
    }
        
    return answer;
}

#include <string>
#include <vector>
#include <algorithm>
#include <regex>

using namespace std;

vector<string> numbers = {"zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten"};

int solution(string s) {
    int answer = 0;
    regex r;
    for(int i = 0; i < numbers.size(); i++) {
        r = numbers[i];
        s = regex_replace(s, r, to_string(i));
    }
    answer = stoi(s);
    return answer;
}

~~~

![Scr1](/img/220802/220802_2Scr1.png)

***
* eMail : <yskl7137@gmail.com>
