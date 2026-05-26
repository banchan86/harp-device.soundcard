## Configure Digital Input

The digital input channels on the SoundCard can be configured to report TTL signals coming from other devices or trigger sound index playback.

For the examples in this article, connect `DI0` (5 V tolerant) and `GND` on the SoundCard to a TTL output from another device.

(Placeholder for wiring diagram)

The complete workflow is shown below:

:::workflow
![Configure Digital Input Top Level](../workflows/configureDI-toplevel.bonsai)
:::

[!INCLUDE [](../apidoc/configureDI-triggersound.md)]

[!INCLUDE [](version-footer.md)]