/**
  @page USART_Printf USART_Printf
  
  @verbatim
  ******************** (C) COPYRIGHT 2012 STMicroelectronics *******************
  * @file    USART/USART_Printf/readme.txt 
  * @author  MCD Application Team
  * @version V1.0.1
  * @date    13-April-2012
  * @brief   Description of the USART Printf Example.
  ******************************************************************************
  *
  * Licensed under MCD-ST Liberty SW License Agreement V2, (the "License");
  * You may not use this file except in compliance with the License.
  * You may obtain a copy of the License at:
  *
  *        http://www.st.com/software_license_agreement_liberty_v2
  *
  * Unless required by applicable law or agreed to in writing, software 
  * distributed under the License is distributed on an "AS IS" BASIS, 
  * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  * See the License for the specific language governing permissions and
  * limitations under the License.
  *
  ******************************************************************************
  @endverbatim

@par Example Description 

This example shows how to retarget the C library printf function to the USART. 
This implementation output the printf message on the Hyperterminal using USART3.

The USARTx is configured as follow:
    - BaudRate = 115200 baud  
    - Word Length = 8 Bits
    - One Stop Bit
    - No parity
    - Hardware flow control disabled (RTS and CTS signals)
    - Receive and transmit enabled


@par Directory contents 

  - USART/USART_Printf/stm32f4xx_conf.h     Library Configuration file
  - USART/USART_Printf/stm32f4xx_it.h       Interrupt handlers header file
  - USART/USART_Printf/stm32f4xx_it.c       Interrupt handlers
  - USART/USART_Printf/main.c               Main program

      
@par Hardware and Software environment 

  - This example runs on STM32F4xx Devices.
  
  - This example has been tested with STM32F4-Discovery.

  - STM32F4-Discovery Set-up 
    - Connect a probes on PA2 for STM32 USART2 TxD and on PA3 for STM32 USART2 RxD

  
 * <h3><center>&copy; COPYRIGHT STMicroelectronics</center></h3>
 */
