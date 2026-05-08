## Harp Device Pattern

To control the SoundCard with Bonsai, we will setup a Harp [device pattern](https://harp-tech.org/articles/operators.html#device-pattern). This will initialize the device and provide hooks to send commands as well as receive messages from the SoundCard using the [Harp communication protocol](https://harp-tech.org/protocol/BinaryProtocol-8bit.html). It will also [log data](acquisition.md) from the device.

:::workflow
![SoundCard Device Pattern](../workflows/harp-devicepattern.bonsai)
:::

- Open Bonsai from the Windows Start menu.
- Hover over the workflow cell above, and click on the "Copy" icon on the top right. 
- Paste the workflow into Bonsai.

> [!TIP]
> If your workflow does not look the one above, make sure that the [Harp.SoundCard`](./installation.md#bonsai) package is installed.

- Click on the [`SoundCard (Device)`] operator and set the `PortName` property to the communications port for the device (e.g. COM8).
- Click on the [`SoundCardDataWriter (DeviceDataWriter)`] operator and set the `Path` property for the name and location of the save file (e.g. `Data\SoundCard.harp`).
- Press the "Start" button in Bonsai to run the workflow.

If the connection is successful, the green LED indicator light on the device will cycle on and off with a period of 2 secs to indicate that its communicating with Bonsai. If it does not change or an error appears, check out the [troubleshooting](troubleshooting.md) guide. 

Otherwise, move on to the [play sound](play-sound.md) article to play your first sound!

[!INCLUDE [](version-footer.md)]

<!--Reference Style Links -->
[`SoundCard (Device)`]: xref:Harp.SoundCard.Device
[`SoundCardDataWriter (DeviceDataWriter)`]: xref:Harp.SoundCard.DeviceDataWriter