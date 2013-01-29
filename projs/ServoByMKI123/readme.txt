This project uses onboard MEMS accelerometer X and Y axis to control
two servos. They are latched on TIM4 update interruption and PWM duty
cycles are ajusted considering inertial board position.

TIM4CLK is fixed to SystemCoreClock / 2, the TIM4 Prescaler is set to
(SystemCoreClock / 2) / 1000000, which makes it increments timer counter
every 1 us.

The Timer Counter is configured to 20000, which makes TIM4 overflows
every 20 ms, the commom period of servos.

Developer just have to connect one servo signal on PD11 and a second
servo signal on PD15.
