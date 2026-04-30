## Visualize data with harp-python

> [!NOTE]
> This article assumes basic familiarity with [Python](https://www.python.org/) and requires a Python environment with [`pandas`](https://pandas.pydata.org/), [`matplotlib`](https://matplotlib.org/) and [harp-python](installation.md#harp-python) installed.

The harp-python library provides a low-level interface to import and manipulate data stored in the Harp data format. When imported, the data is stored in pandas DataFrames. The following example demonstrates how to read data from a specific register:

```python
# Import harp-python for data interface and pandas for simple plotting
import harp
import pandas as pd 

# Create a device object with harp reader
device = harp.create_reader("./SoundCard.harp")

# Read data from a specific register
play_sound_or_frequency_df = device.PlaySoundOrFrequency.read()

# Inspect dataframe
print(play_sound_or_frequency_df.head())

# Plot sound onset times
pd.Series(play_sound_or_frequency_df).plot()
```

[!INCLUDE [](version-footer.md)]