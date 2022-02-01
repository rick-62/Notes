---
id: Oe7rC5HnKMMNAf9jwy1wz
title: Conda
desc: ''
updated: 1643577134225
created: 1642253136381
---

## Environments

```bash
# create new Conda environment
conda create --name <name>

# activate environment (Windows)
conda activate <name>

# activate environment (bash)
source activate <name>

# deactivate current environment (Windows)
conda deactivate

# deactivate current environment (bash)
source conda deactivate

# list all current environments
conda env list

# remove environment
conda env remove --name <name>

# export current environment (including env name) to YAML
conda env export > environment.yaml

# create environment from environment.yaml
conda env create -f environment.yaml
```

## Installation

```bash
# install a package using conda-forge
conda install -c conda-forge <package-name>
```
