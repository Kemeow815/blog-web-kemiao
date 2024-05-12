---
title: AlphaFold3
date: 2024-05-12T12:18:17+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1714687980739-4382cd22bd65?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTU0ODczOTl8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1714687980739-4382cd22bd65?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTU0ODczOTl8&ixlib=rb-4.0.3
---

# [kyegomez/AlphaFold3](https://github.com/kyegomez/AlphaFold3)

[![Multi-Modality](agorabanner.png)](https://discord.gg/qUtxnK2NMf)

# AlphaFold3
Implementation of Alpha Fold 3 from the paper: "Accurate structure prediction of biomolecular interactions with AlphaFold3" in PyTorch


## install
`$ pip install alphafold3`

## Input Tensor Size Example

```python
import torch

# Define the batch size, number of nodes, and number of features
batch_size = 1
num_nodes = 5
num_features = 64

# Generate random pair representations using torch.randn
# Shape: (batch_size, num_nodes, num_nodes, num_features)
pair_representations = torch.randn(
    batch_size, num_nodes, num_nodes, num_features
)

# Generate random single representations using torch.randn
# Shape: (batch_size, num_nodes, num_features)
single_representations = torch.randn(
    batch_size, num_nodes, num_features
)
```

## Genetic Diffusion
Need review but basically it operates on atomic coordinates.

```python
import torch
from alphafold3.diffusion import GeneticDiffusion

# Create an instance of the GeneticDiffusionModuleBlock
model = GeneticDiffusion(channels=3, training=True)

# Generate random input coordinates
input_coords = torch.randn(10, 100, 100, 3)

# Generate random ground truth coordinates
ground_truth = torch.randn(10, 100, 100, 3)

# Pass the input coordinates and ground truth coordinates through the model
output_coords, loss = model(input_coords, ground_truth)

# Print the output coordinates
print(output_coords)

# Print the loss value
print(loss)
```

## Full Model Example Forward pass

```python
import torch 
from alphafold3 import AlphaFold3

# Create random tensors
x = torch.randn(1, 5, 5, 64)  # Shape: (batch_size, seq_len, seq_len, dim)
y = torch.randn(1, 5, 64)  # Shape: (batch_size, seq_len, dim)

# Initialize AlphaFold3 model
model = AlphaFold3(
    dim=64,
    seq_len=5,
    heads=8,
    dim_head=64,
    attn_dropout=0.0,
    ff_dropout=0.0,
    global_column_attn=False,
    pair_former_depth=48,
    num_diffusion_steps=1000,
    diffusion_depth=30,
)

# Forward pass through the model
output = model(x, y)

# Print the shape of the output tensor
print(output.shape)
```


# Citation
```bibtex
@article{Abramson2024-fj,
  title    = "Accurate structure prediction of biomolecular interactions with
              {AlphaFold} 3",
  author   = "Abramson, Josh and Adler, Jonas and Dunger, Jack and Evans,
              Richard and Green, Tim and Pritzel, Alexander and Ronneberger,
              Olaf and Willmore, Lindsay and Ballard, Andrew J and Bambrick,
              Joshua and Bodenstein, Sebastian W and Evans, David A and Hung,
              Chia-Chun and O'Neill, Michael and Reiman, David and
              Tunyasuvunakool, Kathryn and Wu, Zachary and {\v Z}emgulyt{\.e},
              Akvil{\.e} and Arvaniti, Eirini and Beattie, Charles and
              Bertolli, Ottavia and Bridgland, Alex and Cherepanov, Alexey and
              Congreve, Miles and Cowen-Rivers, Alexander I and Cowie, Andrew
              and Figurnov, Michael and Fuchs, Fabian B and Gladman, Hannah and
              Jain, Rishub and Khan, Yousuf A and Low, Caroline M R and Perlin,
              Kuba and Potapenko, Anna and Savy, Pascal and Singh, Sukhdeep and
              Stecula, Adrian and Thillaisundaram, Ashok and Tong, Catherine
              and Yakneen, Sergei and Zhong, Ellen D and Zielinski, Michal and
              {\v Z}{\'\i}dek, Augustin and Bapst, Victor and Kohli, Pushmeet
              and Jaderberg, Max and Hassabis, Demis and Jumper, John M",
  journal  = "Nature",
  month    =  may,
  year     =  2024
}
```



# Notes
-> pairwise representation -> explicit atomic positions
-> within the trunk, msa processing is de emphasized with a simpler MSA block, 4 blocks
-> msa processing -> pair weighted averaging 
-> pairformer: replaces evoformer, operates on pair representation and single representation
-> pairformer 48 blocks
-> pair and single representation together with the input representation are passed to the diffusion module
-> diffusion takes in 3 tensors [pair, single representation, with new pairformer representation]
-> diffusion module operates directory on raw atom coordinates
-> standard diffusion approach, model is trained to receiev noised atomic coordinates then predict the true coordinates
-> the network learns protein structure at a variety of length scales where the denoising task at small noise emphasizes large scale structure of the system.
-> at inference time, random noise is sampled and then recurrently denoised to produce a final structure
-> diffusion module produces a distribution of answers
-> for each answer the local structure will be sharply defined
-> diffusion models are prone to hallucination where the model may hallucinate plausible looking structures
-> to counteract hallucination, they use a novel cross distillation method where they enrich the training data with alphafold multimer v2.3 predicted strutctures. 
-> confidence measures predicts the atom level and pairwise errors in final structures, this is done by regressing the error in the outut of the structure mdule in training,
-> Utilizes diffusion rollout procedure for the full structure generation during training ( using a largeer step suze than normal)
-> diffused predicted structure is used to permute the ground truth and ligands to compute metrics to train the confidence head.
-> confidence head uses the pairwise representation to predict the lddt (pddt) and a predicted aligned error matrix as used in alphafold 2 as well as distance error matrix which is the error in the distance matrix of the predicted structure as compared to the true structure
-> confidence measures also preduct atom level and pairwise errors
-> early stopping using a weighted average of all above metic
-> af3 can predict srtructures from input polymer sequences, rediue modifications, ligand smiles
-> uses structures below 1000 residues
-> alphafold3 is able to predict protein nuclear structures with thousnads of residues
-> Covalent modifications (bonded ligands, glycosylation, and modified protein residues and
202 nucleic acid bases) are also accurately predicted by AF
-> distills alphafold2 preductions
-> key problem in protein structure prediction is they predict static structures and not the dynamical behavior
-> multiple random seeds for either the diffusion head or network does not product an approximation of the solution ensenble
-> in future: generate large number of predictions and rank them
-> inference: top confidence sample from 5 seed runs and 5 diffusion samples per model seed for a total of 25 samples
-> interface accuracy via interface lddt which is calculated from distances netween atoms across different chains in the interface
-> uses a lddt to polymer metric which considers differences from each atom of a entity to any c or c1 polymer atom within  aradius


# Todo

- [ ] Implement Figure A, implement triangle update, transition, 
- [ ] Impelment Figure B, per token, cond, 
- [ ] Implement Figure C: Network Chunk,
- [ ] Implement confidence module
- [ ] Implement Template Module
