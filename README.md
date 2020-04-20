# SynCAN Dataset 

The goal of this dataset, which we call SynCAN Dataset (Synthetic CAN Bus Data), is to provide a benchmark to evaluate and compare different CAN Intrusion Detection Systems (IDS) on different attack scenarios in the signal space. It should be used to train an IDS in an unsupervised manner and evaluate its performance on normal an anomolous data. This data set was created as supplementary material for the paper <a href="https://ieeexplore.ieee.org/document/9044377">CANet: An Unsupervised Intrusion Detection System for High Dimensional CAN Bus Data</a>.

## Data Description

If you plan to use this data set for your own research, please cite:

@ARTICLE{9044377,  <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;author={M. {Hanselmann} and T. {Strauss} and K. {Dormann} and H. {Ulmer}}, <br> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;journal={IEEE Access},  <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;title={CANet: An Unsupervised Intrusion Detection System for High Dimensional CAN Bus Data},   <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;year={2020},  <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;volume={8},  <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;number={},  <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pages={58194-58205},<br>
}

@article{hanselmann2019canet, <br>
title={CANet: An Unsupervised Intrusion Detection System for High Dimensional CAN Bus Data},<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;author={Hanselmann, Markus and Strauss, Thilo and Dormann, Katharina and Ulmer, Holger},<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;journal={arXiv preprint arXiv:1906.02492},<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;year={2019}<br>
}

In the following, a short description of the data set is given. We refer to the <a href="https://arxiv.org/abs/1906.02492">paper </a> for more details. 

The data set consists of a training data set and six test data sets that all contain the following columns: 

Label,  ID,  Time,  Signal1 _of_ID,  Signal2 _of_ID,  Signal3 _of_ID,  Signal4 _of_ID

The column 'Label' indicates whether the data row is to be considered as normal (Label=0) or as intrusion (Label=1). Since we assume that the IDS is trained in an unsupervised manner, the label on the training data set is always set to zero, meaning that there are no intrusions (the column is just there for a consistent representation of the data).

In the column 'Time' the time stamp of the current message is represented in milliseconds. 

The column 'ID' contains the identifiers for the IDs that are 'id1', ..., 'id10'.

The columns 'Signal1_of_ID', ... , 'Signal4_of_ID' contain the actual signal values. Note, that different IDs have a different number of signals and that in general the signals from different IDs represent different signals, e.g., Signal1_of_ID of id0 and Signal1_of_ID of id5 are different. 
In the data set the number of signals of the IDs id1, ..., id10 is: 

(2, 3, 2, 1, 2, 2, 2, 1, 1, 4) 

The data set consists of the training data and six test data sets. The four training data sets (train_1.zip, ..., train_4.zip)  should be concatenated in order to obtain the entire training data set. The test files are:

1. test_normal.zip: This data set consists entirely of normal data i.e. no intrusions are present. Hence, the label is equal to zero for all data in this file. It can be used to evaluate the performance of an IDS on unperturbated data.
2. test_plateau.zip: A signal is overwritten and set to a constant value over a period of time. 
3. test_continuous.csv: A signal is overwritten in such a way that it drifts slowly away from its true value. 
4. test_playback.zip: Over a period of time, a signal value is overwritten with a recorded time series of values of that same signal. 
5. test_suppress.zip: The attacker prevents a ECU from sending messages, for example, by turning it off over a period of time. This kind of attack implies that messages of some particular ID do not appear in the CAN traffic for some period of time.
6. test_flooding.zip: The attacker sends messages of a particular existing ID with high frequency to the CAN bus.

In test data 2-6, multiple attacks of the given type are injected. Each attack is followed by several seconds of normal traffic. An attack is always on a single signal or a signal ID over a period of time. During each attacked time interval, the label of all IDs is set to one. 

## License (Abstract)

This SynCAN Dataset is made freely available to academic and non-academic entities for non-commercial purposes such as academic research, teaching, scientific publications, or personal experimentation simulations only, but not in the field, as this dataset has not been tested for field use. Permission is granted to use the data given that you agree to our [license terms](https://github.com/etas/SynCAN/blob/master/License%20terms.txt).
