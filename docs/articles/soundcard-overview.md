## SoundCard

High performance sound card with two output channels using 24 bits DACs at 192kHz sample rate.

![Harp SoundCard](../images/OEPS-SoundCard.png){width=450}

### Key Features

- Internal memory to store sounds, enabling low-latency sound delivery
- Pre-selected sounds can be triggered using an external TTL
- Internal wave generator allows the user to configure a pure tone without loading a sound file

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
- Analog inputs: 2 (5V max)

### Benchmarks

- THD: -111 dB (1 kHz @ 2 V rms)
- Noise Floor: 20 µV rms | -94 dB (20 Hz – 80 kHz)
- SNR: 100 dB | 113 dBA (20 Hz – 80 kHz @ 2 V rms)

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

[!INCLUDE [](version-footer.md)]