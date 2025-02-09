---
uid: Meadow.Foundation.Sensors.Environmental.Pmsa003i
remarks: *content
---

| Pmsa003i | |
|--------|--------|
| Status | <img src="https://img.shields.io/badge/Working-brightgreen" style="width: auto; height: -webkit-fill-available;" alt="Status badge: working" /> |
| Source code | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/main/Source/Meadow.Foundation.Peripherals/Sensors.Environmental.Pmsa003I) |
| Datasheet(s) | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/main/Source/Meadow.Foundation.Peripherals/Sensors.Environmental.Pmsa003I/Datasheet) |
| NuGet package | <a href="https://www.nuget.org/packages/Meadow.Foundation.Sensors.Environmental.Pmsa300i/" target="_blank"><img src="https://img.shields.io/nuget/v/Meadow.Foundation.Sensors.Environmental.Pmsa300i.svg?label=Meadow.Foundation.Sensors.Environmental.Pmsa300i" alt="NuGet Gallery for Meadow.Foundation.Sensors.Environmental.Pmsa300i" /></a> |
### Code Example

```csharp
Pmsa003i pmsa003i;

public override Task Initialize()
{
    var bus = Device.CreateI2cBus(I2cBusSpeed.Standard);
    pmsa003i = new Pmsa003i(bus);

    pmsa003i.Updated += Pmsa003i_Updated;

    return base.Initialize();
}

public override Task Run()
{
    Resolver.Log.Info("Run...");

    pmsa003i.StartUpdating(TimeSpan.FromSeconds(2));

    return base.Run();
}

private void Pmsa003i_Updated(object sender, IChangeResult<(
    Density? StandardParticulateMatter_1micron,
    Density? StandardParticulateMatter_2_5micron,
    Density? StandardParticulateMatter_10micron,
    Density? EnvironmentalParticulateMatter_1micron,
    Density? EnvironmentalParticulateMatter_2_5micron,
    Density? EnvironmentalParticulateMatter_10micron,
    ParticleDensity? ParticleDensity_0_3microns,
    ParticleDensity? ParticleDensity_0_5microns,
    ParticleDensity? ParticleDensity_10microns,
    ParticleDensity? ParticleDensity_25microns,
    ParticleDensity? ParticleDensity_50microns,
    ParticleDensity? ParticleDensity_100microns)> e)
{
    Resolver.Log.Info($"Standard Particulate Matter 1 micron: {e.New.StandardParticulateMatter_1micron.Value.MicroGramsPerMetersCubed} micrograms per m^3");
    Resolver.Log.Info($"Standard Particulate Matter 2_5micron: {e.New.StandardParticulateMatter_2_5micron.Value.MicroGramsPerMetersCubed} micrograms per m^3");
    Resolver.Log.Info($"Standard Particulate Matter 10 micron: {e.New.StandardParticulateMatter_10micron.Value.MicroGramsPerMetersCubed} micrograms per m^3");
    Resolver.Log.Info($"Environmental Particulate Matter 1 micron: {e.New.EnvironmentalParticulateMatter_1micron.Value.MicroGramsPerMetersCubed} micrograms per m^3");
    Resolver.Log.Info($"Environmental Particulate Matter 2.5 micron: {e.New.EnvironmentalParticulateMatter_2_5micron.Value.MicroGramsPerMetersCubed} micrograms per m^3");
    Resolver.Log.Info($"Environmental Particulate Matter 10 micron: {e.New.EnvironmentalParticulateMatter_10micron.Value.MicroGramsPerMetersCubed} micrograms per m^3"); ;

    Resolver.Log.Info($"Count of particles - 0.3 microns: {e.New.ParticleDensity_0_3microns.Value.ParticlesPerCentiliter} in 0.1 liters of air");
    Resolver.Log.Info($"Count of particles - 0.5 microns: {e.New.ParticleDensity_0_5microns.Value.ParticlesPerCentiliter} in 0.1 liters of air");
    Resolver.Log.Info($"Count of particles - 10 microns: {e.New.ParticleDensity_10microns.Value.ParticlesPerCentiliter} in 0.1 liters of air");
    Resolver.Log.Info($"Count of particles - 25 microns: {e.New.ParticleDensity_25microns.Value.ParticlesPerCentiliter} in 0.1 liters of air");
    Resolver.Log.Info($"Count of particles - 50 microns: {e.New.ParticleDensity_50microns.Value.ParticlesPerCentiliter} in 0.1 liters of air");
    Resolver.Log.Info($"Count of particles - 100 microns: {e.New.ParticleDensity_100microns.Value.ParticlesPerCentiliter} in 0.1 liters of air");
}

```

[Sample project(s) available on GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/main/Source/Meadow.Foundation.Peripherals/Sensors.Environmental.Pmsa003I/Samples/Pmsa003I_Sample)

