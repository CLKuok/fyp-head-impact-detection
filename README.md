# Head Impact Detection — Overview

This project investigates automatic detection of player collisions and potential head impacts in AFL match footage, developed with HITIQ as part of a Monash University Final Year Project. The pipeline combines player tracking with action recognition to surface candidate impact events for review and future alignment with HITIQ’s smart mouthguard data.

Status: In progress  
Last updated: 02 Dec 2025 (AEST)

## What’s in this repository

- player-tracker/
  - Purpose: Detect players and track them across frames.
  - Core tech: YOLO (v5/v8) for detection, ByteTrack for multi-object tracking.
  - Outputs: Overlaid videos, per-frame tracks, optional player crops for downstream models.
  - Notebook: player-tracker/notebook/impact_detection_tracker.ipynb
  - Weights: player-tracker/weights/ (see its README)
  - Setup: player-tracker/README.md (Conda-first, pip for extras)

- action-recogition/
  - Purpose: Classify video segments (e.g., impact vs non-impact) using Human Action Recognition.
  - Core tech: MMAction2 (e.g., TSN/TSM/SlowFast).
  - Outputs: Class probabilities, event timelines, evaluation summaries.
  - Notebook: action-recogition/Evaluation.ipynb
  - Checkpoints: action-recogition/checkpoints/ (subfolders per model: tsm/, tsn/, slowfast/)
  - Setup and layout tips: action-recogition/README.md

## Typical workflow

1) Tracking
- Run the player-tracker notebook on match footage to produce tracks and, optionally, player-centric crops or time windows.

2) Action recognition
- Run the action-recogition notebook on the cropped clips or windows to classify impact vs non-impact and generate event candidates.

3) Review and integration
- Inspect overlays and prediction summaries; plan alignment with HITIQ mouthguard timelines for validation.

## Acknowledgements

- Ultralytics YOLO and ByteTrack for tracking foundations.
- OpenMMLab MMAction2 for action recognition.
- Football-Players-Tracking for pretrained football player detectors used in early baselines.
- HITIQ for collaboration context and downstream integration goals.

For environment setup and command details, see the component READMEs in player-tracker/ and action-recogition/.