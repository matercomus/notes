# CPPNs: Compositional Pattern Producing Networks

Compositional Pattern Producing Networks (CPPNs) are a method of evolving artificial neural networks with a genetic algorithm. They evolve not only the weights and topology of the network, but also the activation functions.

- CPPNs are evolved with CPPN-NEAT, which is similar to [[NEAT]], but the activation functions are also evolved. Examples of activation functions include Gaussian, sigmoid, and periodic functions.
- The network is a function of the problem given its geometry. It's a developmental encoding: a neural network that generates “artefacts”.
- The composition of the activation functions create patterns with regularities. This can endow objects with regularities such as symmetry and result in a smaller search space.

To query the network means to provide inputs about the geometry (or context) of the problem to the network, obtaining outputs. The space where queries are applied is called substrate.

![[CPPNN_query_imge.png]]

## Examples #TODO 
CPPNs can be used to create 2D drawings, paintings, shapes, and even compose music.

*Image placeholders here for future reference*
