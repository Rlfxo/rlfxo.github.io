---
title: (Programmers) 약수의 합
author: Rlfxo
date:  2022-06-10 10:23:56 +0900
categories: [CodingTest]
tags: [None]
pin: false
# render_with_liquid: false
---

![Scr2](/img/220611/220611_Scr2.png)

Note <br>

~~~ c
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
     int answer = 0;
    
    for(int i=1; i <=n; i++){
        if(n%i == 0)
            answer +=i;
    }
    return answer;
}
~~~

![Scr1](/img/220611/220611_Scr1.png)

***
* eMail : <yskl7137@gmail.com>
