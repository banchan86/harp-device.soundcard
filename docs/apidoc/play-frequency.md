### Play Pure Tone Frequency

Pure tones can be played from the `SoundCard` internal sine wave generator by specifying the frequency in the [`PlaySoundOrFrequency`] register payload. Sounds will be played continuously at the device's max amplitude until stopped.

:::workflow
![Play Sound Frequency](../workflows/playsound-frequency.bonsai)
:::

- Insert a [`KeyDown`] source and set the `Filter` property to `A`. 
- Insert a [`CreateMessage`] operator and configure these properties:
   - `Payload` - Select [`PlaySoundOrFrequencyPayload`].
   - `PlaySoundOrFrequency` - Set the desired frequency in Hz (e.g. 1000).
- Insert a [`MulticastSubject`] operator named `SoundCard Commands`.

On another branch:

- Insert a [`KeyDown`] source and set the `Filter` property to `S`.
- Insert a [`CreateMessage`] operator and configure these properties:
   - `Payload` - Select [`StopPayload`].
   - `Stop` - Set the value to 1 (any non-zero value stops playback).
- Insert a [`MulticastSubject`] operator named `SoundCard Commands`.

Run the workflow, press the <kbd>A</kbd> key to play the sound, and press the <kbd>S</kbd> key to stop playback.

> [!WARNING]
> The [`Stop`] register can only be used to stop playback from the internal sine wave generator, not sounds from the onboard memory.

<!--Reference Style Links -->
[`CreateMessage`]: xref:Harp.SoundCard.CreateMessage
[`Device`]: xref:Harp.SoundCard.Device
[`HarpMessage`]: xref:Bonsai.Harp.HarpMessage
[`KeyDown`]: xref:Bonsai.Windows.Input.KeyDown
[`MulticastSubject`]: xref:Bonsai.Expressions.MulticastSubject
[`PlaySoundOrFrequency`]: xref:Harp.SoundCard.PlaySoundOrFrequency
[`PlaySoundOrFrequencyPayload`]: xref:Harp.SoundCard.CreatePlaySoundOrFrequencyPayload
[`Stop`]: xref:Harp.SoundCard.Stop
[`StopPayload`]: xref:Harp.SoundCard.CreateStopPayload