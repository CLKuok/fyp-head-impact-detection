# FYP: Head Impact Detection

This repository explores **AI-based methods for detecting player collisions and head impacts in AFL match footage**, developed in collaboration with **HITIQ** as part of a Monash University Final Year Project.  
The project investigates player detection, tracking, and impact classification using deep learning models, with the eventual goal of integrating video-based analysis with HITIQ’s smart mouthguard system.

---
> **Status:** In progress  
> **Last updated:** 29 Aug 2025 (AEST)

## 🗓 Project Timeline (Rev. Sept 2025)

### ✅ Completed
- Evaluated YOLOv5/YOLOv8 (football-trained) on custom AFL frames; baseline metrics recorded.
- Reviewed two action-recognition approaches (MMAction2-based) for impact-related motion.
- Set up data pipelines: frame extraction, YOLO-format annotations, clip generation prototype.

### 🔜 Near Term (Sept–Oct 2025)
- Fine-tune YOLO on AFL-specific annotations to improve precision under occlusion/dense play.
- Prototype heuristic impact detection (sudden bbox velocity/acceleration) as a baseline.
- Curate initial impact/non-impact clips (from provided clips + interim alignment of XML timestamps).

### 🔭 Mid Term (Oct–Nov 2025)
- Train/evaluate HAR model (e.g., TSN/SlowFast) on curated clips (binary: impact vs non-impact).
- Integrate detection → tracking → HAR on candidate windows; produce event lists for review.

### 🤝 Integration (Rolling)
- Align model outputs with HITIQ mouthguard timelines for validation and triage.
- Document limitations, failure modes, and data needs for AFL-specific robustness.

## 📅 Next Steps (Snapshot)
- **Fine-tune player detection** on AFL frames.  
- **Prototype intuitive impact detection** using bbox dynamics.  
- **Prepare/expand impact vs non-impact clip set** for HAR training.

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

The methodology for this project follows three main stages:

1. **Dataset Preparation**  
   AFL match footage was processed into datasets for both detection and classification tasks. Frames were extracted at fixed intervals and annotated for player detection, then organised in YOLO format. For impact detection, two complementary sources were used:  
   - **Clipped impact footage provided by HITIQ**, which is being consolidated into a centralised repository for streamlined access.  
   - **XML annotations of mouthguard-recorded impacts**, which currently require further alignment with the corresponding match footage to enable automated clip extraction.  
   These combined sources are intended to provide both impact and non-impact samples for training Human Action Recognition (HAR) models.

2. **Model Survey and Evaluation**  
   Existing open-source models and tools were reviewed and tested for their suitability in head impact detection. This included pretrained YOLOv5/YOLOv8 models (sourced from the *Football-Players-Tracking* repository) for player detection, and Human Action Recognition frameworks such as MMAction2 (TSN, SlowFast) for impact motion classification. Each model was evaluated qualitatively and quantitatively against AFL-specific data, with particular focus on challenges such as dense player distributions, occlusion, and the absence of helmets.

3. **Fine-Tuning and Integration**  
   Promising models were adapted and fine-tuned using AFL-specific datasets to improve detection precision and robustness. The outputs of player detection and impact classification modules were then considered for integration into a unified workflow, with the aim of supporting HITIQ’s smart mouthguard ecosystem by aligning predicted impact events with sensor timelines.

---

## 📊 Results & Findings (Work in Progress)

The following table summarises detection performance across four YOLO model variants, tested on our custom AFL dataset.  
Pretrained weights for these models were sourced from the [Football-Players-Tracking repository](https://github.com/Darkmyter/Football-Players-Tracking), and evaluation was carried out on AFL match footage annotated for this project.

| Model           | mAP@0.5 | Precision | Recall | F1-Score | Total Predictions |
|-----------------|---------|-----------|--------|----------|-------------------|
| YOLOv8m-640     | 0.8311  | 0.3166    | 0.9820 | 0.4788   | 3797              |
| YOLOv8l-640     | 0.8325  | 0.3304    | 0.9847 | 0.4947   | 3690              |
| YOLOv5m-1280    | 0.8099  | 0.3605    | 0.9950 | 0.5293   | 3858              |
| YOLOv5x-1280    | 0.8051  | 0.3835    | 0.9959 | 0.5537   | 3763              |

**Notes:**  
- Pretrained YOLOv5 and YOLOv8 weights were originally trained on the football-players-detection dataset (Roboflow) via the Football-Players-Tracking project.  
- Our contribution is testing and benchmarking these models on AFL data, which poses unique challenges compared to soccer/football datasets: AFL features more frequent occlusions, denser player distributions, different jersey styles, and the absence of helmets, all of which increase false positives and reduce precision.   
- Recall and F1-Score are notably high across models, indicating strong capability for locating players, while precision remains a challenge in crowded AFL scenes.  
- Evaluation time and inference speed were comparable across models, with larger architectures (YOLOv5x/YOLOv8l) offering marginal improvements in F1 but not in precision.

**More to come...**
---

## 🛠 Tools & Frameworks

- PyTorch
- YOLOv5 / YOLOv8
- MMAction2
- CVAT (for data annotation)

---

## 📅 Next Steps

- **Fine-tune Player Detection**  
  Adapt and fine-tune the football-trained YOLO models on AFL-specific annotated frames to improve detection precision and robustness under occlusion and dense player distributions.

- **Prototype Intuitive Impact Detection**  
  Explore heuristic methods for identifying potential head impacts, such as detecting sudden changes in player bounding box position or velocity. This will serve as an initial baseline until clipped impact datasets are fully available.

- **Head Detection and Localisation**  
  Investigate the feasibility of detecting and tracking heads (or upper body regions) directly, as a precursor to linking visible impact events with sensor-based mouthguard data.

## ⚠️ Limitations and Challenges

Several challenges were encountered during the early stages of this project, primarily related to data preparation and domain-specific complexity:

- **Data alignment:**  
  While XML annotations from mouthguard sensors contain valuable impact information, they are not yet directly aligned with the corresponding match footage. Additional processing is required to synchronise these data streams before automated clip extraction can be achieved.

- **Data availability and consolidation:**  
  Impact clips are being progressively consolidated into a centralised repository for streamlined access. This is part of the ongoing data management process in the collaboration and will enable more efficient training and evaluation once fully established.

- **Domain-specific complexity:**  
  AFL footage introduces unique challenges compared to existing sports datasets (e.g., soccer or American football). These include high player density, frequent occlusions, and the absence of helmets, which contribute to reduced precision in detection models.

These challenges are not unusual in applied AI projects and highlight the importance of careful dataset curation, preprocessing, and iterative model adaptation. They also provide opportunities for future work in developing more robust multi-modal alignment techniques and AFL-specific training datasets.
---

## 📜 License

⚠️ To be decided (MIT, Apache 2.0, or private depending on HITIQ requirements).

---

## 🔗 References & Acknowledgements

This work is conducted as part of the Monash University Mechatronics & Robotics Engineering FYP, with industry collaboration from HITIQ.

- [Darkmyter/Football-Players-Tracking](https://github.com/Darkmyter/Football-Players-Tracking):  
  Provided the original training code and pretrained YOLOv5/YOLOv8 weights for football player detection.  
  In this project, we reused those pretrained weights but tested them on our own AFL dataset for evaluation.
