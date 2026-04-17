## Intro to Bonsai

Placeholder for short guide to Bonsai.

## Device pattern

Set up the standard Harp [device pattern](../articles/operators.md#device-pattern) to initialize the device, log data, broadcast events, and send commands to the `SoundCard`.

:::workflow
![SoundCard Device Pattern](../workflows/harp-devicepattern.bonsai)
:::

- Insert a [`Device`] operator and set the `PortName` property to the communications port for the device.
- Insert a [`DeviceDataWriter`] sink and set the `Path` property (e.g. `SoundCard.harp`). 
   - This will save the data in the standard Harp logging format, which can be loaded with [`harp-python`](../articles/python.md).
- Insert a [`PublishSubject`] operator and name it `SoundCard Events`.
- Right-click the [`Device`] operator, select "Create Source (Bonsai.Harp.HarpMessage)" > "BehaviorSubject". 
   - Name the generated [``BehaviourSubject`1``] [source subject](https://bonsai-rx.org/docs/articles/subjects.html#source-subjects) `SoundCard Commands`. 
   - Connect it as input to the [`Device`] operator.

## Testing the device in Bonsai

:::workflow
![SoundCard Hello World](../workflows/soundcard-helloworld.bonsai)
:::

- Hover over the workflow cell above, click the "Copy" icon in the top right, and paste the workflow into Bonsai.
- Set the `PortName` property of the [`SoundCard`](xref:Harp.SoundCard.Device) operator to the communications port of the `SoundCard` (e.g. COM7).
- Run the workflow. If the `SoundCard` is properly connected, you should hear a short tone.

[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->
[`AttenuationAndPlaySoundOrFreq`]: xref:Harp.SoundCard.AttenuationAndPlaySoundOrFreq
[`AttenuationAndPlaySoundOrFreqPayload`]: xref:Harp.SoundCard.CreateAttenuationAndPlaySoundOrFreqPayload
[``BehaviourSubject`1``]: xref:Bonsai.Reactive.BehaviorSubject
[`ConfigureDI0Payload`]: xref:Harp.SoundCard.CreateConfigureDI0Payload
[`SoundIndexDI0Payload`]: xref:Harp.SoundCard.CreateSoundIndexDI0Payload
[`CreateMessage`]: xref:Harp.SoundCard.CreateMessage
[`Device`]: xref:Harp.SoundCard.Device
[`DeviceDataWriter`]: xref:Harp.SoundCard.DeviceDataWriter
[`HarpMessage`]: xref:Bonsai.Harp.HarpMessage
[`KeyDown`]: xref:Bonsai.Windows.Input.KeyDown
[`Merge`]: xref:Bonsai.Reactive.Merge
[`MulticastSubject`]: xref:Bonsai.Expressions.MulticastSubject
[`PlaySoundOrFrequency`]: xref:Harp.SoundCard.PlaySoundOrFrequency
[`PlaySoundOrFrequencyPayload`]: xref:Harp.SoundCard.CreatePlaySoundOrFrequencyPayload
[`PublishSubject`]: xref:Bonsai.Reactive.PublishSubject
[`Stop`]: xref:Harp.SoundCard.Stop
[`StopPayload`]: xref:Harp.SoundCard.CreateStopPayload
[`SubscribeSubject`]: xref:Bonsai.Expressions.SubscribeSubject
[`SubscribeWhen`]: xref:Bonsai.Reactive.SubscribeWhen
[`Take`]: xref:Bonsai.Reactive.Take
[`Timer`]: xref:Bonsai.Reactive.Timer