# MIMIC-PAP-Dataset
Dataset of PAP waveforms with numerics from MIMIC-III.

The waveforms were derived from the MIMIC-III Waveform Database Matched Subset by searching for records that include:

* PAP waveforms.
* Numerics: systolic/diastolic/mean PAP and heart rate.

Additionally, records were limited to the first 6000 seconds and included only if they met the following criteria:

* All numerics had at least 100 values (Numeric values were recorded every minute. Thus, for a 6000 second waveform record there should be 6000/60 = 100 numeric values).
* a
