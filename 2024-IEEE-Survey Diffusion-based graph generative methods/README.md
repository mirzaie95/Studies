# A Survey on Diffusion-Based Graph Generative Methods

## Introduction

Graph generative methods are essential for generating new graphs, which play a crucial role in various applications such as drug discovery, material science, and social network analysis. Among these techniques, diffusion-based generative models have emerged as highly effective due to their robust theoretical foundations. This survey aims to provide a comprehensive overview of diffusion-based graph generative methods, highlighting their key principles, paradigms, applications, and formulas.

## Diffusion Methods: An Overview

Diffusion-based generative methods involve a two-step process: a forward diffusion process and a reverse generative process. The forward process gradually adds noise to the data until it becomes nearly random, while the reverse process reconstructs the data from the noisy version using learned models.

There are three main paradigms in diffusion methods:
1. **Denoising Diffusion Probabilistic Models (DDPMs)**
2. **Score-Based Generative Models (SGMs)**
3. **Stochastic Differential Equations (SDEs)**

Each paradigm uses a distinct approach to model and generate data through the diffusion process.

## Graph Learning Problem Formulation

Graphs are defined by vertices (nodes) and edges (connections). The goal is to learn a probabilistic distribution over graphs to sample new, realistic graphs. This involves learning the underlying distribution through the diffusion process and generating graphs through the reverse process.

## Denoising Diffusion Probabilistic Models (DDPMs)

DDPMs operate with two Markov chains: the forward chain, which corrupts the data by adding noise, and the reverse chain, which denoises the data. The processes are defined as follows:

**Forward Process:**

$$ q(x_t | x_{t-1}) = \mathcal{N}(x_t; \sqrt{1 - \beta_t} x_{t-1}, \beta_t \mathbf{I}) $$

**Reverse Process:**

$$ p_\theta(x_{t-1} | x_t) = \mathcal{N}(x_{t-1}; \mu_\theta(x_t, t), \sigma_t^2 \mathbf{I}) $$

The forward process iteratively adds noise with variance $\beta_t$ to the data, and the reverse process reconstructs the data by learning the mean $\mu_\theta$ and variance $\sigma_t^2$.

## Score-Based Generative Models (SGMs)

SGMs rely on score matching to estimate the gradient (score) of the data distribution. The key idea is to model the score function of the data distribution and use it to generate new samples. The training objective is to minimize the following loss:

$$ \mathbb{E}[\lambda(t) || \epsilon + \sigma_t s_\theta(x_t, t) ||^2] + \text{const} $$

Here, $\lambda(t)$ is a weighting function, $\epsilon$ is noise, and $s_\theta(x_t, t)$ is the score function parameterized by $\theta$. SGMs can handle both continuous and discrete data, making them versatile for various graph generation tasks.

## Stochastic Differential Equations (SDEs)

SDEs provide a mathematical framework to model the diffusion process. The data evolution is described by an SDE:

$$ dx = f(x, t)dt + g(t)dw $$

where $f(x, t)$ is the drift coefficient, $g(t)$ is the diffusion coefficient, and $dw$ is a Wiener process. The reverse process involves solving the SDE backward in time to generate data from noise.

## Applications in Molecule Generation

Diffusion-based graph generative methods have been particularly successful in molecule generation, with three main applications:

1. **De Novo Molecule Design:** Generating novel molecules with desired properties, tackling the discrete nature of molecular graphs using methods like VAEs, GANs, and 3D molecule geometries.
   
2. **Conformation Design:** Generating 3D structures of molecules, crucial for understanding their function and interaction with other molecules, using techniques like Noise Conditional Score Networks and Langevin Dynamics (e.g., ConfGF).

3. **Ligand Design and Docking:** Designing molecules that can bind to specific protein targets, essential for drug discovery, incorporating out-of-distribution information to ensure the generated molecules are effective (e.g., DIFFDOCK).

## Evaluation Metrics

Evaluating the performance of graph generative models involves several metrics:
- **Validity:** The generated graphs should represent valid structures.
- **Uniqueness:** The generated graphs should be distinct from each other.
- **Novelty:** The generated graphs should differ from those in the training set.

Specific datasets and benchmarks are used to assess these metrics, ensuring that the models produce high-quality results.

## Challenges and Future Directions

Despite the progress, there are several challenges in diffusion-based graph generative methods:
- **Discrete Nature of Graphs:** Handling the combinatorial nature of graphs remains difficult.
- **Training Complexity:** Training these models requires significant computational resources and time.

Future directions include developing more efficient algorithms, expanding applications to other domains, and integrating 3D structures into the generative process.

## Conclusion

Diffusion-based graph generative methods represent a promising field with significant potential for various applications. This survey provides a detailed overview of the key paradigms, methods, and applications, highlighting the strengths and challenges of these approaches. With ongoing research and development, diffusion-based methods are poised to make substantial contributions to graph generation and its numerous applications.
