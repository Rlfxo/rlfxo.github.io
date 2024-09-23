---
title: Algorithm Problem solving [0] -Tips-
author: Rlfxo
date: 2024-07-19 16:48:00 +0900
categories: [ALGORITHM]
tags: [PS]
pin: true
# image:
#   path: /img/240501/ex_2.png
---

## 딱 기억해 바보야 
> uint8_t : 0 ~ 255
> uint16_t : 0 ~ 65,535
> uint32_t : 0 ~ 4,294,967,295
>uint64_t : 0 ~ 18,446,744,073,709,551,615
---
- 입출력
* 라인 입력
``` c
string line;
getline(cin, line);
for (char c : line){
    cout << c << endl;
}
```

>\n : 줄바꿈

> %o : 8진수
> %d : 10진수
> %x : 16진수
> %u : unsigned 10진수
> %zu : size
>%p: 포인터의 주소
---
- Vector

Vector Interator
선업 : vector<data *type*>::iterator iter
초기화 : iter = v.begin();
접근 : iter[idx]
연산 : iter++, *iter
* 순방향 접근
for (iter = v.begin(); iter != v.end(); iter++){
    cout << *iter << endl;
}

- Vector Container
선언 : vector<data *type*> v
> v.at(idx);      // idx 참조 (범위 점검 o = 안전)
> v[idx];         // idx 참조 (범위 점검 x = 빠름)
> v.front()       // 처음 원소
> v.back()        // 마지막 원소
> v.begin()       // 처음 원소 (iterator)
> v.end()         // 마지막 원소 (iterator)
> v.size()        // 원소의 갯수
> v.capadity()    // 할당된 공간의 크기
> v2.swap(v1)     // v1과 v2의 capacity를 교환 
>                // 응용 : vector<int>().swap(v1)
> v.insert(x,y)   // x번째 위치에 y 삽입 (interator 반환)
> v.erase(iter)   // iter가 가리키는 원소를 제거
>                // size만 줄어들고 capacity는 남음
> v.empty()       // size가 0이면 true 반환

---
- 부적 
```
    ios::sync_with_stdio(false); cin.tie(NULL);
    cin.exceptions(ios::badbit | ios::failbit);
```
* cin cout 속도 향상
* cout << '\n';
