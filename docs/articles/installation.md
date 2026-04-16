# Installation

- Install the WinUSB driver if you plan to upload sounds to the onboard memory:
   - Download and launch [Zadig](https://zadig.akeo.ie/).
   - Connect the USB Micro-B cable to the computer.
   - Select the "Harp Sound Card" from the list. If the device is not available, go to "Options" > "List All Devices".
   - Select the "WinUSB" driver and click "Install Driver".
- Install [Bonsai](https://bonsai-rx.org/docs/articles/installation.html).
- Install the `Harp.SoundCard` package by searching for it in the [Bonsai package manager](https://bonsai-rx.org/docs/articles/packages.html).

Waveforms can be generated and uploaded to the `SoundCard` in Bonsai. Optionally, you can use the [Harp SoundCard GUI](https://bitbucket.org/fchampalimaud/downloads/downloads/Harp_Sound_Card_v1.3.2.zip) as a standalone interface for waveform management. This requires the [LabVIEW runtime](https://bitbucket.org/fchampalimaud/downloads/downloads/Runtime-1.0.zip) to be installed first.

[!INCLUDE [](version-footer.md)]