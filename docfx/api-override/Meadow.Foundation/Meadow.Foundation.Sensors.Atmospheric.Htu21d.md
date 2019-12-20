---
uid: Meadow.Foundation.Sensors.Atmospheric.Htu21d
remarks: *content
---

| HTU21D        |             |
|---------------|-------------|
| Status        | Working     |
| Source code   | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Sensors.Atmospheric.HTU21D) |
| NuGet package | <img src="https://img.shields.io/nuget/v/Meadow.Foundation.Sensors.Atmospheric.Htu21D.svg?label=NuGet" style="width: auto;" /> |

The **HTU21D** is a low-cost, easy to use, highly accurate, digital humidity and temperature sensor controlled via the I2C bus.

### Code Example

```csharp
public class MeadowApp : App<F7Micro, MeadowApp>
    {
        Htu21d sensor;

        public MeadowApp()
        {
            sensor = new Htu21d(Device.CreateI2cBus(400));

            sensor.Updated += Sensor_Updated;

            sensor.StartUpdating(1000);
        }

        private void Sensor_Updated(object sender, Meadow.Peripherals.Sensors.Atmospheric.AtmosphericConditionChangeResult e)
        {
            Console.WriteLine($"Temp: {e.New.Temperature}, Humidity: {e.New.Humidity}");
        }
    }

```

[Sample projects available on GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Sensors.Atmospheric.Htu21d/Samples/) 