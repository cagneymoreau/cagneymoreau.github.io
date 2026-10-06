---
layout: post
title: "Learning Machine Learning the Hard Way, With DL4J"
date: 2020-09-14
---

*Based on a short 2020 post on my old blog. Expanded.*

For a while I worked with DL4J (Deeplearning4j) like crazy. I wrote my robot software in Java, and DL4J was the serious deep learning library in the Java world, so that's where I learned machine learning.

## The roadmap

I ended up with a pile of small projects that built on each other, each one teaching a single concept before moving to the next. Since they were sequential, I put them on GitHub as a learning path in case anyone else was searching for DL4J examples: [github.com/cagneymoreau/DL4j_RoadMap](https://github.com/cagneymoreau/DL4j_RoadMap).

They're far from polished, and I'd call that honest. Very often I'd build a feature one way, then learn a better way a few projects later. The repo shows that progression instead of pretending I got it right the first time.

## What learning it this way taught me

- **Working outside the mainstream forces you to understand things.** With fewer tutorials and answers to copy, I had to understand what each layer and setting actually did.
- **Small sequential projects beat one big one.** Each project isolated one idea, so when something broke I knew where to look.
- **Keep the rough versions.** Notes and messy early code are often easier to learn from than a polished final method.

Around the same time I was also experimenting with reinforcement learning, which led to a reading map of model-based RL, and with the [OpenAI Gym HTTP API](https://github.com/cagneymoreau/gym-http-api) so Java code could talk to Python environments.
