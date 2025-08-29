# FYP: Head Impact Detection

This repository explores **AI-based methods for detecting player collisions and head impacts in AFL match footage**, developed in collaboration with **HITIQ** as part of a Monash University Final Year Project (FYP).  
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

---
## ⚙️ Getting Started


### 1. Clone the Repository
```bash
git clone https://github.com/CLKuok/fyp-head-impact-detection.git
cd fyp-head-impact-detection
