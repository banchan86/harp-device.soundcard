## Play and stop sounds

The [Harp SoundCard](https://github.com/harp-tech/device.soundcard) supports playback of waveforms stored in its onboard memory. It also includes an internal sine wave generator for pure tones. The following exercises demonstrate how to play these sounds in Bonsai.

> [!WARNING]
> When adding these operators to the workflow, make sure to use the device-specific versions, e.g. `Device (Harp.SoundCard)` instead of `Device (Harp)`. If correctly selected, the names of these operators in the workflow panel will change to reflect either the name of the device or the selected register/payload.

[!INCLUDE [](../apidoc/playsoundorfrequency.md)]

## Controlling sound playback with other events

You can replace [`KeyDown`] with other operators to trigger sound playback on other events in Bonsai.

:::workflow
![Play Sound Index Timer](../workflows/playsound-indextimer.bonsai)
:::

- Replace the [`KeyDown`] source with a [`Timer`] source and set the `DueTime` property to 0.
- Insert a [`SubscribeWhen`] operator after `SoundCard Commands`.
- Insert a [`SubscribeSubject`] operator named `SoundCard Events`, and connect it to [`SubscribeWhen`].

> [!TIP]
> The `SubscribeWhen` > `SoundCard Events` pattern is useful for ensuring that [`HarpMessage`] commands are only sent after the [`Device`] has been initialized. It relies on the `DumpRegisters` property being set to `True` in [`Device`]. Use it when needed, for instance, if sounds are being played at the start of the workflow.

[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->
[`Device`]: xref:Harp.SoundCard.Device
[`KeyDown`]: xref:Bonsai.Windows.Input.KeyDown
[`SubscribeSubject`]: xref:Bonsai.Expressions.SubscribeSubject
[`SubscribeWhen`]: xref:Bonsai.Reactive.SubscribeWhen
[`Timer`]: xref:Bonsai.Reactive.Timer