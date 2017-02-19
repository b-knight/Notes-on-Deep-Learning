# Notes on Recurrent Neural Networks (RNN) & Long Short-Term Memory (LSTM) Models 
RNNs are designed to handle sequences of information. Situating an input within the context of a sequence allows the RNN to utilize context to better identify patterns in the data. These sequences can be of a time series nature (e.g. stills from a video feed), but need not be. Examples include sequences of letters or words, item IDs within a shopping cart, etc. <br>

To build a RNN, let's get some terminology under our belts. Let *X* and *Y* represent our inputs, and outputs respectively. Let *h* represent the hidden layer subscripted by *t* - the element within the sequence. In this fashion,


![](https://github.com/b-knight/Notes-on-Deep-Learning/blob/master/Images/RNN.gif)

<div align="center">
<img src="https://github.com/b-knight/Notes-on-Deep-Learning/blob/master/Images/RNN.gif" align="middle" width="453" height="113" />
</div>

## References
### Recurrent Neural Networks & LSTM

- Karpathy, Andrej. [MachineLearner]. (2016, June 14th). *CS231n Lecture 10 - Recurrent Neural Networks, Image Captioning, LSTM*. Retrieved from https://www.youtube.com/watch?v=iX5V1WpxxkY.

- Nguyễn, Giang. (2013, March 10th). *7 - 5 - Long-term Short-term-memory*. Retrieved from https://www.youtube.com/watch?v=izGl1YSH_JA.

- Olah, Chris. (2015, August 27th). *Understanding LSTM Networks*. Retrieved from http://colah.github.io/posts/2015-08-Understanding-LSTMs/.
