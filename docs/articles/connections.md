## SoundCard Device Pinout
![Harp SoundCard Device Pinout](../images/soundcard-devicepinout.svg){width=600}

* 1x reset button [tactile switch]
* 3x general purpose digital outputs (3.3V or 5V) (OUT0-OUT2) [screw terminal]
* 3x general purpose digital inputs (5V tolerant) (IN0-IN2) [screw terminal]
* 2x analog inputs (3.3V máx - 5V tolerant) (ADC0-ADC1) [screw terminal]

## Wiring Diagram for Speaker and Amplifier

![Harp SoundCard Connections](../images/connection.jpg){width=450}

*<small>Single channel connection diagram with Harp Audio Amplifier and attached speaker. Reproduced from [Silva et al. (2024)](https://doi.org/10.1016/j.ohx.2024.e00555). CC BY 4.0.</small>*

**Amplifier** - The `SoundCard` requires an external amplifier. For high-fidelity applications, consider using the [Harp Audio Amplifier](https://github.com/harp-tech/peripheral.audioamp).

**Speaker** - The choice of speaker depends on the amplifier. For the `Harp Audio Amplifier`, any speaker with an impedance from 4 to 8 ohms can be used. The XT25SC90-04 (Peerless by Tymphany) has been tested and has a good frequency response up to 80 kHz.