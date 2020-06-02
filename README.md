# MM-SADA_Domain_Adaptation_Splits
This repository contains the annotations for the domain adaptation dataset used in the paper [Multi-Modal Domain Adaptation for Fine-Grained Action Recognition](https://arxiv.org/abs/2001.09691). 

## Annotations
Three domains are defined as D1, D2 and D3 from individual kitchens in the EPIC Kitchens dataset (P08, P01 and P22 respectively).

`D*_train.pkl` - Contains action segments for either a labelled source or unlabelled target domain. For an unlabelled target domain only video id's and timestamps should be used.

`D*_test.pkl`  - Contains action segments for evaluation only.

`verb_class` is a numeric id used as the ground truth action prediction in this work.

Each pickle file contains a pandas.DataFrame with 10 columns:

| Column Name         | Type                         | Example          | Description                                                                                                           |
| ------------------- | ---------------------------- | ---------------- | --------------------------------------------------------------------------------------------------------------------- |
| `uid`               | int                          | `12917`           | Unique ID of the segment.                                                                                             |
| `video_id`          | string                       | `P08_01`         | Video the segment is in.                                                                                              |
| `narration`         | string                       | `close fridge`   | English description of the action provided by the participant.                                                        |
| `start_timestamp`   | string                       | `00:00:07.29`   | Start time in `HH:mm:ss.SSS` of the action.                                                                           |
| `stop_timestamp`    | string                       | `00:00:08.95`   | End time in `HH:mm:ss.SSS` of the action.                                                                             |
| `start_frame`       | int                          | `437`          | Start frame of the action (WARNING only for RGB frames extracted as detailed in [Video Information](https://github.com/epic-kitchens/annotations/#video-information)). |
| `stop_frame`        | int                          | `537`          | End frame of the action (WARNING only for RGB frames  extracted as detailed in [Video Information](https://github.com/epic-kitchens/annotations/#video-information)).  |
| `participant_id`    | string                       | `P08`            | ID of the participant.                                                                                                |
| `verb`              | string                       | `close`          | Parsed verb from the narration.                                                                                       |
| `verb_class`        | int                          | `3`              | Numeric ID of the parsed verb's class.          

### Flow modality start and stop times
Optical Flow was calcuated with a stride=2 in EPIC Kitchens, therefore the start and stop frames for the Flow modality are (`start_frame/2`, `stop_frame/2`).

## Downloading Frames
The download scripts for EPIC Kitchens are avaialable here: https://github.com/epic-kitchens/download-scripts. Alternatively, download_script.sh is provided that will download the relevent participants P08, P02 and P22 into the below directory structure. Unless an argument is specfied, the directory structure will be created in `"$HOME/Downloads/EPIC_KITCHENS_UDA"`.


```
~/Downloads/EPIC_KITCHENS_2018/
└── frames_rgb_flow
    ├── rgb
    │   ├── test
    │   │   ├── D1
    │   │   │   ├── P08_10.tar
    │   │   │   ├── ...
    │   │   ├── D2
    │   │   │   ├── P01_11.tar
    │   │   │   └── ...
    │   │   └── D3
    │   │       ├── P22_01.tar
    │   │       └── ...
    │   └── train
    │       ├── D1
    │       │   └── ...
    │       ├── D2
    │       │   └── ...
    │       └── D3
    │           └── ...
    └── flow
        ├── ... same file structure as rgb

```
## BibTeX
If this repository was used in future work please use this citation:
```
@InProceedings{munro20multi,
author = "Munro, Jonathan and Damen, Dima",
title = "{M}ulti-modal {D}omain {A}daptation for {F}ine-grained {A}ction {R}ecognition",
booktitle = "Computer Vision and Pattern Recognition (CVPR)",
year = "2020"
}
```
