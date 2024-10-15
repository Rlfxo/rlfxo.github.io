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
> Windows 환경에서 STM32CubeProgrammer을 사용할 때, 정품이 아닌 ST-Link 호환 제품을 사용할 경우 "UR connection mode is defined with the HWrst reset mode" 메시지와 함께 연결이 되지 않는 증상이 발생하였다.

#### Contents

1. [Issue](#1-issue)
2. [Cause](#2-cause)

### 1. Issue
![img1](/img/240501/ex_1.png){: .normal }

STM32CubeProgrammer에서 ST-Link 호환 제품으로 연결을 시도할 때, 위와 같은 Log 창에 "UR connection mode is defined with the HWrst reset mode" 메시지가 나타나며 연결이 이루어지지 않았다.

![img2](/img/240501/ex_2.png){: .normal }

Mac 환경에서 사용할 때와 Windows 환경에서 사용할 때의 차이점으로는 ST-LINK configuration의 Serial number가 정상적으로 읽히지 않고, 1개의 문자로 나타나는 것을 확인할 수 있었다. (예: C, 8, 3 등)

![img3](/img/240501/info_1.png){: .normal }

커뮤니티에서 유사한 증상을 보이는 이슈를 발견하였는데, fakechip이 사용된 경우 외관은 비슷하지만 내부는 다른 호환 제품이라는 보고가 있었다. (정품의 경우 ST칩이 사용됨)

### 2. Cause
![img4](/img/240501/check_0.png){: .normal }

원인을 확인하기 위해 ST-Link의 케이스를 분해하여 내부에 사용된 칩을 확인하였다.

![img5](/img/240501/check_1.png){: .normal }

fakechip으로 알려진 예시 사진과 동일한 칩이 사용된 호환 제품임을 확인하였다.

![img5](/img/240501/info_2.png){: .normal }

커뮤니티에서 찾은 다른 사진으로, ST 공식 홈페이지에서 구입한 정품과 아마존에서 구입한 호환 제품의 패키징을 비교한 사진을 발견하였다.
(좌: 정품, 우: 호환 제품)

![img6](/img/240501/check_3.png){: .normal }

정품과 호환 제품의 뒷면을 비교한 사진으로, 가지고 있는 제품의 구분이 필요할 경우 이를 참조하면 될 것이다.
(좌: 정품, 우: 호환 제품) 참고로 A2020.03으로 적힌 제품과 A2022.06으로 적힌 제품도 있다.

Mac에서는 ST-LINK configuration의 Serial number가 정상적으로 입력되며 정상적으로 사용이 가능한 것으로 보아, STM32CubeProgrammer에서 ST-Link의 정품 여부를 확인하는 기능이 Windows에서만 작동하는 것인지, 혹은 Mac용 Programmer에 해당 기능이 아직 추가되지 않은 것인지는 추가적인 확인이 필요하다.

또한, Windows 환경에서 호환 제품을 사용할 수 있는 방법으로는 STM32CubeProgrammer 대신 STM32 ST-LINK UTILITY Application을 사용할 수 있다. (단, code protection 등의 기능은 사용할 수 없음)

---