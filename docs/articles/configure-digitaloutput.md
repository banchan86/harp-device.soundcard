## Configure Digital Output

This article will cover how to configure the digital output channels on the SoundCard to emit TTL signals on sound playback or in response to other workflow events. Refer to the [connections](./connections.md) article to set up the hardware connection.

The complete workflow is shown below:

:::workflow
![Configure Digital Output Top Level](../workflows/configureDO-toplevel.bonsai)
:::

### Signal Sound Playback

The digital output channel can be set to `High` for sound onset and `Low` for sound offset.

:::workflow
![Configure DO Signal Sound](../workflows/configureDO-signalsound.bonsai)
:::

- Insert a [`KeyDown`] operator and configure these properties:
   - `Filter` - Set to `1`.
- Insert a [`CreateMessage`] operator and configure these properties:
   - `Payload` - Select [`ConfigureDO0Payload`].
   - `ConfigureDO0` - Select `HighWhenSound`.
- Insert a [`MulticastSubject`] operator named `SoundCard Commands`.

Run the workflow and press <kbd>1</kbd> to set the configuration, then play a sound and check the TTL signal on the other device.

> [!WARNING]
> Only sound index reporting on `DO0` is supported currently.


[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->
[`ConfigureDO0Payload`]: xref:Harp.SoundCard.CreateConfigureDO0Payload
[`CreateMessage`]: xref:Harp.SoundCard.CreateMessage
[`KeyDown`]: xref:Bonsai.Windows.Input.KeyDown
[`MulticastSubject`]: xref:Bonsai.Expressions.MulticastSubject