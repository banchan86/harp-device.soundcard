
## Receiving and logging data

:::workflow
![Logging Top Level](../workflows/harp-devicepattern.bonsai)
:::

### Receiving data
Placeholder

## Logging data
Data from the SoundCard can be logged in two ways: 

- **Harp format** - The [`DeviceDataWriter`] in the [harp device pattern](harp-bonsai.md#harp-device-pattern) will log data from all device registers in the harp binary format, which can be analyzed directly with [harp-python](visualize-data.md).

:::workflow
![SoundCard Device Pattern](../workflows/harp-devicepattern.bonsai)
:::

- **CSV format** - Bonsai's [`CsvWriter`] can be used to log data from individual registers into text files. This approach is best used if compatibility with external programs is needed. However, it does not scale well when working with multiple registers or high frequency data streams (>100 Hz).

> [!NOTE]
> To use [`CsvWriter`], install the `Bonsai.System` and `Bonsai.System.Design` package from the Bonsai package manager.

:::workflow
![SoundCard CsvWriter](../workflows/logging-csvwriter.bonsai)
:::

- Insert a [`CsvWriter`] operator after each [`Parse`] register that you want to record.
- Configure the `FileName` property of the [`CsvWriter`] with a file name ending in `.csv`, e.g. `PlaySoundOrFrequency.csv`.
- Set the `IncludeHeader` property of the [`CsvWriter`] to `True` to include column names.

[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->
[`CsvWriter`]: xref:Bonsai.IO.CsvWriter
[`DeviceDataWriter`]: : xref:Harp.SoundCard.DeviceDataWriter
[`Parse`]: xref:Harp.SoundCard.Parse