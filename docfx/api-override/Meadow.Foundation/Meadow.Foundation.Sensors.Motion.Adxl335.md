---
uid: Meadow.Foundation.Sensors.Motion.Adxl335
remarks: *content
---

| ADXL335       |             |
|---------------|-------------|
| Status        | Working     |
| Source code   | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Sensors.Motion.Adxl335) |
| NuGet package | ![NuGet](https://img.shields.io/nuget/v/Meadow.Foundation.Sensors.Motion.Adxl335.svg?label=NuGet) |
| | |

The **ADXL335** is a low power accelerometer capable of measuring +/- 3g of acceleration along three axes. The ADXL335 is controlled via I2C.

### Code Sample

```csharp
public class MeadowApp : App<F7Micro, MeadowApp>
{
    Adxl335 sensor;

    public MeadowApp()
    {
        sensor = new Adxl335(Device, Device.Pins.A01, Device.Pins.A02, Device.Pins.A03, 500);

        sensor.AccelerationChanged += Sensor_AccelerationChanged;
    }

    private void Sensor_AccelerationChanged(object sender, Meadow.Foundation.Sensors.SensorVectorEventArgs e)
    {
        Console.WriteLine($"X: {e.CurrentValue.X}, Y: {e.CurrentValue.Y}, Z: {e.CurrentValue.Z}");
    }
}
```

[Sample projects available on GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Sensors.Motion.Adxl335/Samples/) 

### Purchasing

The ADXL335 sensor can be purchased on a breakout board from the following suppliers:

* [Adafruit ADXL335](https://www.adafruit.com/product/163)
* [Sparkfun ADXL335](https://www.sparkfun.com/products/9269)

### Wiring Example

![](../../API_Assets/Meadow.Foundation.Sensors.Motion.Adxl335/Adxl335_Fritzing.svg)