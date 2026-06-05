## Adjust Volume

The [`PlaySoundOrFrequency`] register in the [play sound](play-sound.md) article will play the sound at the amplitude of the stored waveform or at maximum amplitude for the pure tone frequency generator. This article will demonstrate how to dynamically lower the amplitude with other registers.

> [!NOTE]
> The playback amplitude of stored waveforms can be attenuated but not amplified. Upload waveforms at full 24-bit depth to maximize the volume.

The complete workflow is shown below:

:::workflow
![Adjust Volume Top Level](../workflows/adjustvolume-toplevel.bonsai)
:::

[!INCLUDE [](../apidoc/attenuate-sound.md)]

[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->

[`PlaySoundOrFrequency`]: xref:Harp.SoundCard.PlaySoundOrFrequency