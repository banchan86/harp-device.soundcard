### Play Sound Index

Sounds can be played from the `SoundCard` onboard memory by specifying the sound index in the [`PlaySoundOrFrequency`] register payload. Sound duration and amplitude are determined by the properties of the stored waveform.

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

<!--Reference Style Links -->
[`CreateMessage`]: xref:Harp.SoundCard.CreateMessage
[`Device`]: xref:Harp.SoundCard.Device
[`HarpMessage`]: xref:Bonsai.Harp.HarpMessage
[`KeyDown`]: xref:Bonsai.Windows.Input.KeyDown
[`MulticastSubject`]: xref:Bonsai.Expressions.MulticastSubject
[`PlaySoundOrFrequency`]: xref:Harp.SoundCard.PlaySoundOrFrequency
[`PlaySoundOrFrequencyPayload`]: xref:Harp.SoundCard.CreatePlaySoundOrFrequencyPayload