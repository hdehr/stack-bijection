# Learning a Bijection with a Variational Autoencoder

Let us define a **stack** as a subset $S$ of a two-dimensional non-negative integer lattice such that
1. if $(0, j)$ is in $S$ with $j > 0$ then $(0, j-1)$ is also in $S$ and
2. if $(i, j)$ is in $S$ with $i,j > 0$ then either $(i-1, j)$ or $(i-1, j-1)$ is in $S$.

The central fact we are concerned with is that there are exactly $3^{n-1}$ stacks of size $n$.
I became aware of this fact through Peter Kagey who made this related [StackExchange post](https://math.stackexchange.com/questions/3659431/number-of-ways-to-stack-lego-bricks), citing a 1988 paper by [Gouyou-Beauchamps and Viennot](https://doi.org/10.1016/0196-8858(88)90017-6).
This project is an attempt to have a neural network learn an, ideally human-intelligible, bijection between stacks of size $n$ and ternary sequences of length $n-1$.

We do not fully succeed, but the strategy we employ is to build a variational autoencoder that attempts to reconstruct a representation of a stack after passing it through a latent space of continuous approximations to ternary categorical distributions.
Achieving zero error would mean the encoder and decoder halves could be interpreted as inverse bijections.