# FYP: Head Impact Detection

This repository explores **AI-based methods for detecting player collisions and head impacts in AFL match footage**, developed in collaboration with **HITIQ** as part of a Monash University Final Year Project.  
The project investigates player detection, tracking, and impact classification using deep learning models, with the eventual goal of integrating video-based analysis with HITIQ’s smart mouthguard system.

---

## 🚀 Project Overview

Concussions are a major concern in contact sports, and current workflows at HITIQ require manual review of match footage to validate mouthguard-recorded events.  
This project aims to reduce manual workload and improve efficiency by developing an AI pipeline capable of automatically detecting and classifying head impacts from video.

---

## 📂 Project Structure

```bash
fyp-head-impact-detection/
├── data/                # Dataset instructions (not raw AFL videos)
│   └── README.md        # How to prepare datasets
├── notebooks/           # Jupyter notebooks for experiments
├── src/                 # Source code
│   ├── detection/       # YOLO-based player detection
│   ├── action/          # MMAction2 / HAR models for impact classification
│   └── utils/           # Preprocessing & evaluation helpers
├── results/             # Model outputs, metrics, visualisations
├── reports/             # Project findings, diagrams
├── requirements.txt     # Python dependencies
└── README.md            # This file
```

---

## ⚙️ Getting Started

**1. Clone the Repository**
```bash
git clone https://github.com/CLKuok/fyp-head-impact-detection.git
cd fyp-head-impact-detection
```

**2. Install Dependencies**
```bash
pip install -r requirements.txt
```

**3. Dataset Preparation**

Due to privacy, raw AFL/HITIQ footage is not included.  
Follow `data/README.md` for instructions on:

- Extracting frames from videos
- Organising YOLO-format datasets
- Preparing impact/non-impact clips for MMAction2

---

## 🧠 Methodology

The project is divided into three key stages:

1. **Player Detection & Tracking**
   - YOLOv5/YOLOv8 for detecting players in AFL footage
   - Tracking algorithms (DeepSORT, ByteTrack) for consistent IDs

2. **Impact Motion Classification**
   - Human Action Recognition models (TSN, SlowFast, etc.)
   - Trained on clips labelled as impact or non-impact (from XML annotations & HITIQ data)

3. **Integration & Evaluation**
   - Match detected events with HITIQ’s smart mouthguard data
   - Evaluate performance using metrics (mAP@0.5, Precision, Recall, F1)

---

## 📊 Results & Findings (Work in Progress)

| Model         | mAP@0.5 | Precision | Recall | Notes                 |
|---------------|---------|----------|--------|-----------------------|
| YOLOv5x       | TBD     | TBD      | TBD    | AFL player detection  |
| TSN (MMAction)| TBD     | TBD      | TBD    | Impact classification |

---

## 🛠 Tools & Frameworks

- PyTorch
- YOLOv5 / YOLOv8
- MMAction2
- CVAT (for data annotation)

---

## 📅 Next Steps

- Prepare and label AFL player detection dataset (YOLO format)
- Extract impact/non-impact clips from annotated XML + videos
- Train and benchmark TSN/SlowFast models on action recognition
- Integrate detection + HAR for full pipeline evaluation

---

## 📜 License

⚠️ To be decided (MIT, Apache 2.0, or private depending on HITIQ requirements).

---

## 🔗 References & Acknowledgements

This work is conducted as part of the Monash University Mechatronics & Robotics Engineering FYP, with industry collaboration from HITIQ.

- [Darkmyter/Football-Players-Tracking](https://github.com/Darkmyter/Football-Players-Tracking):  
  Provided the original training code and pretrained YOLOv5/YOLOv8 weights for football player detection.  
  In this project, we reused those pretrained weights but tested them on our own AFL dataset for evaluation.
