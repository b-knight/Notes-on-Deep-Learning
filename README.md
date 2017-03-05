# Recurrent Neural Networks (RNN) & Long Short-Term Memory (LSTM) Models 
**Benjamin S. Knight**, February 18th, 2017

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; While [neural nets](https://en.wikipedia.org/wiki/Artificial_neural_network) excel at pattern recognition, certain types of problems require utilizing information from an observation's broader context. Deciphering hand-written text in cursive is one such example (Bezerra et al 2012). The task of identifying an individual character becomes far more tractable if we can also leverage classifications of the preceeding and subsequent characters as well. With these types of highly contextualized problems, pattern recognition effectively becomes sequence recognition. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; These sequences can be of a time series nature (e.g. stills from a video feed), but need not be. Examples include sequences of letters, words, or even items within a shopping cart. Recurrent neural networks (RNNs) handle such sequences through the use of dedicated hidden layers. RNNs can be configured in a variety of ways, ranging from many inputs to one output for a task such as sentiment analysis to a one-to-many network for image captioning. Let us designate a specific hidden layer of nodes within the network as *h* subscripted by *t* for time step (although again, the elements within the sequence need not be a time series). A RNN then derives an array of weights *f* to be applied to the various interations between the values of the hidden layer corresponding to the previous time step and the inputs corresponding to the current time step. Then, depending on the number of desired outputs, the values from the hidden layer corresponding to the current time step are then passed on to the next hidden layer, to the output layer where they are weighted in turn, or both.  
<br>

<p align="center"><b>Figure 1: Derivation of the RNN Weights</b></p>
<div align="center">
<img src="https://github.com/b-knight/Notes-on-Deep-Learning/raw/master/Images/RNN_Formulas.png" alt="The formulas used for creating the arrays of weights used by the recurrent neural network." width="506" height="118">
</div>
<br>


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; For an example, imagine that we want to create a model that takes a word as an input and predicts whether the word is associated with positive feelings, i.e. sentiment analysis. Setting aside issues of capitalization and grammar, we can create a network with twenty-six inputs (the letters of the alphabet) and one output (a 'yes'/'no' positive sentiment boolean). If we wanted a network that could accommodate words three letters in length, then we would need three hidden layers - one layer for every element in the sequence. Figure 2 depicts what such a network would look like after being abridged to only suport three inputs.
<br>

<br>
<p align="center"><b>Figure 2: A Many-to-One RNN with Sequences Three Elements in Length</b></p>
<div align="center">
<img src="https://github.com/b-knight/Notes-on-Deep-Learning/raw/master/Images/RNN.gif" alt="Throughput of a recurrent neural net." width="740" height="385">
</div>
<br>


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Because we are modeling the interdependencies of the inputs not just relative to one another but also relative to their place within the sequence, a RNN will inevitably be more complex relative to a standard network. The three dimensions of inputs are:

**1. Number of Features:** <br> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The number of possible values that an element within the sequence can assume.<br>
**2. Sequence Length:** <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The number of timesteps the network must accomodate - corresponds to the number of <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; hidden layers.<br> 
**3. Batch Size:** <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; How many observations to be propagated through the network at a given time. A full batch <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; tends to yield the most accurate estimate of the gradient whereas mini-batches tend to be <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; less accurate but also less expensive. 
<br>

<br>
<p align="center"><b>Figure 3: Required Inputs and Data Volume of a Standard Neural Network Versus a RNN</b></p>
<div align="center">
<img src="https://github.com/b-knight/Notes-on-Deep-Learning/raw/master/Images/Vector_Length.jpg" alt="The data volume and computational cost or a recurrent neural network far exceeds that of a conventional neural network." width="640" height="356">
</div>

<br>
## The Vanishing Gradient Problem 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Another disadvantage of RNNs is that they are typically unable to discern patterns between elements far apart (10 timesteps or more) from one another within a sequence. This is due the [vanishing gradient problem](https://en.wikipedia.org/wiki/Vanishing_gradient_problem) a problem that afflicts any many-layered network, not just RNNs. First identified by Sepp Hochreiter (Hochreiter, 1991), the vanishing gradient problem occurs over the process of [backpropagation](https://en.wikipedia.org/wiki/Backpropagation).<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Neural networks typicaly utilize hyperbolic tangent functions which have gradients in the range (−1, 1). During backpropagation, the chain rule is invoked with the effect of multiplying these less-than-one values *n* times. The end result is the exponential decay of the gradient (error signal) as backpropagation proceeds from the output layers to the front layers. In practical terms, the front layers of a many-layered network will tend to train very slowly to the point of impracticality.

## Long Short Term Memory (LSTM) Networks

<p align="center"><b>Figure 4: Walk-Through of a LSTM Cell </b></p>
<div align="center">
<img src="https://github.com/b-knight/Notes-on-Deep-Learning/raw/master/Images/LSTM.gif" alt="Walk-Through of a LSTM Cell">
</div>


## References

- Bezerra, Byron Leite Dantas, Cleber Zanchettin, and Vinícius Braga de Andrade. (2012). A Hybrid RNN Model for Cursive Offline Handwriting Recognition. Paper presented at 2012 Brazilian Symposium on Neural Networks (SBRN). Institute of Electrical and Electronics Engineers (IEEE). doi: 10.1109/SBRN.2012.41.

- Hochreiter, S. Untersuchungen zu dynamischen neuronalen Netzen. Diploma thesis, Institut f. Informatik, Technische Univ. Munich, 1991. Advisor: J. Schmidhuber.

- Karpathy, Andrej. [MachineLearner]. (2016, June 14th). *CS231n Lecture 10 - Recurrent Neural Networks, Image Captioning, LSTM*. Retrieved from [https://www.youtube.com/watch?v=iX5V1WpxxkY](https://www.youtube.com/watch?v=iX5V1WpxxkY).

- Olah, Chris. (2015, August 27th). *Understanding LSTM Networks*. Retrieved from [http://colah.github.io/posts/2015-08-Understanding-LSTMs/](http://colah.github.io/posts/2015-08-Understanding-LSTMs/).

- Patterson, Josh, and Adam Gibson. (2016). Deep Learning. Retrieved from [https://www.safaribooksonline.com/library/view/deep-learning/9781491924570/](https://www.safaribooksonline.com/library/view/deep-learning/9781491924570/).
