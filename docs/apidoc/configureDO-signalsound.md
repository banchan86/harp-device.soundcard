### Signal Sound Playback

The digital output channel can be set to `High` for sound onset and `Low` for sound offset.

:::workflow
![Configure DO Signal Sound](../workflows/configureDO-signalsound.bonsai)
:::

- Insert a [`SubscribeSubject`] operator named `SoundCard Events`.
- Insert a [`Take`] combinator and set the `Count` property to 1.
- Insert a [`CreateMessage`] operator and configure these properties:
   - `Payload` - Select [`ConfigureDO0Payload`].
   - `ConfigureDO0` - Select `HighWhenSound`.
- Insert a [`MulticastSubject`] operator named `SoundCard Commands`.

Run the workflow, play a sound, and check the TTL signal on the other device.

> [!WARNING]
> Only sound index reporting on `DO0` is supported currently.

> [!TIP]
> The `SoundCard Events` > `Take(1)` ensures that configuration commands are sent as soon as the SoundCard has initialized. For this to work, set the `DumpRegisters` property in the [`Device`] operator to `True` so that the device emits events on startup.

<!--Reference Style Links -->
[`ConfigureDO0Payload`]: xref:Harp.SoundCard.CreateConfigureDO0Payload
[`CreateMessage`]: xref:Harp.SoundCard.CreateMessage
[`Device`]: xref:Harp.SoundCard.Device
[`MulticastSubject`]: xref:Bonsai.Expressions.MulticastSubject
[`SubscribeSubject`]: xref:Bonsai.Expressions.SubscribeSubject
[`Take`]: xref:Bonsai.Reactive.Take