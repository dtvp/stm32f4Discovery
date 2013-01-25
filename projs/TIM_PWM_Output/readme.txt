This example uses the 4 user LEDs pins to shows how to configure the TIM4
as PWM Output to control servos.

TIM4CLK is fixed to SystemCoreClock / 2, the TIM4 Prescaler is set to
(SystemCoreClock / 2) / 1000000, which makes it increments timer counter
every 1 us.

The period of PWM wave is fixed in 20 ms, like most servos, and servo
PWM duty cycle is set on output capture registers.

The Timer Counter is set in 20000 to produce overflows every 20 ms.

TIM4 output capture channels 1 and 2 uses Servo1Pulse value, which is
configured as 1000, 1 ms.

Channels 3 and 4 uses Servo2Pulse value, set in 2000, 2 ms.

To fix a servo position, just connect the servo signal to PD12 or PD13
for Servo1. You can also connect servo signal on PD14 or PD15 for Servo2.

The TIM_ConfigPins() inits TIM4 and GPIO clocks and config GPIOs to
Alternate Function and connects them to TIM4.

The TIM4 interrupt just ajust the capture value every interruption on that
channel. An Update event will restart timer and so capture registers.
