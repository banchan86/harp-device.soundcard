## Trigger sound index playback with digital inputs

The `SoundCard` features digital input channels that can be configured to trigger sound index playback.

:::workflow
![Trigger Sound Configure Digital Input](../workflows/triggersound-configureDI.bonsai)
:::

- Connect a TTL signal from another device to the digital input channel `DI0` (5 V tolerant) and `GND` on the `SoundCard`.
- Insert a [`SubscribeSubject`] operator named `SoundCard Events`.
- Insert a [`Take`] combinator and set the `Count` property to 1.
- Insert a [`CreateMessage`] operator and configure these properties:
   - `Payload` - Select [`ConfigureDI0Payload`].
   - `ConfigureDI0` - Select `StartSound`.
- Insert a second [`CreateMessage`] operator on a new branch and configure these properties:
   - `Payload` - Select [`SoundIndexDI0Payload`].
   - `SoundIndexDI0` - Set the sound index for playback.
- Combine both messages with a [`Merge`] combinator.
- Insert a [`MulticastSubject`] operator named `SoundCard Commands`.

Run the workflow and send the TTL signal from the other device to trigger sound playback.

> [!WARNING]
> Only sound index playback is supported currently.

> [!TIP]
> The `SoundCard Events` > `Take(1)` is another useful pattern for ensuring that configuration commands are sent as soon as the `SoundCard` has initialized. It also relies on the `DumpRegisters` property being set to `True` in the [`Device`] operator.

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