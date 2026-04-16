## Harp Soundcard
This is a high performance sound card with two output channels using 24 bits DACs at 192kHz sample rate. 

![HarpSoundcard](./images/pcb.png)

### Key Features

* Internal memory to store sounds, enabling low-latency sound delivery
* Pre-selected sounds can be triggered using an external TTL
* Internal wave generator allows the user to configure a pure tone without loading a sound file
* Stereo 24 bit @ 192 kHz maximum sampling rate outputs
* THD: -111dB (1 kHz @ 2 V rms)
* Noise Floor:	20 µV rms | -94 dB (20 Hz – 80 kHz)
* SNR:	100 dB | 113 dbA (20 Hz – 80 kHz @ 2 V rms)

### Connectivity

* 1x clock sync input (CLKIN) [stereo jack]
* 1x USB (for computer communication) [USB Mini-B]
* 1x micro USB (for sounds loading) [USB Micro-B]
* 1x 12V supply [barrel connector jack]
* 1x reset button [tactile switch]
* 1x output for the left channel [RCA]
* 1x output for the right channel [RCA]
* 3x general purpose digital outputs (3.3V or 5V) (OUT0-OUT2) [screw terminal]
* 3x general purpose digital inputs (5V tolerant) (IN0-IN2) [screw terminal]
* 2x analog inputs (3.3V máx - 5V tolerant) (ADC0-ADC1) [screw terminal]

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