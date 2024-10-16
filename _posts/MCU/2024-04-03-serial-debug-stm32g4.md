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

## NucleoG474RE에서 VCP를 활용한 시리얼 모니터 설정
> STM32 NucleoG474RE에서 `printf`를 사용한 디버깅을 위해, 보드에 내장된 STLink의 Virtual COM Port(VCP)를 통해 시리얼 모니터를 설정하는 방법을 알아보겠습니다.

#### 목차
1. [VCP LPUART 포트 설정](#1-vcp-port-설정)
2. [Baud Rate 및 클럭 설정](#2-baud-rate-clock-설정)
3. [Hello Task 출력 확인](#3-print-hello-task)

### 1 VCP 포트 설정
![img](/img/240403/VCP_1.png)

먼저, NucleoG474RE 보드에 STLink V3의 VCP가 있는지 회로도를 통해 확인합니다.

![img](/img/240403/VCP_2.png)

VCP의 TX, RX 핀은 **LPUART1**에 연결되어 있으며, 각각 **PA2**와 **PA3** 핀에 할당되어 있습니다.

![img](/img/240403/SYS_1.png)
![img](/img/240403/SYS_2.png)

`Serial Wire Viewer` (SWD + SWO)는 ARM 기반 MCU에서 `printf`를 사용하여 펌웨어의 디버깅 정보를 출력하는데 유용합니다. SYS Mode and Configuration에서 **Trace Asynchronous SW**를 설정합니다.

![img](/img/240403/LPUART_1.png)

이후 **LPUART1**을 활성화합니다.

#### CubeIDE에서 핀 수동 설정
![img](/img/240403/LPUART_2.png)

기본적으로 **PC0**와 **PC1** 핀이 자동으로 할당되지만, 회로도에 따라 **PA2**와 **PA3** 핀을 수동으로 설정해야 합니다.

![img](/img/240403/LPUART_FIX_1.png)

**PA2**에서 **LPUART1_TX**를 선택합니다.

![img](/img/240403//LPUART_FIX_2.png)

각 핀을 설정한 후에는 고정된 모습을 확인할 수 있습니다.

![img](/img/240403/LPUART_FIX_3.png)

마지막으로 **LPUART1**을 활성화하여 원하는 핀으로 설정을 완료합니다.

### 2 Baud Rate 및 클럭 설정
![img](/img/240403/BAUDRATE_0.png)
![img](/img/240403/BAUDRATE_1.png)

시리얼 통신의 Baud Rate는 기본적으로 209700 Bits/s로 설정되어 있지만, 이를 115200으로 변경하겠습니다.

![img](/img/240403/CLOCK_1.png)

다음으로, NucleoG474RE 보드의 외부 크리스털을 이용하여 클럭을 설정합니다.

![img](/img/240403/CLOCK_2.png)

초기 상태의 클럭 설정 화면에서 **Clock Source**와 최대 클럭 주파수, 그리고 **LPUART1**에 적용되는 클럭 설정을 확인한 후 필요한 값을 입력하여 수정합니다.

![img](/img/240403/CLOCK_3.png)

HSE를 입력 주파수로 사용하여 원하는 클럭 값으로 설정합니다. STM32CubeIDE는 자동으로 최적의 조합을 찾아 설정해 줍니다. 저는 최대 170MHz 중 144MHz로 설정했습니다.

### 3 Hello Task 출력 확인

기본 설정이 완료되었으니, `printf` 함수를 사용하여 시리얼 출력을 확인하겠습니다. 이를 위해서는 몇 가지 코드 작업이 필요합니다.

![img](/img/240403/CODE_2.png)
![img](/img/240403/CODE_1.png)

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
![img](/img/240403/CODE_0.png)

주석에서 설명한 것처럼, 스케줄러가 시작되는 `osKernelStart` 이후에는 `while` 루프 외부에 있는 코드는 실행되지 않습니다. 따라서 출력 함수를 `while` 문이 아닌 **DefaultTask** 영역에 작성해야 합니다.

![img](/img/240403/CODE_3.png)

![img](/img/240403/PRINT_2.png)

이제 시리얼 모니터를 통해 정상적으로 출력되는 것을 확인할 수 있습니다.

![img](/img/240403/PRINT_TASK_0.png)

마지막으로, FreeRTOS에서 생성한 Task가 제대로 동작하는지 확인하기 위해 앞서 작성한 코드를 실행해 보겠습니다.

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
![img](/img/240403/PRINT_TASK_1.png)

Task0는 1000ms 간격으로, Task1은 500ms 간격으로 각각 출력되도록 설정했습니다. 결과적으로, 시리얼 모니터에서는 Task0가 한 번 출력될 때 Task1이 두 번 출력되는 것을 확인할 수 있습니다.
---
