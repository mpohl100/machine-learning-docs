## Neural Networks
### Why are neural networks useful
One has an input vector v of dimension 100. 
1) In a classification problem one wants to find out to which of three classes the vector v belongs. In this case one wants to transform the vector v to a vector of targets t of dimension three where the sum of the entries is one. The individual entries denote the likelyhood that vector v belongs to the category of the position of the entry in vector t.
2) One can also imagine that one has 100 entries of data and wants to artificially generate another 50 values that are similar to the data in vector v. In this case the target vector t has 50 entries.

### How does one change the dimensions of vector v?

For this one can use a so called dense layer. A dense layer consist of a matrix of weights W and a vector of biases b. Also some kind of activation function a is used.
1) In scenario one of above the matrix W of weights has the dimensions 100 x 3. Calculation v' = W * v converts the dimensions of vector v from 100 to 3. After that the biases of dimesnion 3 are applied by calculating the sum v'' = v' + b. This is known as the forward pass through the dense layer. Finally the activation function a is applied to all entries of vector v'': v''' = a(v''). The calculations for the dense layer are finished.
2) In scenario two the same calculations are applied except this time the matrix of weights W has the dimensions 100 x 50 and the biases have the dimension 50. Therefore the dimensions of vector v''' are 50.

### How a neural network is formed.

A neural network consists of a concatenation of dense layers in our example which transforms the dimensions and the values of the entries for example like this:
1) dense layer 1: 100 -> 50; dense layer 2: 50 -> 25; dense layer 3: 25 -> 12; dense layer 4: 12 -> 6; dense layer 5: 6 -> 3
2) one can also make the neural network bigger in the beginning: dense layer 1: 100 -> 200; dense layer 2: 200 -> 200; dense layer 3: 200 -> 100; dense layer 4: 100 -> 50;
FInding out the optimal architecture of the neural network is part of the job of the engineer.

### How the weights and biases are calculated
For this the technique known as linear regression is used. Basically one can compare the calculated output of a dense layer v''' and compare it to the target output t. One can caluclate the difference by calculating d = v''' - t. 
1) The derivative of the activation function is applied to get the vector vb''
2) One can calculate a matrix of gradients by calculating G = vb'' transposed * v'.
3) Now one can calculate the matrix of weights of the next epoch W next = W previous + learning_rate * G. The learning rate is a constant floating point number which defines the speed of regression.

### How training is organized
Above the calculation and the training of one dense layer is described.
The training of a neural network now takes for example 100 epochs and over time the difference between the actual outputs and the target outputs is minimized. The loss of each epoch is a measure of how much the weights and biases of the neural network have changed. Over time the loss should become smaller.

## Other Types of Neural Networks
The basic idea of introducing new types of Neural Networks is to make them turing complete.

### Retry Neural Network

#### What it is
A retry neural network receives an internal dimension in the layers 1..N with N the total number of layers.
If after evaluating the primary network the internal dimension is close to zero the secondary neural network which is the same architecture as the primary neural network minus the internal dimensions is invoked and the evaluation of the secondary is returned as the result.
Now it is possible that the secondary network is again a retry network and therefore the touring condition that one can loop is fullfilled. Obviously it is tough to loop forever as one would run out of diskspace to save the neural networks. Looping forever is anyways not a practical application of a neural network as one wants to compute a result in an acceptable amount of time.
However the gist of retry neural networks is that they are basically able to dismiss their first result and can invoke a secondary network where its confidence to be right is higher.
Of course the secondary network can again be a retry network and therefore you can add an arbitrary number pf levels.

#### How to train a retry network
First one trains the primary neural network. Then all the training samples are tested with this neural network.
The correct predictions receive a one as last internal dimension which stands for "do not continue". The wrong predictions receive a zero which stands for "continue". After that the primary network is reshaped to contain the internal dimensions. Now everything needs to be retrained. The theory is that the 0..N-1 dimensions end up being the same as before and the network learns with the internal dimension whether to continue or not.
Then only the wrongly predicted samples are passed as training parameters to the secondary neural network.
That means with each level of retry you add the training samples become less in numbers.
The theory is that the toughest to classify samples get rejected by all levels and reach the last level of retries.
The hope is to improve the accuracy of a neural network architecture in general. With just one level it should be worse than with some retry levels.