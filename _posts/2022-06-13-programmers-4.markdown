---
layout: post
title:  "[Programmers] 소수 찾기"
date:   2022-06-14 10:23:56 +0900
categories: CodingTest
---

![Scr2](/img/220613/220613_4Scr2.png)

Note <br>
![noteImg](/img/220613/220613_4.PNG)

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    
    for(int i=1; i<n+1; i++){
        if(i == 1) continue;
        int cnt = 0;
        for(int j=1; j<i+1; j++){
            if(i%j == 0) cnt++;
        }
        if(cnt == 2) answer++;
    }
    
    return answer;
}
~~~
-최적화 오류
~~~ c
#include <string>
#include <cstring>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    bool eratos[n+1];
    memset(eratos,false,sizeof(eratos));
    
    for(int i=2; i<=n; i++){
        if(!eratos[i]) answer++;
        
        for(int j=i; j<=n; j+=i){
            eratos[j] = true;
        }
    }
    
    return answer;
}
~~~
-에라토스의 체 적용

![Scr1](/img/220613/220613_4Scr1.png)

***
* eMail : <yskl7137@gmail.com>
