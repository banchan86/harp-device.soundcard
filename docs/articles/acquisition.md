## Data Acquisition

The SoundCard will echo any command it receives and broadcast events occuring on the device. This article covers the different ways to receive, filter, parse, and log these [`HarpMessages`]. The complete top-level workflow is shown below:

:::workflow
![Logging Top Level](../workflows/acquisition-toplevel.bonsai)
:::

### Receiving messages

:::workflow
![SoundCard Receiving Messages](../workflows/acquisition-receivingmessages.bonsai)
:::

To visualize [`HarpMessages`] coming from the device, double-click the [`SoundCard (Device)`](xref:Harp.SoundCard.Device) operator in the [harp device pattern](harp-bonsai.md#harp-device-pattern) while the workflow is running to open the text visualizer. For example, after playing a sound using the [`PlaySoundOrFrequency`] register, the visualizer displays:

```text
Write 32 TimestampedU16@3028.80749 Length:1
Event 32 TimestampedU16@3028.80842 Length:1
```

- `Write` is an echo of the command sent to the SoundCard
- `Event` is when the SoundCard actually executed the command.
- The [address](xref:Harp.SoundCard.Device) `32` in both messages corresponds to the [`PlaySoundOrFrequency`] register
- `TimestampedU16@XX` refers to the message type and the timestamp on the device clock.
- `Length` reflects the number of elements in the message `Payload`, which in this case is just `1` (either the sound index or frequency of the sound).

> [!TIP]
> You can click and drag the border of the visualizer window to increase the number of items displayed.

This method of receiving and reading [`HarpMessages`] gives the `Register` and `Timestamp` but does not include the `Payload` value. It also includes data from all the registers on the device.

### Filtering and parsing messages

Often, we are only interested in visualizing [`HarpMessages`] from a specific `Register` and the `Payload` value. For example, we might only want messages indicating when the device played a sound and which sound index was used. Continuing with the previous workflow:

:::workflow
![SoundCard Filter and Parse](../workflows/acquisition-filterandparse.bonsai)
:::

- Insert a [`SubscribeSubject`] operator named `SoundCard Events`. This will listen to [`HarpMessages`] broadcast from the [`PublishSubject`] named `SoundCard Events` in the [harp device pattern](harp-bonsai.md#harp-device-pattern).
- Insert a [`FilterMessageType`] operator and configure the `MessageType` property to `Event`.
- Insert a [`Parse`] operator and configure the `Register` property to `TimestampedPlaySoundOrFrequency`.
- Double-click the [`Parse`] operator to open the text visualizer and play a sound.

The visualizer will display:

```text
2@15346.973344
```

The first number corresponds to the `Payload` value, in this case the sound index, and the second number is the timestamp on the device clock. Note that only one message is now displayed when a sound is played.

### Logging data

[`HarpMessages`] from the SoundCard can be logged in two ways:

- **Harp format** - The [`DeviceDataWriter`] in the [harp device pattern](harp-bonsai.md#harp-device-pattern) will log raw data from all device registers in the harp binary format, which can be analyzed directly with [harp-python](visualize-data.md).

:::workflow
![SoundCard Device Pattern](../workflows/harp-devicepattern.bonsai)
:::

- **CSV format** - Bonsai's [`CsvWriter`] can be used to log data from individual registers into text files. This approach is best used if compatibility with external programs is needed. However, it does not scale well when working with multiple registers or high-frequency data streams (>100 Hz).

> [!NOTE]
> To use [`CsvWriter`], install the `Bonsai.System` and `Bonsai.System.Design` packages from the Bonsai package manager.

:::workflow
![SoundCard CsvWriter](../workflows/acquisition-csvwriter.bonsai)
:::

- Insert a [`CsvWriter`] operator after each filtered and parsed [`HarpMessage`] stream.
- Configure the `FileName` property of the [`CsvWriter`] with a file name ending in `.csv`, e.g. `PlaySoundOrFrequency.csv`.
- Set the `IncludeHeader` property of the [`CsvWriter`] to `True` to include column names.

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