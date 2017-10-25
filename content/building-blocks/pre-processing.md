---
title: "Pre-Processing"
date: 2017-10-24T14:49:15-04:00
weight: 2
---

We define 'pre-processing' quite broadly as 'operations carried out on seismic traces'. There are several modules you can make use of to assemble your own pre-processing workflow. Such modules may include:

- `Signal processing`
- `Window selection`
- `Measuring fit between observed and synthetic seismograms`
- `Generating adjoint sources`

### Signal processing

Seismic signal processing, is a subfield of digital signal processing (DSP). Though there are many tools developed for this purpose, the basic operations are the same.

Here we listed some code examples based on [Obspy](https://github.com/obspy/obspy/wiki). The python code example is pretty self-explanatory.

#### 1. Initial processing
In this category we include simple operations such as demeaning, detrending and tapering.

```python
from obspy import read
st = read("/path/to/data")
st.detrend("linear")
st.detrend("demean")
st.taper(max_percentage=0.05, type="hann")
```

[include figures]

#### 2. Instrument response removal
Seismic data are often provided as raw output from a seismometer.  In such cases, the response of the instrument must be removed before the data can be used in any meaningful way. Also, filtering will happen at the same time when we remove the instrument response.

```python
from obspy import read_inventory
## Corner frequency of filter(Hz)
pre_filt = [0.013, 0.016, 0.033, 0.045]
## read in stationxml file
inv = read_inventory("/path/to/stationxml/file")
st.attach_inventory(inv)
st.remove_response(output="DISP", pre_filt=pre_filt, zero_mean=False, taper=False)
## you may want to demean, detrend and taper again
st.detrend("linear")
st.detrend("demean")
st.taper(max_percentage=0.05, type="hann")
st.interpolate(sampling_rate=sampling_rate, starttime=starttime, npts=npts)
```

#### 3. Bandpass filtering
For synthetic data, we need to banpass filter it into the same period band as observed data.

```python
## Bp code here
```
[include code and figures]


### Window selection
In regional and global inversion, comparison of observations and synthetics within carefully selected windows can be used to allow expertise with classical body wave and surface wave phases to be brought to bear in the waveform inversion framework.  In this approach, window selection is made on the basis of fit between observations and synthetics, with windows chosen only where the fit is good.  In our approach, relatively few windows are chosen at the beginning.  As the inversion progresses and data fit improves, more and more are added so that eventually the whole waveform is included. 

![window selection](../images/window_selection_demo.png?classes=shadow&width=600px)
[*Figure Credit to Pyflex]

**Windows selection tools**
  * [pyflex](https://github.com/krischer/pyflex): python export of FLEXWIN
  * [FLEXWIN](https://github.com/geodynamics/flexwin): original version of FLEXWIN

Outside of regional and global inversion, record sections may be more complex, window selection may be less stable, and other strategies for mitigating nonlinearity and nonconvexity may be preferred.

### Measuring fit between observed and synthetic seismograms
[click to show sample code]()
[click to show sample figures]()


### Generating adjoint sources
Different kinds of adjoint sources can be calculated based on the measurements.

**Ajoint sources creation tools**
  * [Pyadjoint](https://github.com/krischer/pyadjoint)
  * [Measure_adj](https://github.com/wjlei1990/seismo-MEASURE_ADJ)

