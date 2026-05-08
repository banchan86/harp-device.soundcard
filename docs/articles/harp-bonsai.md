## Harp Device Pattern

While we can connect operators directly to the SoundCard [`Device`] operator, often we want to access the Harp device from multiple points in the workflow, which can quickly become unwieldy. To streamline this process, we will set up a Harp [device pattern](https://harp-tech.org/articles/operators.html#device-pattern) which makes use of Bonsai [subjects](https://bonsai-rx.org/docs/articles/subjects.html). Subjects are special Bonsai operators that allow us to retrieve data and broadcast commands from anywhere else in the workflow. We will also add an operator to log the data.

:::workflow
![SoundCard Device Pattern](../workflows/harp-devicepattern.bonsai)
:::

- Insert a [`Device`] operator and set the `PortName` property to the communications port for the device.
- Insert a [`DeviceDataWriter`] sink and set the `Path` property for the name and location of the save file (e.g. `Data\SoundCard.harp`). 
   - This will save the data in the standard Harp logging format, which can be loaded with [`harp-python`](visualize-data.md).
- Insert a [`PublishSubject`] operator and name it `SoundCard Events`.
- Right-click the [`Device`] operator, select "Create Source (Bonsai.Harp.HarpMessage)" > "BehaviorSubject". 
   - Name the generated [``BehaviorSubject`1``] [source subject](https://bonsai-rx.org/docs/articles/subjects.html#source-subjects) `SoundCard Commands`. 
   - Connect it as input to the [`Device`] operator.

[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->
[``BehaviorSubject`1``]: xref:Bonsai.Reactive.BehaviorSubject
[`CreateMessage`]: xref:Harp.SoundCard.CreateMessage
[`Device`]: xref:Harp.SoundCard.Device
[`DeviceDataWriter`]: xref:Harp.SoundCard.DeviceDataWriter
[`Parse`]: xref:Harp.SoundCard.Parse
[`HarpMessage`]: xref:Bonsai.Harp.HarpMessage
[`PlaySoundOrFrequency`]: xref:Harp.SoundCard.PlaySoundOrFrequency
[`KeyDown`]: xref:Bonsai.Windows.Input.KeyDown
[`MulticastSubject`]: xref:Bonsai.Expressions.MulticastSubject
[`PublishSubject`]: xref:Bonsai.Reactive.PublishSubject