## Play and stop sounds

The [Harp SoundCard](https://github.com/harp-tech/device.soundcard) supports playback of waveforms stored in its onboard memory. It also includes an internal sine wave generator for pure tones. The following exercises demonstrate how to play these sounds in Bonsai.

> [!WARNING]
> When adding these operators to the workflow, make sure to use the device-specific versions, e.g. `Device (Harp.SoundCard)` instead of `Device (Harp)`. If correctly selected, the names of these operators in the workflow panel will change to reflect either the name of the device or the selected register/payload.

## Play sound index

Sounds can be played from the `SoundCard` onboard memory by using the [`PlaySoundOrFrequency`] register.

:::workflow
![Play Sound Index Keydown](../workflows/playsound-indexkeydown.bonsai)
:::

- Insert a [`KeyDown`] source and set the `Filter` property to `A`. 
- Insert a [`CreateMessage`] operator to construct a [`HarpMessage`] command to send to the device and configure these properties:
    - `Payload` - Select [`PlaySoundOrFrequencyPayload`] from the property dropdown menu.
    - `PlaySoundOrFrequency` - Set the index of the sound you want to play from the `SoundCard` onboard memory (2-31).
- Insert a [`MulticastSubject`] operator to send [`HarpMessage`] commands to named subjects, and configure the `Name` property to `SoundCard Commands`.

Run the workflow and press the <kbd>A</kbd> key to play the sound. Sound duration is determined by the length of the stored waveform.

You can replace [`KeyDown`] with other operators to trigger sound playback on other events in Bonsai.

:::workflow
![Play Sound Index Timer](../workflows/playsound-indextimer.bonsai)
:::

- Replace the [`KeyDown`] source with a [`Timer`] source and set the `DueTime` property to 0.
- Insert a [`SubscribeWhen`] operator after `SoundCard Commands`.
- Insert a [`SubscribeSubject`] operator named `SoundCard Events`, and connect it to [`SubscribeWhen`].

> [!TIP]
> The `SubscribeWhen` > `SoundCard Events` pattern is useful for ensuring that [`HarpMessage`] commands are only sent after the [`Device`] has been initialized. It relies on the `DumpRegisters` property being set to `True` in [`Device`]. Use it when needed, for instance, if sounds are being played at the start of the workflow.

## Play pure tone

The [`PlaySoundOrFrequency`] register can also be used to play pure tones using the internal sine wave generator.

:::workflow
![Play Sound Frequency](../workflows/playsound-frequency.bonsai)
:::

- Insert a [`KeyDown`] source and set the `Filter` property to `A`. 
- Insert a [`CreateMessage`] operator and configure these properties:
   - `Payload` - Select [`PlaySoundOrFrequencyPayload`].
   - `PlaySoundOrFrequency` - Set the desired frequency in Hz (e.g. 1000).
- Insert a [`MulticastSubject`] operator named `SoundCard Commands`.

Unlike playback of sounds from the onboard memory, the pure tone will continue playing until it is terminated via the [`Stop`] register.

- Insert a [`KeyDown`] source and set the `Filter` property to `S`.
- Insert a [`CreateMessage`] operator and configure these properties:
   - `Payload` - Select [`StopPayload`].
   - `Stop` - Set the value to 1 (or any other value than 0).
- Insert a [`MulticastSubject`] operator named `SoundCard Commands`.

Run the workflow, press the <kbd>A</kbd> key to play the sound, and press the <kbd>S</kbd> key to stop playback.

> [!WARNING]
> The [`Stop`] register can only be used to stop playback from the internal sine wave generator, not sounds from the onboard memory.

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