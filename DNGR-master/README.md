# DNGR : Deep Neural Networks for Graph Representations


*This is a python implementation of DNGR model using Keras*


The DNGR model uses the following steps to compute node embeddings for a given graph


1. Use Random Surfing Model to construct transition matrix for the nodes

2. Construct PPMI matrices for the transition matrix

3. Feed PPMI to Stacked Denoising Autoencoder to learn non-linear relationships and generate embeddings

**Dataset chosen: 20NewsGroup**

- It can be downloaded [here](https://archive.ics.uci.edu/ml/datasets/Twenty+Newsgroups) or loaded directly using [sklearn](http://scikit-learn.org/stable/datasets/twenty_newsgroups.html)
- There are three groups NG3, NG6 and NG9 that are commonly used in studies for performance comparison. I have made use of the exact same groups. The choice of which group to use for evaluation can be chosen while running the model. The default is NG3.


Install pre-reqs by running: 
`pip3 install -r req.txt`


Run the code by entering: 
`python3 DNGR.py`


A Full list of cmd line arguments are shown by entering: 
```
python3 DNGR.py -h
```

```
usage: DNGR [-h] [--group [{NG3,NG6,NG9}]] [--hops HOPS] [--alpha ALPHA]
            [--hidden_neurons HIDDEN_NEURONS [HIDDEN_NEURONS ...]]

This is a Keras implementaion of DNGR evaluating the 20NewsGroup dataset.

optional arguments:
  -h, --help              show this help message and exit
  
  --group [{NG3,NG6,NG9}] Choose the group to evaluate
  
  --hops HOPS             Maximum number of hops for Transition Matrix in Random
                          surfing

  --alpha ALPHA           Probability of (alpha) that surfing will go to next
                          vertex, probability of (1-alpha) that surfing will
                          return to original vertex and restart. Range 0-1
  
  --hidden_neurons HIDDEN_NEURONS [HIDDEN_NEURONS ...]
                          Eg: '512 256 128' or '256 128 64 32'. Number of hidden
                          neurons in auto-encoder layers. Make sure there are 3
                          or more layers

```

Here is an example of how you would pass arguments from the terminal:
```
python3 DNGR.py --group NG6 --hops 4 --alpha 0.98 --hidden_neurons 512 256 128 
```

*A Jupyter notebook version of the implementation titled DNGR.ipynb has also been included in the repository.*


**References:**

[DNGR: Deep Neural Network for Graphical Representations](https://pdfs.semanticscholar.org/1a37/f07606d60df365d74752857e8ce909f700b3.pdf)

[Learning deep representations for graph clustering](https://www.aaai.org/ocs/index.php/AAAI/AAAI14/paper/view/8527/8571)
