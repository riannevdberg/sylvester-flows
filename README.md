# Sylvester normalizing flows for variational inference

Pytorch implementation of Sylvester normalizing flows, based on our paper:

[Sylvester normalizing flows for variational inference](https://arxiv.org/abs/1803.05649) (UAI 2018) <br/>
Rianne van den Berg*, Leonard Hasenclever*, Jakub Tomczak, Max Welling 

*Equal contribution

## Requirements
The latest release of the code is compatible with:

  * `pytorch 1.0.0`

  * `python 3.7`

Thanks to Martin Engelcke for adapting the code	to provide this compatibility.
<br/>

Version v0.3.0_2.7 is compatible with:
  
  * `pytorch 0.3.0` **WARNING**: More recent versions of pytorch have different default flags for the binary cross entropy loss module: nn.BCELoss(). You have to adapt the appropriate flags if you want to port this code to a later vers\
ion.

  * `python 2.7`


## Data
The experiments can be run on the following datasets:
* static MNIST: dataset is in data folder;
* OMNIGLOT: the dataset can be downloaded from [link](https://github.com/yburda/iwae/blob/master/datasets/OMNIGLOT/chardata.mat);
* Caltech 101 Silhouettes: the dataset can be downloaded from [link](https://people.cs.umass.edu/~marlin/data/caltech101_silhouettes_28_split1.mat).
* Frey Faces: the dataset can be downloaded from [link](https://github.com/y0ast/Variational-Autoencoder/blob/master/freyfaces.pkl).

## Usage

Below, example commands are given for running experiments on static MNIST with different types of Sylvester normalizing flows, for 4 flows:

**Orthogonal Sylvester flows** <br/>
This example uses a bottleneck of size 8 (Q has 8 columns containing orthonormal vectors).
```bash
python main_experiment.py -d mnist -nf 4 --flow orthogonal --num_ortho_vecs 8 
```

**Householder Sylvester flows**<br/>
This example uses 8 Householder reflections per orthogonal matrix Q.
```bash
python main_experiment.py -d mnist -nf 4 --flow householder --num_householder 8
```

**Triangular Sylvester flows**<br/>
```bash
python main_experiment.py -d mnist -nf 4 --flow triangular 
```

<br/>
To run an experiment with other types of normalizing flows or just with a factorized Gaussian posterior, see below.<br/>
<br/>
<br/>

**Factorized Gaussian posterior**<br/>
```bash
python main_experiment.py -d mnist --flow no_flow
```

**Planar flows**<br/>
```bash
python main_experiment.py -d mnist -nf 4 --flow planar
```

**Inverse Autoregressive flows**<br/>
This examples uses MADEs with 320 hidden units.
```bash
python main_experiment.py -d mnist -nf 4 --flow iaf --made_h_size 320
```

<br/>
More information about additional argument options can be found by running ```python main_experiment.py -h```


## Cite

Please cite our paper if you use this code in your own work:

```
@inproceedings{vdberg2018sylvester,
  title={Sylvester normalizing flows for variational inference},
  author={van den Berg, Rianne and Hasenclever, Leonard and Tomczak, Jakub and Welling, Max},
  booktitle={proceedings of the Conference on Uncertainty in Artificial Intelligence (UAI)},
  year={2018}
}
```
