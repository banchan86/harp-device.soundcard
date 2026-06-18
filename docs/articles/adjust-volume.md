## Adjust Volume

The [`PlaySoundOrFrequency`] register in the [play sound](play-sound.md) article will play the sound at the amplitude of the stored waveform or at maximum amplitude for the pure tone frequency generator. This article will demonstrate how to dynamically lower the amplitude with other registers.

> [!NOTE]
> The playback amplitude of stored waveforms can be attenuated but not amplified. Upload waveforms at full 24-bit depth to maximize the volume.

The complete workflow is shown below:

:::workflow
![Adjust Volume Top Level](../workflows/adjustvolume-toplevel.bonsai)
:::

### Attenuate and Play Sound

Use the [`AttenuationAndPlaySoundOrFreq`] register as a drop-in replacement for the [`PlaySoundOrFrequency`] register to start sound playback at a lower volume. The attenuation is set in 0.1 dB steps.

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
> Just like the [`PlaySoundOrFrequency`] register, pure tone playback must be stopped explicitly via the [`Stop`] register.

[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->
[`AttenuationAndPlaySoundOrFreq`]: xref:Harp.SoundCard.AttenuationAndPlaySoundOrFreq
[`AttenuationAndPlaySoundOrFreqPayload`]: xref:Harp.SoundCard.CreateAttenuationAndPlaySoundOrFreqPayload
[`CreateMessage`]: xref:Harp.SoundCard.CreateMessage
[`HarpMessage`]: xref:Bonsai.Harp.HarpMessage
[`Merge`]: xref:Bonsai.Reactive.Merge
[`PlaySoundOrFrequency`]: xref:Harp.SoundCard.PlaySoundOrFrequency
[`Stop`]: xref:Harp.SoundCard.Stop