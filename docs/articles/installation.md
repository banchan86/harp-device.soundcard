## Installation

These steps are only required the first time you connect the Harp SoundCard to a new computer and if you plan to use the specific functionality.

### WinUSB 

Install the WinUSB driver if you plan to upload sounds to the onboard memory:

[]

- Download and launch [Zadig](https://zadig.akeo.ie/).
- Connect the USB Micro-B cable to the computer.
- Select the "Harp Sound Card" from the list. If the device is not available, go to "Options" > "List All Devices".
- Select the "WinUSB" driver and click "Install Driver".

### Bonsai

Install Bonsai to control the SoundCard:

- Install [Bonsai](https://bonsai-rx.org/docs/articles/installation.html).
- Install the `Harp.SoundCard` package by searching for it in the [Bonsai package manager](https://bonsai-rx.org/docs/articles/packages.html).
- Install the `Bonsai.Windows.Input` package from the Bonsai [package manager](https://bonsai-rx.org/docs/articles/packages.html) to follow along with the examples in the documentation.

### SoundCard GUI
Waveforms can be generated and uploaded to the `SoundCard` in Bonsai. Optionally, you can use the [Harp SoundCard GUI](https://bitbucket.org/fchampalimaud/downloads/downloads/Harp_Sound_Card_v1.3.2.zip) as a standalone interface for waveform management. This requires the [LabVIEW runtime](https://bitbucket.org/fchampalimaud/downloads/downloads/Runtime-1.0.zip) to be installed first.

### Firmware

| Tag | Description |
| - | - |
| SoundCard-* | Firmware for the sound card's microcontroller (8 bits processor) |
| SoundCard.PIC32-* | Firmware for the sound card's 32 bits processor |

#### Firmware Update

1 - Install the [Harp Converto to CSV](https://bitbucket.org/fchampalimaud/downloads/downloads/Harp_Convert_To_CSV_v1.8.3.zip).

2 - Open the Harp Convert to CSV application and write *bootloader* under List box on the Options tab

3 - Select the correspondent COM port and then select the firmware to be loaded for both microcontrollers 

[!INCLUDE [](version-footer.md)]