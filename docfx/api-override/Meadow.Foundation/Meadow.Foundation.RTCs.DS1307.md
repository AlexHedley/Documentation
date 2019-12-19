---
uid: Meadow.Foundation.RTCs.DS1307
remarks: *content
---

| DS1307        |             |
|---------------|-------------|
| Status        | Working     |
| Source code   | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/RTCs.DS1307) |
| NuGet package | ![NuGet](https://img.shields.io/nuget/v/Meadow.Foundation.RTCs.DS1307.svg?label=NuGet) |
| | |

### Code Example

```csharp
public class MeadowApp : App<F7Micro, MeadowApp>
{
    protected DS1307 ds1307;

    public DS1307App()
    {
        ds1307 = new DS1307(Device.CreateI2cBus());

        if (ds1307.IsRunning == false)
        {
            Console.WriteLine("Starting RTC...");
            dSs1307.IsRunning = true;
        }

        while (true)
        {
            for (int i = 0; i < 3; i++)
            {
                var now = ds1307.GetTime();
                Console.WriteLine($"Current time: {now.ToString("MM/dd/yy HH:mm:ss")}");
                Thread.Sleep(1000);
            }

            var rand = new Random();

            if (now.Year < 2019)
            {
                now = DateTime.Now;
            }
            else
            {
                now = now.AddSeconds(rand.Next(1, 30));
            }

            var data = new byte[56];
            for (int i = 0; i < 56; i++)
            {
                data[i] = (byte)rand.Next(256);
            }

            Console.WriteLine($"Writing to RTC RAM   : {BitConverter.ToString(data)}");
            ds1307.WriteRAM(0, data);
            Console.Write($"Reading from RTC RAM : ");
            data = ds1307.ReadRAM(0, 56);
            Console.WriteLine(BitConverter.ToString(data));

        }
    }
}
```

### Circuit Example

The DS3231 real time clock module (see image below) requires only four (for simple timekeeping) or five (for alarms) connections

| DS3231 | Meadow Pin    |
|---------|---------------|
| GND     | GND           |
| VCC     | 3V3           |
| SCL     | D08 (SCL Pin) |
| SDA     | D07 (SDA Pin) |

The 32K pin outputs the 32,768 Hz clock signal from the module.  This signal is only available when power is supplied by V<sub>cc</sub>, it is not available when the module is on battery power.

![](../../API_Assets/Meadow.Foundation.RTCs.DS1307/DS1307_Fritzing.png)
