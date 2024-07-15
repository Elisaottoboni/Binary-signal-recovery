# Binary Signal Recovery Using the Metropolis-Hastings Algorithm

## Introduction

This project aims to recover an unknown binary signal using the Metropolis-Hastings algorithm, a stochastic sampling technique. The objective is to estimate a binary parameter vector $\theta$ from noisy observations $y$. The project studies how the mean square error $(\operatorname{MSE})$ varies with the number of measurements $m$.

## Problem Definition

### Signal Model

- $X \in \mathbb{R}^{m \times d}$: Random sensing matrix with i.i.d. entries from $N(0, 1)$.
- $\xi \in \mathbb{R}^{m}$: Noise vector with i.i.d. entries from $N(0, 1)$.
- $\Theta = \{0, 1\}^{d}$: Signal space. $\theta \in \Theta$ is chosen uniformly at random.

The measurement vector $y \in \mathbb{R}^{m}$ is generated as $$y = X\theta + \xi.$$

## Maximum Likelihood Estimate (MLE)

The maximum likelihood estimate of $\theta$ is given by the value $\hat{\theta} \in \Theta$ that minimizes the function

$$
\mathcal{H}(X, y; \theta) = (y - X\theta)^T(y - X\theta)
$$

## Metropolis-Hastings Algorithm

The Metropolis-Hastings algorithm is a Monte Carlo Markov Chain (MCMC) technique used to generate samples from complex probability distributions. It explores the space of solutions by proposing new positions and accepting them with a certain probability, making it possible to approximate the distribution of interest even when it is not possible to sample it directly.

We construct the Metropolis-Hastings (discrete-time) Markov chain on the state space $\theta$, with stationary distribution

$$\pi_{\beta}(\theta) = \frac{e^{-\beta \mathcal{H}(X,y; \theta)}}{Z_\beta}, \quad \text{with} \quad Z_\beta = \sum_{\theta \in \Theta}e^{-\beta \mathcal{H}(X,y; \theta)}$$

The algorithm involves:
1. Initializing with a random $\theta$.
2. Proposing a new $\theta^{*}$ by flipping a random bit.
3. Accepting $\theta^{*}$ with a probability depending on $\mathcal{H}(X, y; \theta)$.

## Results

The project evaluates the $\operatorname{MSE}$ for different numbers of measurements $m$ and identifies the minimum $m/d$ for reliable recovery of $\theta$.