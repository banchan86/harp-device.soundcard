## Analysis

> [!NOTE]
> This article assumes basic familiarity with [Python](https://www.python.org/). It requires a Python environment with [harp-python](installation.md#harp-python) and [`matplotlib`](https://matplotlib.org/) installed.

The `harp-python` library imports data stored in the Harp binary format as [pandas](https://pandas.pydata.org/) DataFrames, which can then be analyzed with any `pandas` compatible plotting or analysis library. 

The following example demonstrates how to read and plot data from a specific register.

```python
# Import harp-python library
import harp

# Create a device object with harp reader
device = harp.create_reader("./SoundCard.harp")

# Read data from a specific register
play_sound_or_frequency_df = device.PlaySoundOrFrequency.read()

# Inspect DataFrame
print(play_sound_or_frequency_df.head())

# Plot sound onset times
play_sound_or_frequency_df.plot()
```

[!INCLUDE [](version-footer.md)]