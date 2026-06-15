## Play Sounds

The SoundCard supports playback of waveforms stored in its onboard memory. It also includes an internal sine wave generator for pure tones. The following article will walk through how to play these sounds in Bonsai using key presses as an example trigger.

The complete workflow is shown below:

:::workflow
![Play Sound Top Level](../workflows/playsound-toplevel.bonsai)
:::

> [!WARNING]
> When adding these operators to the workflow from the Bonsai [Toolbox](https://bonsai-rx.org/docs/articles/editor.html?tabs=mouse-controls#toolbox), make sure to use the device-specific versions, e.g. `Device (Harp.SoundCard)` instead of `Device (Harp)`. If correctly selected, the names of these operators in the workflow panel will change to reflect either the name of the device or the selected register/payload.

[!INCLUDE [](../apidoc/play-sound-index.md)]

[!INCLUDE [](../apidoc/play-frequency.md)]

### Alternative: Controlling Sound Playback with Other Events

You can replace [`KeyDown`] with other operators to trigger sound playback on other events in Bonsai.

:::workflow
![Play Sound Index Timer](../workflows/playsound-indextimer.bonsai)
:::

- Replace the [`KeyDown`] source in the previous workflows with a [`Timer`] source and set the `DueTime` property to the number of seconds to wait before playing the sound (e.g. 5).

[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->
[`KeyDown`]: xref:Bonsai.Windows.Input.KeyDown
[`Timer`]: xref:Bonsai.Reactive.Timer