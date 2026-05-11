## Harp Soundcard

This is a high performance sound card with two output channels using 24 bits DACs at 192kHz sample rate.

![HarpSoundcard](./images/OEPS-SoundCard.png){width=450}

The SoundCard is an open-source, high-fidelity audio device specifically designed for behavioral research experiments. It supports audio frequencies up to 80kHz, making it suitable for experiments with species that communicate ultrasonically. 


It can be triggered with low latency, conforms to the [Harp](https://harp-tech.org/articles/about.html) protocol for synchronization, and integrates with [Bonsai](https://bonsai-rx.org/) for experiment acquisition and control. For a full characterization, see the [publication](https://doi.org/10.1016/j.ohx.2024.e00555).

Assembled units are available from the [Open Ephys store](https://open-ephys.org/harp), or build your own using the [hardware design files](https://github.com/harp-tech/device.soundcard). 

### Key Features

* Internal memory to store sounds, enabling low-latency sound delivery
* Pre-selected sounds can be triggered using an external TTL
* Internal wave generator allows the user to configure a pure tone without loading a sound file

### System Components

To play sounds, the SoundCard must be connected to external amplifiers and speakers. The [Harp Audio Amplifier](./articles/audio-peripherals.md#harp-audio-amplifier) is specifically designed to pair with the SoundCard. 

![Harp SoundCard Connections](./images/connection.svg){width=450}

*<small>Adapted from [Silva et al. (2024)](https://doi.org/10.1016/j.ohx.2024.e00555). CC BY 4.0.</small>*

### Specs

- Maximum sampling rate: 192 kHz
- Number of channels: 2
- Bit depth: 24 bits
- Input voltage: 12 V DC
- Output voltage: 2 V rms
- Flash memory: 30 indices, 8 MB per index (2 million samples)
- Sound duration: 10.922 s at 96 kHz sample rate, or 5.461 s at 192 kHz sample rate
- Timestamp resolution: 32 µs
- Digital outputs: 3 (3.3V or 5V)
- Digital inputs: 3 (5V tolerant)
- Analog inputs: 2 (3.3V max - 5V tolerant)

### Hardware Compatibility

| HW Version | Board                    | Board HW Version  | Notes                             |
| ---------- | ------------------------ |------------------ | --------------------------------- |
| **All**    | [Peripheral.AudioAmp][1] | >= 2.0            |                                   |

[1]: https://github.com/harp-tech/peripheral.audioamp

### Firmware Compatibility

| FW Version | Board                 | Board HW Version | Notes                                   |
| ---------- | --------------------- | ---------------- | --------------------------------------- |
| **>= 2.2** | [Device.SoundCard][2] | >= 1.0           | Bpod serial communication not supported |
| **<= 2.2** | [Device.SoundCard][2] | >= 1.0           |                                         |

[2]: https://github.com/harp-tech/device.soundcard

### Licensing

Each subdirectory will contain a license or, possibly, a set of licenses if it involves both hardware and software.

### Acknowledgments

Hardware design and GUI contributed by [Champalimaud Foundation](https://www.cf-hw.org/), Bonsai interface by [Neurogears](https://neurogears.org/), and documentation by [Open Ephys](https://open-ephys.org/).