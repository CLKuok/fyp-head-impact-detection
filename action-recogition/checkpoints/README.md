# Checkpoints

Place downloaded model weights (checkpoints) in this folder, organized by model family. Example structure:
```
action-recogition/
└─ checkpoints/
   ├─ tsm/
   │  └─ tsm_imagenet-pretrained-r50_8xb16-1x1x8-50e_kinetics400-rgb_20220831-64d69186.pth
   ├─ tsn/
   │  └─ tsn_imagenet-pretrained-r50_8xb32-1x1x8-100e_kinetics400-rgb_20220906-2692d16c.pth
   └─ slowfast/
      └─ slowfast_r50_8xb8-8x8x1-steplr-256e_kinetics400-rgb_20220818-b62a501f.pth
```

Guidelines:
- Create a subfolder per model family (e.g., tsm, tsn, slowfast).
- Keep official filenames to match config references.
- Update paths in your notebooks/scripts to point to these files.

More checkpoints and links:
- https://mmaction2.readthedocs.io/en/latest/model_zoo/recognition.html