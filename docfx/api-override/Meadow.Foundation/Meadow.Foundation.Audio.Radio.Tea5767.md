---
uid: Meadow.Foundation.Audio.Radio.Tea5767
remarks: *content
---

| TEA5767       |             |
|---------------|-------------|
| Status        | Working     |
| Source code   | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Audio.Radio.Tea5767) |
| NuGet package | ![NuGet](https://img.shields.io/nuget/v/Meadow.Foundation.Audio.Radio.TEA5767.svg?label=NuGet) |
| | |

The **TEA5767** FM module is based on the TEA5767GH which is a single-chip, electronically tuned, FM stereo radio for low-voltage applications with fully integrated Intermediate Frequency (IF) selectivity and demodulation. 

The TEA5767 is controlled via I2C. It comes with two 1/4" jacks, one for connection to a headphone/speaker and one to connect an antenna (often sold with the module).

![](../../API_Assets/Meadow.Foundation.Audio.Radio.Tea5767/TEA5767.png)

### Purchasing

You can get a TEA5767 module (with antenna included) from the following supplier(s):

* [newegg](https://www.newegg.ca/p/2S7-01JA-0KY52?item=9SIAJHJ8XC0373&source=region&nm_mc=knc-googleadwordscamkpl-pc&cm_mmc=knc-googleadwordscamkpl-pc-_-pla-lyx+tech+ltd-_-gadgets-_-9SIAJHJ8XC0373&gclid=Cj0KCQjwoKzsBRC5ARIsAITcwXFdQwVcwKklE8IqlrxY8GWLK0dcccGzBlp7OGjuNijObuUBybiqWuwaAqjwEALw_wcB)

### Code Example

The following example shows how to initialize a TEA5767 radio and seek radio stations:

```csharp
public class MeadowApp : App<F7Micro, MeadowApp>
{
    Tea5767 radio;

    public MeadowApp()
    {
        radio = new Tea5767(Device.CreateI2cBus());

        Scan();
    }

    void Scan() 
    {
        Console.WriteLine("TestTEA5767...");

        for (int i = 0; i < 8; i++)
        {
            Thread.Sleep(1000);

            radio.SearchNextSilent();

            Console.WriteLine($"Current frequency: {radio.GetFrequency()}");
        }

        radio.SelectFrequency(94.5f);
    }
}
```
[Sample projects available on GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Audio.Radio.Tea5767/Samples/Audio.Radio.TEA5767_Sample) 

### Wiring Example

To wire a TEA5767 to your Meadow board, connect the following:

| TEA5767 | Meadow Pin  |
|---------|-------------|
| GND     | GND         |
| SCL     | D08 (SCL)   |
| SDA     | D07 (SDA)   |
| VCC     | 3V3         |

It should look like the following diagram:

![](../../API_Assets/Meadow.Foundation.Audio.Radio.Tea5767/TEA5767_Frizzing.png)
