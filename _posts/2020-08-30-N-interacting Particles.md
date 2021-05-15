---
title: 'N-interacting Particles'
date: 2020-08-30
permalink: /posts/2020/08/interacting-particles/
tags:
  - Physics
  - Modelling
---

Summary: Motivates the n-interaction setup and how to model the problem.

## Table of contents

1. TOC
{:toc}

## Basic problem setup

Consider $N$ indistinguishable point particles, and denote by $x_i \in \mathbb{R}^n$ and $v_i ∈ \mathbb{R}^n$ the position and momentum of particle number $i$.

In the Newton world, the positions $x_i$, sometimes written as  $q_i$ to indicate generalise coordinate systems and momenta $p_i$ satisfy 

$$
\begin{align}{
    \frac{d x_i}{dt} = v(p_i) \\ 
    \frac{d p_i}{dt} = \lambda \sum_{j\neq i}F(x_i, x_j)
}\end{align}
$$
> Note: Time is usually another parameter for the 2 odes above but I removed it for beravity and for our case it is sufficient to think in a time-indenpendent way first. 


along with some inital conditions $x_i(t=0) = u_i, p(t=0) = m_i$, it describe everything there is to know about a system. This means that given sufficiently enough accurate measurments of the inital conditions and knowledge about these equations a highly intelligently being could predict the future and see into the past like how we see the present. While this is impractical in reality due to quantum uncertainities, this ideas leads us to the concept of state. A state is a set of numbers that describe the system in this case $(x_i, p_i)$ repersent the state. If we know the state along with the equations above we can predict the future, at least in Netwon's world. This was first noticed by Laplace in the 17 hundreds. 

##  The Typical Setup Of Non-Interaction


Typically these set of equations are simplified such that there isn't any $E(X_i, X_j)$ and instead the function $E(X_i, X_j)$ only depends on its current position and not the position of other particles i.e. $E(X_i, X_j) = E(X_i)$. This is often just called the potential function. Even this smiplified case we can derive useful models such as the ideal-gas law which is a sufficient approximation for most enginnering applications as long as we are not dealing with low temperatures or extreme pressures. 

##  The Atypical Setup Of Interaction

The function $E(Xi, X_j)$ is called the interaction kenerl. A simple interaction kernel is the Poisson kernel, $F=C\frac{x}{x^n}$. This corresponds to particles under gravitational interaction for $C < 0$ or electrostatic interactions (ions in a plasma) for $C > 0$.

Another common interaction kernel is the the polynomial kernel where $F = A{\mid x \mid}^a − B{\mid x\mid}^b$  with $a, b \in \mathbb{R}$ (possibly negative). The potential has an attractive part $− B{\mid x\mid}^b$ and a repulsive one $A{\mid x \mid}^a$. This kernel is a common choice for many life science applications, in particular swarming and flocking. Since interaction should be repulsive at short range because individuals try to avoid collisions but it is attractive at long range in order to keep the flock together. The kernel is also used in molecular physics when modelling the interaction between atoms forming a covalent bond the famous example being the lennard jones potential.

![](https://i.imgur.com/9PsxQzb.png)

There are 2 interesting extensions here 

- Mean field scaling
- Learnt Interaction Kernel

## Mean Field Scaling

The mean field scaling consists in assuming that $λ ∼ 1/N$, that is in considering
$$
\begin{align}{
    \frac{d x_i}{dt} = v(p_i) \\ 
    \frac{d p_i}{dt} = \frac{1}{N} \sum_{j\neq i}F(x_i, x_j)
}\end{align}
$$

At least in the case of classical mechanics with $v(p_i) = p_i$, it is possible to rescale in position and time and therefore in velocity or momentum. By choosing the scalings appropriately, it thus seems to be possible to reduce our original starting equations to the equations above. 

However the rescaling changes the initial conditions in (1.2). Therefore the rescaling in position and time should instead be chosen so that the initial positions and velocities are of order 1. This simplifies our calculuation for such system. 

## Interaction Kernel

The second possible extensions is can we learn the interaction kernel $F(x_i, x_j)$ ? Maybe ? This is something I am still exploring there are some recent papers on the topic of learning pairwise kernels and how to model them that I am still reading on so I will talk more about it in a future blog post. 

## References 

1. [A review of the mean field limits for Vlasov
equations by Pierre-Emmanuel Jabin](https://home.cscamm.umd.edu/~jabin/review_MF.pdf)
