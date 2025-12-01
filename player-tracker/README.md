# Player Tracker — Environment Setup (Conda + Pip)

This folder provides a Conda-first setup, with any missing packages installed via pip. Use both files here:
- Conda: [player-tracker/conda-spec.txt](player-tracker/conda-spec.txt)
- Pip: [player-tracker/requirements.txt](player-tracker/requirements.txt)

If you need ByteTrack/YOLO extras, see [player-tracker/notebook/README.md](player-tracker/notebook/README.md).

## 1) Prerequisites
- Anaconda or Miniconda (recommended)
- Git (optional, for extras)
- NVIDIA GPU + CUDA drivers (optional, for GPU acceleration)

## 2) Create and activate the Conda environment
Start with a fresh Python and install from spec:
```sh
conda create -n player-tracker -y python=3.10
conda activate player-tracker
# Install packages listed in conda-spec.txt (or refer to the source github repo)
conda install -y --file conda-spec.txt -c conda-forge -c pytorch -c nvidia
```
Note: Tested with Python 3.10.17.

## 3) Install remaining packages via pip
For YOLO/ByteTrack extras, use the commands shown in the notebook README:
- See: [player-tracker/notebook/README.md](player-tracker/notebook/README.md)
- It includes the pip commands for:
  - YOLOv5 (`%pip install -qr requirements.txt` inside the cloned repo)
  - YOLOv8 (`pip install ultralytics`)
  - ByteTrack (`pip install -r ByteTrack/requirements.txt` and `python ByteTrack/setup.py develop`, plus `pip install cython_bbox onemetric`)

Tip (GPU PyTorch): if PyTorch/CUDA is not set by Conda yet, install a matching build from PyTorch:
- https://pytorch.org/get-started/locally

I've also included the conda-spec.txt and requirements.txt if you want to install this way.

## 4) Weights
Download any required model weights into [player-tracker/weights](player-tracker/weights/README.md) as described there.

## 5) Run the notebook
- Open VS Code, select the `player-tracker` Conda kernel.
- Open and run: [player-tracker/notebook/impact_detection_tracker.ipynb](player-tracker/notebook/impact_detection_tracker.ipynb)