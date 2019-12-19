---
uid: Meadow.Foundation.Audio.PiezoSpeaker
remarks: *content
---

| PiezoSpeaker  |             |
|---------------|-------------|
| Status        | Working     |
| Source code   | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Core/Speakers) |
| NuGet package | ![NuGet](https://img.shields.io/nuget/v/Meadow.Foundation.svg?label=NuGet) |
| | |

The **PiezoSpeaker** class represents a piezoelectric speaker that can be used to generate tones across a range of frequencies. They typically perform well between 1-5kHz but may go as high as 100kHz. PiezoSpeaker Implements IToneGenerator.

The positive pin of the piezo speaker connects to a pulse width modulation (PWM) capable pin on the Meadow and the negative pin connects to common/ground. A resistor can be placed in-line to reduce volume.

![](../../API_Assets/Meadow.Foundation.Audio.PiezoSpeaker/img_PiezoSpeaker.jpg)

### Code Example

The following example shows how to initialize a PiezoSpeaker and play a melody using an array of notes:

```csharp
public class MeadowApp : App<F7Micro, MeadowApp>
{        
    protected PiezoSpeaker piezoSpeaker;

    public MeadowApp()
    {
        Console.WriteLine("Initializing...");

        piezoSpeaker = new PiezoSpeaker(Device.CreatePwmPort(Device.Pins.D05));

        TestPiezoSpeaker();
    }

    protected void TestPiezoSpeaker()
    {
        Console.WriteLine("TestPiezoSpeaker...");

        while (true)
        {
            Console.WriteLine("Playing A4 note!");
            piezoSpeaker.PlayTone(440, 1000);
            piezoSpeaker.StopTone();
            Thread.Sleep(500);
        }
    }
}

```

[Sample projects available on GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Core.Samples)

### Wiring Example

![](../../API_Assets/Meadow.Foundation.Audio.PiezoSpeaker/PiezoSpeaker.svg)