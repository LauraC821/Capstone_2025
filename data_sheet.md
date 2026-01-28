# Datasheet

## Motivation
The data set was created for a black box optimisation (BBO) challenge, where the aim was to identify the maximum of 8 unknown functions.
 
## Composition
For each unknown function, the dataset consists of input–output pairs corresponding to past queries and their observed results. 
- Inputs: Each query is an array of real-valued inputs, where the length is equals the dimension of the unknown function. Each value lies between 0 and 1, specified to six decimal places.
- Outputs: Each query produces a single real valued output.

The data is stored within the Data folder, which is split into three separate sections:

| Folder Name | Description |
| --- | --- |
| initial_data | Data provided at the start of the optimisation challenge |
| submission_data | Data for submitted queries in txt files |
| processed_data | Input(X) and output(y) data transformed from .txt to .npy files formats |

## Collection process
The initial dataset was provided at the start of the challenge.
Subsequent queries for submissions were typically selected using Bayesian optimisation with a Gaussian Process surrogate model.
After each weekly submission, the observed query results were returned and used to guide the selection of the next set of queries.

## Preprocessing
Only data for the first function was preprocessed, the inputs rotated, and the outputs scaled. The transformed data is intended for use when training surrogate functions that do not manipulate the inputs further. Where a surrogate model transforms inputs e.g. with input warping, the original data should be used.
 
## Distribution and Maintenance
The dataset, without any preprocessing, is available within the Data folder of this GitHub repository. The dataset is not actively maintained.