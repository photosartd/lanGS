# Week 1: setup
- Read the code from main repositories
- Re-read [LangSplat paper](https://arxiv.org/pdf/2312.16084) in details
- Installed the libraries
- Started trying to train the LangSplat model
1. [Gaussian Splatting Lightning](https://github.com/yzslab/gaussian-splatting-lightning)
   1. Setup Note: do not install via `environment.yml`; firstly install cuda-toolkit/dev of the needed
   version, then proceed according instructions.
   2. Idea: may not fully rewrite the training process of a LangSplat, but only rendering part (will probably be easier).
   In Any case will have to work on dependencies since LangSplat contains modified CUDA rasterization code.
2. [LangSplat](https://langsplat.github.io)
   1. Setup Note: same as for Gaussian Splatting Lightning.
   2. Idea/question: how to efficiently handle queries to Gaussians?
