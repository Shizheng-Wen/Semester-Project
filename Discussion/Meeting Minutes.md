# Meeting summary

## May 16, 2023 

Location: ETH AI Center; People: Ben, Mike and me



**Two phased goals:**

1. we aim to learn a autoregressive graph-based PDE solver by only using physical-informed loss. The physical-informed loss will be expressed as the residual of the variational formulation (weak form) for the PDE.
2. Explore a adaptive mesh technique during the autoregressive marching for our model, which may accelerate the training and inference time.



For the **first phase**, We have following potential task

- No sure about the PINN, whether the weak form solution is better than the strong form.

- For weak form, increasing the order of the lagrange basis to see whether the expressivity and the computational efficiency are both improved.

- Change the number of timesteps (interesting hyperparameters) in the autoregressive model. 

- discretized PINN loss. use the finite difference to calculate the derivatives. Compare the GNN and CNN to see which one is better.

- Also, we should consider the generalization:

  - Considering to train on different initial condition and input. Generalize our method. Not just solve a equation solely. 

  - verify our training data(unlabeled) to generalize the solver with different parameters. what parameters that you want to generalize.

  - Training on [0, T] and show the autoregressive model still have a good performance between [T, 2T]

We should more rigorously tested these potential tasks.



Hopefully, we can show that our GNN will be much more slower but high resolution. But if we use the remeshing, we can have speed up, even faster than CNN. Therefore, we want to develop some adaptive mesh algorithm. This is our second phase:

- Learnable adjacency matrix
- pruning trick
- Train a fixed remeshing algorithm based on some data solely.
  - Also we can consider to make the combination of CNN and GNN. Training the solution operator on the CNN. but we have a learnable mapping from discretized points to CNN?? 
  - Refer the paper of GEO-FNO, meshgraphent and PhyGeoNet