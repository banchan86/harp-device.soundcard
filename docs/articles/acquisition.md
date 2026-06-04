## Acquisition and Logging

The SoundCard will echo any command it receives and broadcast events occurring on the device using the [harp communication protocol](https://harp-tech.org/protocol/BinaryProtocol-8bit.html). This article covers how to visualize and log these [`HarpMessages`] while the workflow is running.

The complete workflow is shown below:

:::workflow
![Logging Top Level](../workflows/acquisition-toplevel.bonsai)
:::

### Filter and Parse Messages

Often, we are interested in visualizing [`HarpMessages`] from a specific `Register` and the `Payload` value. For example, we might want messages indicating when the device played a sound and which sound index was used. To do that, we can filter and parse the messages using the workflow below:

:::workflow
![SoundCard Filter and Parse](../workflows/acquisition-filterandparse.bonsai)
:::

- Insert a [`SubscribeSubject`] operator named `SoundCard Events`. This will listen to [`HarpMessages`] broadcast from the [`PublishSubject`] named `SoundCard Events` in the [Harp device pattern](harp-bonsai.md#harp-device-pattern).
- Insert a [`FilterMessageType`] operator and configure the `MessageType` property to `Event`.
- Insert a [`Parse`] operator and configure the `Register` property to `TimestampedPlaySoundOrFrequency`.
- Double-click the [`Parse`] operator to open the text visualizer and play a sound using the [`PlaySoundOrFrequency`] register.

The visualizer will display:

```text
2@15346.973344
```

The first number corresponds to the `Payload` value, in this case the sound index, and the second number is the timestamp on the device clock.

### Log Data

:::workflow
![SoundCard Device Pattern](../workflows/harp-devicepattern.bonsai)
:::

The [`DeviceDataWriter`] in the [Harp device pattern](harp-bonsai.md#harp-device-pattern) will log raw data from all device registers in the harp binary format, which can be analyzed directly with [harp-python](visualize-data.md).

[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->
[`CsvWriter`]: xref:Bonsai.IO.CsvWriter
[`DeviceDataWriter`]: xref:Harp.SoundCard.DeviceDataWriter
[`HarpMessage`]: xref:Bonsai.Harp.HarpMessage
[`HarpMessages`]: xref:Bonsai.Harp.HarpMessage
[`FilterMessageType`]: xref:Bonsai.Harp.FilterMessageType
[`Parse`]: xref:Harp.SoundCard.Parse
[`PlaySoundOrFrequency`]: xref:Harp.SoundCard.PlaySoundOrFrequency
[`PublishSubject`]: xref:Bonsai.Reactive.PublishSubject
[`SubscribeSubject`]: xref:Bonsai.Expressions.SubscribeSubject