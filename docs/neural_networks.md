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