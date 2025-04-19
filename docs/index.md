[ml_rust]: https://github.com/mpohl100/ml_rust

## Introduction

This project was started in November 2024 with the goal to get to know machine learning with a hands-on approach.
Now it has grown and yielded some results that I'd like to share with you.
I think I ended up with an innovative approach to enable configuring machine learning for two reasons:
1) The architecture of the neural network is configured by a yaml file
2) It is possible to run genetic algorithms on the architecture of the neural network effectively enabling the improving of it while one is sleeping which I think is really cool.

In my machine learning project implemented in Rust [ml_rust] I achieved a code base about machine learning in Rust which currently enables in-memory dense layers with the activation functions ReLU, Sigmoid, Tanh and Softmax.
The code design enables an easy extension to an exhaustive list of layer types and activation functions.
The next step is to implement being able to pass a memory barrier to limit how much RAM the program can use at max which shall prevent crashes because of configuring too large neural network architectures. Of course the place on disk must be sufficient to store the neural network.
That is why this machine learning approach is targeted for students/ scientists. On a laptop one has a lot more disk space than memory. That way you can train much bigger models.
After that the plan is to bring dense layers to the GPU so that you can leverage graphics cards.
When that is finished I plan on increasing the list of layer types and activation functions because then I have settled on the architecture of the rust traits of layers and activation functions.

## Neural Networks

Check out the explanation what [Neural Networks](neural_networks.md) are.

## Genetic algorithms to generate neural networks

[Genetic algorithms](genetic_algorithms.md)