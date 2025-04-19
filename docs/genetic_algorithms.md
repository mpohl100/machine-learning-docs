## Genetic algorithms and neural networks

Genetic algorithms are an adaptation of the algorithm of life. A generation of phenotypes faces a certain challenge and the winners of the competition get to spread their genes to the next generation of phenotypes. With this optimization algorithm one tries to find the best phenotype for the challenge.
In our case the challenge is to find the best prediction percentage of a neural network architecture for a given list of samples and targets. That means that the phenotype is the architecture of a neural network and the challenge is to evaluate all samples with this architecture and to find out what percentage of predictions is correct. The more accurate the predictions of a neural network architecture are the more it shapes the next generation of neural network architectures.

## How the neural network architecture can be altered

### Crossover

The crossover operation can be implemented by taking the left half of the one neural network and the right half of another neural network and to put them together via a "glue" dense layer so that the dimensions of all layers match.

### Mutate

#### Adding a layer

Mutating a neural network architecture can be done by adding a layer in a random position. The dimensions of the neighbouring layers must be adapted so that the dimensions match, otherwise the neural network architecture is invalid

#### Changing the activation function of an existing layer

Also, one can change the type of activation function of an existing layer.

#### Removing a layer

It could also be that the neural network architecture has become too big so one also wants to offer to delete a layer and to make the now new neighbours match in dimensions.

### Problems of genetic algorithms

The core problem is that every neural network architecture needs to be trained with all samples for numerous epochs, so the runtime of the algorithm can be pretty bad. Also, randomly selected tries of mutations can be neural network architectures that don't make any sense to try for a human machine learning engineer who can avoid paying the runtime cost.
This indicates that the neural network architectures should generally not be too big otherwise the algorithm could take a long time to finish. The purpose of this project is to find out for what kind of machine learning problems genetic algorithms can be of help.
