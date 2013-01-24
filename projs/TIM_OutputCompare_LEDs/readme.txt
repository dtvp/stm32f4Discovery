This example used the 4 user LEDs to shows how to configure the TIM4
capture output peripheral to generate LED toggle.

TIM4CLK is fixed to SystemCoreClock / 2, the TIM4 Prescaler is set to
(SystemCoreClock / 2) / 10000, which makes it increments timer counter
every 100 us.

The Timer Counter is configured to 10000, which makes TIM4 overflows
every 100 us * 10000 = 1000 ms = 1 s

The objective is to toggle LEDs in different frequencies using only Timer
peripheral:

The channel 1 is connected to LED4 and toggles every 1 ms.
The channel 2 is connected to LED3 and toggles every 10 ms.
The channel 3 is connected to LED5 and toggles every 100 ms.
The channel 4 is connected to LED6 and toggles every 1 s.

The TIM_ConfigPins() inits TIM4 and GPIO clocks and config GPIOs to
Alternate Function and connects them to TIM4.

The TIM4 interrupt just ajust the capture value every interruption on that
channel. An Update event will restart timer and so capture registers.
