# MIMIC-PAP-Dataset
Dataset of PAP waveforms with numerics from MIMIC-III.

The waveforms were derived from the [MIMIC-III Waveform Database Matched Subset](https://www.physionet.org/physiobank/database/mimic3wdb/matched/) by searching for records that include:

* PAP waveform.
* Numerics: systolic/diastolic/mean PAP and heart rate.

Records follow the [MIMIC-III Waveform Database Matched Subset](https://www.physionet.org/physiobank/database/mimic3wdb/matched/) standard notation:

* pXX/pXXNNNN/pXXNNNN-YYYY-MM-DD-hh-mm

Where XXNNNN is the matching MIMIC-III Clinical Database Subject_ID, and YYYY, MM, DD, hh, and mm are the surrogate year, month (01-12), and day (01-31), and the real hour (00-23) and minute (00-59), derived from the starting date and time of day of the record. The surrogate dates match those of the corresponding MIMIC-III Clinical Database records.

Additionally, records were limited to the first 6000 seconds and included only if they met the following criteria:

* All numerics had at least 100 values (Numeric values were recorded every minute. Thus, for a 6000 second waveform record there should be 6000/60 = 100 numeric values).
* The PAP waveform contained values (to avoid all NaN waveforms).
* The PAP waveform yielded at least 1000 onsets using the [wabp](https://www.physionet.org/physiotools/matlab/wfdb-app-matlab/html/wabp.html) function with no more than a 10 second duration between consecutive onsets. This is to ensure the waveform quality is good enough for any further processing and that there will be no excessively large beats due to [wabp](https://www.physionet.org/physiotools/matlab/wfdb-app-matlab/html/wabp.html) missing some onsets.

The dataset can be loaded using Matlab and records are in the following format:

* A single variable cell array called signals containing:
  * 1: PAP waveform (in mmHg)
  * 2: Systolic PAP (in mmHg)
  * 3: Diastolic PAP (in mmHg)
  * 4: Mean PAP (in mmHg)
  * 5: Heart Rate (in bpm)
  * 6: PAP waveform time (in seconds)
  * 7: Numerics time (in seconds)
  * 8: PAP waveform sampling frequency (in Hz)
  * 9: Numerics sampling frequency (in Hz)
