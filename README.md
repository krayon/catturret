# Cat Laser Turret

A radio controlled laser turret, for playing with cats.

## Plan

### Remote

- Run micropython
- 1 x RP2040 Pro Micro / Zero
- 1 x Analog joystick
- 2 x Push buttons (tactile?)
- 1 x nRF24L01+ module
- Capacitors (TBD)

#### Example Code

```python
from machine import Pin, ADC
import utime

buttonA = Pin(20, mode=Pin.IN, pull=Pin.PULL_UP)
buttonB = Pin(22, mode=Pin.IN, pull=Pin.PULL_UP)
buttonL = Pin(21, mode=Pin.IN, pull=Pin.PULL_UP)
xAxis = ADC(Pin(27))
yAxis = ADC(Pin(26))

while True:
    xValue = 65535 - xAxis.read_u16()
    yValue = 65535 - yAxis.read_u16()
    print(str(xValue) +", " + str(yValue) + " --- " + ("L" if not buttonL.value() else " ") + ("A" if not buttonA.value() else " ") + ("B" if not buttonB.value() else " "))
    utime.sleep(0.1)
```

### Turret

- Run micropython
- 1 x RP2040 Pro Micro / Zero
- 1 x Laser module
- 1 x 10k Resistor
- 1 x nRF24L01+ module
- 2 x SG90 Servos
- Capacitors (TBD)
- 1 x MOSFET? (TBD)

----
[//]: # ( vim: set ts=4 sw=4 et cindent tw=80 ai si syn=markdown ft=markdown: )
