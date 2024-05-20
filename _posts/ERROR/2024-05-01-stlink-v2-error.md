---
title: ST-Link message UR connection mode is defined
author: Rlfxo
date: 2024-05-01 16:33:00 +0900
categories: [ST-Link]
tags: [STM32, ERROR]
pin: false
image:
  path: /img/240501/ex_2.png
---

## "UR connection mode is defined with the HWrst reset mode" 원인 분석
> Windows 환경에서 STM32CubeProgrammer을 사용할 때 정품이 아닌 ST-Link 호환 제품 사용시, message 창에 "UR connection mode is defined with the HWrst reset mode" 메시지와 함께 연결이 안되는 증상 발생하는 경우가 있음.

#### Contents

1. [증상](#1-증상-확인)
2. [원인](#2-원인-확인)

### 1 증상 확인
![img1](/img/240501/ex_1.png){: .normal }

STM32CubeProgrammer에서 ST-Link 호환 제품으로 연결 시도시 위와 같이 Log 창에 "UR connection mode is defined with the HWrst reset mode" 메시지만 나오고 연결이 안됩니다. 

![img2](/img/240501/ex_2.png){: .normal }

Mac 환경에서 사용 할때와 Windows 환경에서 사용시 차이점으로는 ST-LINK configuration의 Serial number가 정상적으로 읽지 못하고 1 character로 나타납니다. (ex. C, 8, 3 ...) 

![img3](/img/240501/info_1.png){: .normal }

커뮤니티에서 같은 증상을 보이는 이슈가 있었는데 fakechip이 사용된 경우 외관은 비슷하나 내부는 다른 호환제품 이라는 내용의 이슈를 보았습니다... (정품의 경우 ST칩이 사용 됨)

### 2 원인 확인
![img4](/img/240501/check_0.png){: .normal }

확인을 위해서 ST-Link의 케이스를 분해하여 내부의 사용된 chip을 확인해 보았습니다.

![img5](/img/240501/check_1.png){: .normal }

fakechip으로 불리는 예시 사진과 같은 칩을 사용한 호환제품으로 확인 하였습니다.

![img5](/img/240501/info_2.png){: .normal }

커뮤니티에서 찾은 다른 사진으로 ST 홈페이지에서 구입한 정품과 아마존에서 구입한 호환제품의 패키징을 비교한 사진입니다.
(좌:정품 우:호환제품)

![img6](/img/240501/check_3.png){: .normal }

정품과 호환제품의 뒷면을 비교한 사진으로 가지고 있는 제품의 구분이 필요시 비교하시면 될 것 같습니다.
(좌:정품 우:호환제품)A2020.03으로 적힌 제품, A2022.06으로 적힌 것도 있음


Mac에서는 사용시 ST-LINK configuration의 Serial number가 입력되며 정상적으로 사용이 가능한 것으로 보아 STM32CubeProgrammer에서 ST-Link의 정품 여부를 확인하는 부분에 접근을 못하는 것인지 아직 Mac용 Programmer에서 확인기능을 추가하지 않은 것인지 확인이 필요할 것 같습니다.


추가로 Windows에서 현제 기준으로 호환제품을 사용하는 방법은 STM32CubeProgrammer가 아닌 STM32 ST-LINK UTILITY Application로 사용 가능합니다. (하지만 code protection 등의 기능 없음) 

---
