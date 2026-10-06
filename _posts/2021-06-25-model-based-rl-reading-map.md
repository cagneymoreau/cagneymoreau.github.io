---
layout: post
title: "A Reading Map of Model-Based Reinforcement Learning"
date: 2021-06-25
---

*Originally written in 2021 on my old blog. Revised, with a short note at the end on what's happened since.*

This post organizes the ideas and the rough map of model-based reinforcement learning, as I was reading into it for my robot. Once you see how much data and tuning current machine learning needs, it becomes clear why this matters.

## The problem

Many deployed ML systems are **fragile** and **data-hungry**. Acting randomly and backpropagating through carefully balanced datasets is, I think, an intermediate step. The next step is for a system to **model the physics** of its world and predict which actions lead to success.

The goal is **sample efficiency**: getting things right with as little trial and error as possible. To me that means not just less data but fewer annotations, less tuning, and fewer hand-built reward functions. A deployed system should predict what will happen, how confident it is in that prediction, and what information it's missing.

## The reading list (as of 2021)

- **Dyna (1993):** an early framework that mixes learning from real experience with planning on a learned model. [Paper](https://www.researchgate.net/publication/2342119_Efficient_Learning_and_Planning_Within_the_Dyna_Framework)
- **PILCO (2011):** low-data, model-based policy search using probability distributions for one-step predictions. [Paper](https://www.researchgate.net/publication/221345233_PILCO_A_Model-Based_and_Data-Efficient_Approach_to_Policy_Search)
- **Learning Neural Network Policies with Guided Policy Search (2013):** builds on PILCO for tasks with few samples. [Paper](https://people.eecs.berkeley.edu/~svlevine/papers/mfcgps.pdf)
- **Deep PILCO (2016):** PILCO with neural networks. [Paper](http://mlg.eng.cam.ac.uk/yarin/PDFs/DeepPILCO.pdf)
- **Imagination-Augmented Agents (I2A, 2017):** the start of model-based RL in higher dimensions. [Paper](https://arxiv.org/pdf/1707.06203v1.pdf)
- **Deep RL in a Handful of Trials (2018).** [Paper](https://arxiv.org/abs/1805.12114)
- **ME-TRPO (2018):** TRPO with an ensemble of learned dynamics models, borrowing the ensemble idea from other fields to build the physics model. [Paper](https://arxiv.org/abs/1802.10592)
- **MB-MPO (2018):** model-based meta-policy optimization, using model ensembles with a focus on final performance. [Paper](https://arxiv.org/pdf/1809.05214.pdf)
- **Dynamic Planning Networks (2019).** [Paper](https://arxiv.org/pdf/1812.11240.pdf)
- **Learning Accurate Long-term Dynamics (2020):** moves away from chaining one-step predictions toward predicting further ahead. [Paper](https://arxiv.org/pdf/2012.09156.pdf)
- **Dreamer (2020):** compresses high-dimensional observations into a small latent space and learns behavior by imagining inside it. [Project page](https://danijar.com/project/dreamer/), [earlier work (PlaNet)](https://arxiv.org/pdf/1811.04551.pdf)

Good places to keep up: Berkeley's [CS287 lectures](https://people.eecs.berkeley.edu/~pabbeel/cs287-fa19/), the [BAIR blog](https://bair.berkeley.edu/blog/), and [Danijar Hafner's site](https://danijar.com/).

## Since then

Right after this language models took off. I did not expect that to happen. Maybe I should have been more aware? I remember seeing cool language model examples but I never made the connection that this could be a tool that would radically speed up my work flow. Now it seems people are leaning back into the model based world. Either way, I'm out of practice on these details but it would be interesting to dive back in.
