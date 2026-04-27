## Lower sound playback volume

The [`PlaySoundOrFrequency`] register plays the sound at the amplitude of the stored waveform or at maximum amplitude for pure tones. To lower the volume, use the [`AttenuationAndPlaySoundOrFreq`] register instead to set the attenuation in 0.1 dB steps.

:::workflow
![Adjust Volume Attenuation](../workflows/adjustvolume-attenuation.bonsai)
:::

- Insert a [`KeyDown`] source and set the `Filter` property to `A`. 
- Insert a [`CreateMessage`] operator and configure these properties:
   - `Payload` - Select [`AttenuationAndPlaySoundOrFreqPayload`].
   - `AttenuationAndPlaySoundOrFreq` - Click on the dialog button in the property grid to open the member collection editor. Add three members:
      - The sound index or pure tone frequency to be played (e.g. 2).
      - The attenuation of the left channel (e.g. 200 = -20 dB).
      - The attenuation of the right channel (e.g. 200 = -20 dB).
- Insert a [`MulticastSubject`] operator named `SoundCard Commands`.

Run the workflow and press the <kbd>A</kbd> key to play the sound at reduced volume.

> [!TIP]
> Pure tone playback must be stopped explicitly via the [`Stop`] register.

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