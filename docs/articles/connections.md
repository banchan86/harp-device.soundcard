## Connections

![Harp SoundCard Device Pinout](../images/soundcard-devicepinout.svg){width=600}

**Power** - The device requires a 12 V power supply.

**Soundbank** - This port connects to the device's onboard sound memory bank for uploading of waveforms for sound playback. To use this functionality, install the [WinUSB drivers](./installation.md). Once the sounds have been uploaded, this cable can be disconnected, as it is not required for playing of sounds. 

**Computer** - This port connects to the device's internal controller to control sound playback with [Bonsai](./bonsai-harp.md).

**Harp Clock Input** - The device is compatible with the [Harp](https://harp-tech.org/articles/about.html) family of devices, which can self-synchronize their internal clocks to a precision of +/- 64 us. To use this functionality, connect an output from a [Harp Timestamp Generator](https://github.com/harp-tech/device.timestampgeneratorgen3).

**GPIO** - The general purpose input/output (GPIO) pins can be used to communicate with external devices to trigger sound playback, control volume, etc. The follow pins are provided:

* 3x general purpose digital outputs (3.3V or 5V) (OUT0-OUT2)
* 3x general purpose digital inputs (5V tolerant) (IN0-IN2)
* 2x analog inputs (3.3V máx - 5V tolerant) (ADC0-ADC1)

For more information on how to use them, refer to the [GPIO](trigger-sound.md) article.

**Audio Channels** - The `SoundCard` provides stereo channel outputs that connect with external amplifiers via RCA cables.

## Audio Setup

To play sounds, the `SoundCard` must be connected to external amplifiers and speakers. The wiring diagram below shows how to connect the `SoundCard` for mono channel playback on a single speaker:

![Harp SoundCard Connections](../images/connection.jpg){width=450}

*<small>Reproduced from [Silva et al. (2024)](https://doi.org/10.1016/j.ohx.2024.e00555). CC BY 4.0.</small>*

**Amplifier** - Any external amplifier that accepts line-level RCA inputs is supported. For high-fidelity applications, consider using the [Harp Audio Amplifier](./audio-amp.md) (pictured above).

**Speaker** - The choice of speaker depends on the amplifier's rated impedance and power. For the `Harp Audio Amplifier`, any speaker with an impedance from 4 to 8 ohms can be used. The XT25SC90-04 (Peerless by Tymphany) has been tested and offers a good frequency response up to 80 kHz.