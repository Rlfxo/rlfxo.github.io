---
layout: post
title:  "[Programmers] 직사각형 별찍기"
date:   2022-06-07 16:13:46 +0900
categories: CodingTest For
---

![Scr2](/img/220607/220607Scr2.png)

Note <br>
![noteImg](/img/220607/220607.PNG)


~~~ c
#include <iostream>

using namespace std;

int main(void) {
    int n;
    int m;
    cin >> n >> m;
    
    for(int i=0; i<m; i++){
        for(int j=0; j<n; j++){
            cout << "*";
        }
        cout << endl;
    }
    return 0;
}
~~~

![Scr1](/img/220607/220607Scr1.png)

***
* eMail : <yskl7137@gmail.com>
