# DIY camera trap for automated insect monitoring

<img src="https://raw.githubusercontent.com/maxsitt/insect-detect-docs/main/docs/assets/logo.png" width="500">

[![DOI](https://zenodo.org/badge/580886977.svg)](https://zenodo.org/badge/latestdoi/580886977)
[![License badge](https://img.shields.io/badge/license-GPLv3-yellowgreen)](https://choosealicense.com/licenses/gpl-3.0/)

This repository contains Python scripts and a [YOLOv5s](https://github.com/ultralytics/yolov5)
detection model ([.blob format](https://docs.luxonis.com/en/latest/pages/model_conversion/))
for testing and deploying the Insect Detect DIY camera trap for automated insect monitoring.
The camera trap system is composed of low-cost off-the-shelf hardware components
([Raspberry Pi Zero 2 W](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/),
[Luxonis OAK-1](https://docs.luxonis.com/projects/hardware/en/latest/pages/BW1093.html),
[PiJuice Zero pHAT](https://uk.pi-supply.com/products/pijuice-zero)), combined with
open source software and can be easily assembled and set up with the
[provided instructions](https://maxsitt.github.io/insect-detect-docs/).

<img src="https://raw.githubusercontent.com/maxsitt/insect-detect-docs/main/docs/hardware/assets/images/insectdetect_diy_cameratrap.jpg" width="400">

## Installation

Instructions on how to install all required Python packages can be found in the
[**Insect Detect Docs**](https://maxsitt.github.io/insect-detect-docs/software/pisetup/#oak-1-configuration) 📑.

## Processing pipeline

More information about the processing pipeline can be found in the
[**Insect Detect Docs**](https://maxsitt.github.io/insect-detect-docs/deployment/detection/) 📑.

Processing pipeline for the `yolov5_tracker_save_hqsync.py` script that can be used for
continuous automated insect monitoring:

- The object tracker output (+ passthrough detections) from inference on LQ frames (e.g. 416x416) is synchronized
  with HQ frames (e.g. 3840x2160) in a script node on-device (OAK), using the respective sequence numbers.
- Detections (area of the bounding box) are cropped from the synced HQ frames and saved to .jpg.
- All relevant metadata from the detection model and tracker output (timestamp, label, confidence score, tracking ID,
  relative bbox coordinates, .jpg file path) is saved to a metadata .csv file for each cropped detection.

<img src="https://raw.githubusercontent.com/maxsitt/insect-detect-docs/main/docs/deployment/assets/images/hq_sync_pipeline.png" width="500">

<img src="https://raw.githubusercontent.com/maxsitt/insect-detect-docs/main/docs/deployment/assets/images/hq_frame_sync.png" width="500">

## License

All Python scripts are licensed under the GNU General Public License v3.0
([GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/)).

## Citation

You can cite this repository as:

```
Sittinger, M. (2022). Insect Detect - Software for automated insect monitoring
with a DIY camera trap system (v1.3). Zenodo. https://doi.org/10.5281/zenodo.7554302
```
