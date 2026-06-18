## Configure Digital Input

This article will cover how to configure the digital input channels on the SoundCard to report TTL signals coming from other devices or trigger sound index playback. Refer to the [connections](./connections.md) article to set up the hardware connection.

The complete workflow is shown below:

:::workflow
![Configure Digital Input Top Level](../workflows/configureDI-toplevel.bonsai)
:::

### Trigger Sound Playback

:::workflow
![Configure Digital Input Trigger Sound](../workflows/configureDI-triggersound.bonsai)
:::

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
> Only sound index triggering is supported currently.

> [!TIP]
> The `SoundCard Events` > `Take(1)` ensures that configuration commands are sent as soon as the SoundCard has initialized. For this to work, set the `DumpRegisters` property in the [`Device`] operator to `True` so that the device emits events on startup.

[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->
[`ConfigureDI0Payload`]: xref:Harp.SoundCard.CreateConfigureDI0Payload
[`CreateMessage`]: xref:Harp.SoundCard.CreateMessage
[`Device`]: xref:Harp.SoundCard.Device
[`Merge`]: xref:Bonsai.Reactive.Merge
[`MulticastSubject`]: xref:Bonsai.Expressions.MulticastSubject
[`SoundIndexDI0Payload`]: xref:Harp.SoundCard.CreateSoundIndexDI0Payload
[`SubscribeSubject`]: xref:Bonsai.Expressions.SubscribeSubject
[`Take`]: xref:Bonsai.Reactive.Take