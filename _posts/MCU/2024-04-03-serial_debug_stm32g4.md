---
title: STM32 VCP Serial Monitor
author: Rlfxo
date: 2024-04-03 18:53:00 +0900
categories: [STM32 NUCLEO G474RE]
tags: [NUCLEO, STM32, VCP]
pin: false
# render_with_liquid: false
---

## NucleoG474RE에서 VCP를 통한 Serial Monitor
> STM32 NucleoG474RE에서 printf를 사용한 debugging을 하려면 Nucleo 보드에 장착되어있는 STLink에 연결되어 있는 Virtual COM Port로 Serial Monitor를 해보겠습니다.

#### 목차
1. [VCP LPUART port 설정](#1-vcp-port-설정)
2. [Baud Rate, Clock 설정](#2-baud-rate-clock-설정)
3. [Print Hello Task!](#3-print-hello-task!)

### 1 VCP Port 설정
![img](/img/240331/frtos-setting-1.png){: .normal }

### 2 Baud Rate Clock 설정
![img](/img/240331/make-new-task-1.png){: .normal}

### 3 Print Hello Task!

---
