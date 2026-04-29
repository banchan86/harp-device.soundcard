---
uid: Harp.SoundCard.CreatePlaySoundOrFrequencyPayload
---

## Play sound index

Sounds can be played from the `SoundCard` onboard memory by specifying the sound index in the [`PlaySoundOrFrequency`] register. Sound duration and amplitude are determined by the properties of the stored waveform.

:::workflow
![Play Sound Index Keydown](../workflows/playsound-indexkeydown.bonsai)
:::

- Insert a [`KeyDown`] source and set the `Filter` property to `A`. 
- Insert a [`CreateMessage`] operator to construct a [`HarpMessage`] command and configure these properties:
    - `Payload` - Select [`PlaySoundOrFrequencyPayload`] from the property dropdown menu.
    - `PlaySoundOrFrequency` - Set the index of the sound you want to play from the `SoundCard` onboard memory (2-31).
- Insert a [`MulticastSubject`] operator named `SoundCard Commands`.

Run the workflow and press the <kbd>A</kbd> key to play the sound. 

> [!TIP]
> You can terminate the sound early by playing an empty sound index.

## Play pure tone

Pure tones can be played from the `SoundCard` internal sine wave generator by specifying the frequency in the [`PlaySoundOrFrequency`] register. Sounds will be played continuously at the device's max amplitude until stopped.

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
   - `Stop` - Set the value to 1 (or any other value than 0).
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