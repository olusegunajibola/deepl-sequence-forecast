# deepl-sequence-forecast


## Introduction

In this project, we design and code a panel of k predictors of the type Ψ(M,1) with an MLP, LSTM and
RNN each constructed and trained to predict one symbol of the sequence future, taking as input M
symbols of the sequence past.

The algorithm is as follows:

Ψ_1: input [s(t-M), s(t-M+1), ..., s(t- 1 )] output s(t)

Ψ_2 : input [s(t-M- 1 ), s(t-M), ..., s(t- 2 )] output s(t)

...

Ψ_k: input [s(t-M-(k-1) ),..., s(t-M-k)] output s(t).

Having done this, we proceeded to create, code, and train another set of deep models i.e new MLP
layer that takes as input the k predictions of your predictors and outputs one symbol. We do the same
for LSTM and RNN.

## Methodology

To achieve our objectives, we ensured that we do not use the entire set of our data. This enables us
to measure the accuracy of all predictors Ψ_k respectively.
![methodology](https://user-images.githubusercontent.com/58126151/211492206-a5e2981d-a617-44ff-9d68-508e34ce2d16.png)
The image above demonstrates our idea where the original dataset are numbers from 1 to 20 and we
try to predict the last figure i.e 20 using 4 predictors. We note that the first predictor (i.e k=1) has the
most recent data which leads to our desired forecast i.e 20. Consequently, the kth predictor (in this
instance k=4) has more information from the past and it has less recent information that leads to the
desired forecast.

We apply this methodology to the pi digit numbers and Italia positive giornaliero data.


## Data Visualization

We first make a preliminary visualization of our datasets to see the evolution.

The image above shows us the evolution of covid occurrence in Italy over about 700 days. This is the
Italia positive giornaliero data. We notice a peak around the 300th day. Our desire is to predict the last
day in the data i.e **15,9317**.

Secondly, the data we have is the pi digits i.e 3.14... The visualization above depicts the first 1,
digits after removing ‘3.’. As a result, our desire is to predict the 1000th digit i.e **9**.


## Models, Analysis and Results

For both datasets, we build deep learning models of MLP, RNN and LSTM of 20 predictors.

### MLP – COVID DATA

The LSTM earliest predictor (1, 2, 3) models on the covid data gave us figures that are very close to
the actual value we were looking for. Furthermore, the most accurate predictor was the 9th predictor.
Nevertheless, we begin to have figures that were consistently far off the expected prediction from the
14th predictor. Lastly, combining the prediction by all the predictors gave us a prediction that was
above the expected prediction.

### MLP – PI NUMBERS

This time around, the LSTM gave us negative values in prediction. This is notable in the 1st, 2nd, and 4th
predictor. The third predictor was the only one that gave us the best prediction even though the 14th
predictor came close alongside the prediction made by the combination of the predictors after all
negative predictions have been removed.


### LSTM – PI NUMBERS

This time around, the LSTM 8th predictor gave us the closest figure to the actual value we are looking
for. Nevertheless, it only had one negative value predictions (for the 13th predictor). Also, the
prediction by the combination of all predictors gave us our second best prediction. We removed the
negative predictor to achieve this. The best predictor was the 8th.

### LSTM – COVID DATA

Just as observed in the MLP model where the prediction power became poor, we notice the same
here the further we go away from s(t). In this instance, the 12th to 20th predictors gave awful results.
Nevertheless, the 2nd and 11th predictors performed best here, whereas the combination of all
predictors gave a fair output.


### RNN – COVID DATA

Again, consistent declines are visible after the 12th predictor. The 4th predictor was the best.
Nevertheless, the first 5 predictors were good enough to be considered as well. Finally, the
combination of prediction by the predictors to make a forecast gave us a value that we can consider
to be somewhat off-mark. Please note that this model did not output negative values, the labelling
was wrong. It should be **average of predictors** instead.

### RNN – Pi Digits

The RNN model built gave a prediction that was way above the expected output in the 4th predictor.
The best predictor in this case is the prediction gotten by the combination of values from all predictors.


## Conclusion

We made an aggregate of plots of the respective models in the two datasets. This enables us to come
to some valid conclusion as we move from one predictor to the other in order to achieve our
forecasting goal. For the COVID and Pi data, we combine the predictions from the three models and
compare.

### COVID Data

Collectively, for the first two predictors, we had values that are close to the actual value for all models
under consideration. Also, from the 14th predictor, we notice consistent declines. From this graph, we
can conclude that the MLP model performs best for sequence prediction on the COVID dataset given
the algorithm under study as it was consistent in its forecast at every predictor.

### Pi Digits

We notice here that both the LSTM and MLP predictors gave negative predictions (amongst their pre).
Whereas the RNN predictors gave us a value that was way too high in its 4th predictor. Nevertheless,
MLP once more gave the best predictors looking at its 3rd and 14th predictor.

Given the algorithm under study, we conclude that the MLP model is the best for the datasets.
