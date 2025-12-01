# Action Recognition — Setup (MMAction2 + Conda/Pip)

This component uses MMAction2 for video action recognition. The environment is Conda-first, with pip where needed. Tested with Python 3.10.17.

## 1) Prerequisites
- Anaconda or Miniconda
- CUDA-capable GPU and drivers (optional, for acceleration)
- Git

## 2) Create and activate Conda env (Python 3.8)
```
conda create --name openmmlab python=3.8 -y
conda activate openmmlab

For more details, visit https://mmaction2.readthedocs.io/en/latest/get_started/installation.html
```

## 3) Install MMAction2 and deps (pip)
Follow MMAction2’s install steps:
```
git clone https://github.com/open-mmlab/mmaction2.git
cd mmaction2
pip install -v -e .
```

## 4) Model configs, checkpoints, labels
Place or link your configs, checkpoints, and label map as referenced in the notebook:
- configs: e.g., configs\recognition\slowfast\slowfast_r50_...py
- checkpoints: e.g., checkpoints\slowfast\slowfast_r50_...pth
- labels: tools/data/kinetics/label_map_k400.txt

You can download official checkpoints from MMAction2 model zoo:
- https://mmaction2.readthedocs.io/en/latest/model_zoo/recognition.html
