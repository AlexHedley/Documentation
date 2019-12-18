---
uid: Meadow.Foundation.Sensors.Motion.Adxl362
remarks: *content
---

ADXL362 is an ultralow power, 3-axis MEMS accelerometer that consumes less than 2 μA at a 100 Hz output data rate and 270 nA when in motion triggered wake-up mode. 

## Purchasing

The ADXL362 is available on a small breakout board:

* [Sparkfun ADXL362 Breakout Board](https://www.sparkfun.com/products/11446)

### Usage

The ADXL362 can operating in interrupt and polling mode.  Polling applications are responsible for determining when a sensor is read.  Interrupt applications will be notified when the sensor reading changes by + / - a threshold value.

### Wiring Example

![](../../API_Assets/Meadow.Foundation.Sensors.Motion.Adxl362/Adxl362_Fritzing.svg)