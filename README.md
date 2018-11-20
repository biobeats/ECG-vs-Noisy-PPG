# ECG vs MS Band 2 dataset

# Introduction

This dataset contains a small experiment designed to analyse the error present in Inter Beat Intervals (IBI) reported by the MS Band 2 wearable devices, using an ECG chest strap as ground truth.

This dataset contains PPG and ECG data of 4 subjects (1 additional subject is kept away from the dataset, to be used as test set), every subject was asked to:

* be as still as possible for 10 minute;
* climb up and down a ramp of stairs for 10 minutes;
* be as still as possible for 10 minutes;
* move freely for 10 minutes.

The sensors used are:

* Microsoft Band v2 (PPG and Accelerometer)
* RR data from a Polar H10

## Data format

Data is organised in folders, one folder for each subject. Each folder contains 5 text files:

* ECG.csv: this file contains the RR intervals from the ECG chest strap, it contains 2 columns: *timestamp* and *value*. *timestamp* is the moment when the RR was received by the app from the band; *value* is the RR.
* ACC.csv: this file contains the accelerometer data from the Microsoft Band 2, it contains 4 columns: *timestamp*, *x*, *y*, *z*. *timestamp* is the moment when the data was received by the app; *x*, *y*, and *z* are the accelerometer data.
* PPG.csv: this file contains the PPG data from the MS Band 2, it contains 2 columns: *timestamp* and *value*. *timestamp* contains the moment in time at which the IBI was received by the app from the band; *value* contains the IBI duration. Important: the MS Band 2 sends data over bluetooth, and doesn't send the IBI immediately. As a consequence the *timestamp* should not be used as a strict indication of when the heartbeat happened, only approximately.
* sections.csv: this file contains 2 columns: *offset* and *section*. *Offset* contains the starting time of the section, in seconds, since the beginning of the experiment; *section* contains the name of the section.
* offset.csv: this file contains the estimated difference in time between timestamps from PPG and from ECG, useful to align the two time series.

## References

For an analysis of the propagation of noise in PPG data from IBI to HRV features see http://digital-library.theiet.org/content/journals/10.1049/htl.2017.0039
