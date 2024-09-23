---
title: STM32 VCP Serial Monitor
author: Rlfxo
date: 2024-04-03 18:53:00 +0900
categories: [STM32 NUCLEO G474RE]
tags: [NUCLEO, STM32, VCP]
pin: false
image:
  path: /img/240403/VCP_2.png
---

## NucleoG474RE에서 VCP를 통한 Serial Monitor
> STM32 NucleoG474RE에서 printf를 사용한 debugging을 하려면 Nucleo 보드에 장착되어있는 STLink에 연결되어 있는 Virtual COM Port로 Serial Monitor를 해보겠습니다.

#### Contents
1. [VCP LPUART port 설정](#1-vcp-port-설정)
2. [Baud Rate, Clock 설정](#2-baud-rate-clock-설정)
3. [Print Hello Task!](#3-print-hello-task!)

### 1 VCP Port 설정
![img](/img/240403/VCP_1.png){: .normal }

NucleoG474에 STlnik V3의 VCP가 있는지 회로도를 통해서 확인 해줍니다.

![img](/img/240403/VCP_2.png){: .normal }

VCP의 TX, RX가 **LPUART1**으로 연결되어 있고 각각 **PA2, PA3** Pin에 연결되어 있습니다.

![img](/img/240403/SYS_1.png){: .normal }
![img](/img/240403/SYS_2.png){: .normal }

Serial Wire Viewer (SWD + SWO) : ARM 기반 MCU에서 실행되는 펌웨어를 debug할 때 printf를 사용하여 출력하고 싶은 내용을 SWO를 통해 출력합니다. SYS Mode and Configuration에서 Trace Asynchronous Sw를 설정합니다.

![img](/img/240403/LPUART_1.png){: .normal }

LPUART1을 활성화 시킵니다.

#### CubeIDE Pin 수동 설정
![img](/img/240403/LPUART_2.png){: .normal }

비어있는 Pin중에 설정가능한 PC0, PC1 Pin으로 할당 됩니다 우리는 이 Pin이 아닌 회로도에서 확인한 VCP는 PA2, PA3를 사용해야 함으로 수동으로 설정해야 합니다.

![img](/img/240403/LPUART_FIX_1.png){: .normal }

원하는 설정을 위해서 PA2에서 LPUART1_TX를 직접 선택합니다.

![img](/img/240403//LPUART_FIX_2.png){: .normal }

각각의 Pin에 설정을 하면 위와 같이 고정된 모습을 확인 할 수 있습니다.

![img](/img/240403/LPUART_FIX_3.png){: .normal }

이후 다시 LPUART1을 활성화 시키면 원하는 Pin으로 설정이 됩니다.

### 2 Baud Rate Clock 설정
![img](/img/240403/BAUDRATE_0.png){: .normal }
![img](/img/240403/BAUDRATE_1.png){: .normal }

제가 사용할 Serial에서 BaudRate를 115200으로 설정할 예정으로 기존의 209700 Bits/s로 설정 되어있는 BaudRate를 변경해주도록 하겠습니다.

![img](/img/240403/CLOCK_1.png){: .normal }

다음으로는 NucleoG474에 있는 외부 크리스털을 통해서 클럭을 설정합니다.

![img](/img/240403/CLOCK_2.png){: .normal }

초기상태의 Clock Configuration은 다음과 같습니다. 여기서 자세히 봐야할 부분은 좌측부터 Clock Source가 무엇으로 되어있는지, Max Clock MHz는 얼마까지 설정이 가능한지, 설정이 적용되는 부분 (LPUART1 (MHz))을 보고 원하는 값으로 변경하면 됩니다.

![img](/img/240403/CLOCK_3.png){: .normal }

저는 Input frequency를 사용해서 HSE로 설정하고 HCLK등에 원하는 값(MHz)을 입력하면 CudeIDE에서 자동으로 나머지 값들을 자동으로 설정해 줍니다. 만약 조합이 불가능한 값이 아니라면 자동으로 조합을 찾아줍니다.

저는 최대 클럭은 170MHz이지만, 16의 배수 중 적절한 값인 144 MHz로 설정하였습니다.

### 3 Print Hello Task!
이제 기본적인 설정을 마치고 printf 함수로 Serial 출력을 확인 해보겠습니다.
printf를 사용하기 위해서 우선 몇가지 코드 작업을 해줘야합니다.

![img](/img/240403/CODE_2.png){: .normal }
![img](/img/240403/CODE_1.png){: .normal }
``` c
#include "stdio.h"

#ifdef __GNUC__
#define PUTCHAR_PROTOTYPE int __io_putchar(int ch)
#else
#define PUTCHAR_PROTOTYPE int fputc(int ch, FILE *f)
#endif

/**
 * @brief Retargets the C library printf function to the USART
 * @param None
 * @retval None
 */
PUTCHAR_PROTOTYPE{
	if (ch == '\n') HAL_UART_Transmit(&hlpuart1, (uint8_t*)"\r", 1, 0xFFFF);
	HAL_UART_Transmit(&hlpuart1, (uint8_t*)&ch, 1, 0xFFFF);
	return ch;
}
```
![img](/img/240403/CODE_0.png){: .normal }

코드상의 주석 처럼 scheduler이 시작되는 osKernelStart 이후의 코드는 동작하지 않습니다.
그래서 위의 while 영역이 아닌 DefaultTask 영역에 출력 함수를 작성해야 합니다.

![img](/img/240403/CODE_3.png){: .normal }

![img](/img/240403/PRINT_2.png){: .normal }

Serial Monitor를 확인해보면 정상적으로 출력되는 것을 확인할 수 있습니다.

![img](/img/240403/PRINT_TASK_0.png){: .normal }

이제 이전에 FreeRTOS에서 생성한 Task가 정상적으로 동작하는지 확인을 위해 위의 코드로 확인 해보겠습니다.
``` c
void StartDefaultTask(void*argument){
  for(;;){
    osDelay (1):
    printf("Hello TaskO!\r\n");
    osDelay (1000):
  }
}

void StartTask02 (void*argument){
  for(;:){
    osDelay (1);
    printf ("Hello Task1!\r\n" );
    osDelay (500);
  }
}
```
![img](/img/240403/PRINT_TASK_1.png){: .normal }

Task0는 1000ms에 한번씩 출력하고 Task1은 500ms에 한번씩 출력하게 하여
Serial Monitor에 Task0 1번에 Task1 2번씩 출력되는 것을 확인 할 수 있습니다.
---
