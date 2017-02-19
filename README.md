# Recurrent Neural Networks (RNN) & Long Short-Term Memory (LSTM) Models 
**Benjamin S. Knight**, February 18th, 2017

While [neural nets](https://en.wikipedia.org/wiki/Artificial_neural_network) excel at pattern recognition, certain types of problems require utilizing information from an observation's broader context. Deciphering hand-written text in cursive is one such example. The task of identifying an individual character becomes far more tractable if we can also leverage classifications of the preceeding and subsequent characters as well. With these types of highly contextualized problems, pattern recognition effectively becomes sequence recognition. These sequences can be of a time series nature (e.g. stills from a video feed), but need not be. Examples include sequences of letters, words, or even items within a shopping cart.

Recurrent neural networks (RNNs) handle such sequences through the use of dedicated hidden layers.
To build a RNN, let's get some terminology under our belts. Let *X* and *Y* represent our inputs, and outputs respectively. Let *h* represent the hidden layer subscripted by *t* - the element within the sequence. In this fashion,

<p align="center"><b>Figure 1: Derivation of the RNN Weights</b></p>
<div align="center">
<img src="https://github.com/b-knight/Notes-on-Deep-Learning/raw/master/Images/RNN_Formulas.png" alt="The formulas used for creating the arrays of weights used by the recurrent neural network." width="506" height="118">
</div>

<p align="center"><b>Figure 2: A Many-to-One RNN with Sequences Three Elements in Length</b></p>
<div align="center">
<img src="https://github.com/b-knight/Notes-on-Deep-Learning/raw/master/Images/RNN.gif" alt="Throughput of a recurrent neural net." width="740" height="385">
</div>

<p align="center"><b>Figure 3: Required Inputs and Data Volume of a Standard Neural Network Versus a RNN</b></p>
<div align="center">
<img src="https://github.com/b-knight/Notes-on-Deep-Learning/raw/master/Images/Vector_Length.jpg" alt="The data volume and computational cost or a recurrent neural network far exceeds that of a conventional neural network." width="640" height="356">
</div>




## Long Short Term Memory (LSTM) Networks

<p align="center"><b>Figure 4: Walk-Through of a LSTM Cell </b></p>
<div align="center">
<img src="https://github.com/b-knight/Notes-on-Deep-Learning/raw/master/Images/LSTM.gif" alt="Walk-Through of a LSTM Cell">
</div>


### References

- Karpathy, Andrej. [MachineLearner]. (2016, June 14th). *CS231n Lecture 10 - Recurrent Neural Networks, Image Captioning, LSTM*. Retrieved from https://www.youtube.com/watch?v=iX5V1WpxxkY.

- Nguyễn, Giang. (2013, March 10th). *7 - 5 - Long-term Short-term-memory*. Retrieved from https://www.youtube.com/watch?v=izGl1YSH_JA.

- Olah, Chris. (2015, August 27th). *Understanding LSTM Networks*. Retrieved from http://colah.github.io/posts/2015-08-Understanding-LSTMs/.
