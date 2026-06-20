# UltimateLabeling

![Build Status](https://img.shields.io/github/actions/workflow/status/alexandre01/UltimateLabeling/ci.yml?branch=master)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python 3.10+](https://img.shields.io/pypi/pyversions/ultimatelabeling.svg)
![PyPI](https://img.shields.io/pypi/v/ultimatelabeling.svg)
![GitHub stars](https://img.shields.io/github/stars/alexandre01/UltimateLabeling.svg?style=social)

A multi-purpose **Video Labeling GUI** in Python with integrated SOTA detector and tracker. Developed using PyQt5, updated with 2025-2026 tools and models.

## Overview

UltimateLabeling provides an all-in-one video annotation tool with integrated object detection, pose estimation, and visual tracking — designed for creating high-quality training datasets for computer vision models.

## What's New (2025-2026)

- **YOLO11 / YOLOv9**: Latest Ultralytics models for detection and segmentation
- **SAM-2 Integration**: Segment Anything Model 2 for interactive and automatic segmentation
- **RT-DETR**: Real-time transformer-based detection
- **Grounding DINO**: Text-prompted object detection (zero-shot)
- **MMPose / RTMPose**: Modern pose estimation pipeline
- **FastSAM**: Fast segment anything for real-time annotation
- **CLIP Embeddings**: Semantic search for labeled frames
- **CUDA 12.x / cuDNN 8.9+**: GPU acceleration
- **ONNX Runtime**: Cross-platform inference backend
- **Dark Mode** improved with custom themes

## Features

- SSH connection to remote GPU server
- **YOLO11, YOLOv9** integrated object detection (single frame/video)
- **SAM-2 / FastSAM** automatic and interactive segmentation
- **Grounding DINO** text-prompted detection (describe what to find)
- **RTMPose** human pose estimation
- Hungarian algorithm for track_id assignment
- SiamMask visual object tracking
- CLIP-based semantic search for annotation quality
- Zoom on video, resizable bounding boxes and skeletons
- Dark mode with customizable themes

## Supported Detectors

| Detector | Type | Speed | mAP |
|----------|------|-------|-----|
| YOLO11 | Detection | Real-time | 53.9 (COCO) |
| YOLOv9 | Detection | Real-time | 53.0 (COCO) |
| RT-DETR | Detection | Real-time | 54.8 (COCO) |
| Grounding DINO | Zero-shot | Near real-time | 52.5 (COCO) |
| SAM-2 | Segmentation | Near real-time | 85.6 (SA-V) |
| FastSAM | Segmentation | Real-time | 74.2 (SA-1B) |
| OpenPifPaf | Pose | Real-time | 72.6 (COCO) |
| RTMPose | Pose | Real-time | 77.0 (COCO) |

## Installation

```bash
git clone https://github.com/alexandre01/UltimateLabeling.git
cd UltimateLabeling

# Create virtual environment
python -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Launch GUI
python -m ultimatelabeling.main
```

### GPU Acceleration

```bash
# Install CUDA toolkit (12.x)
pip install torch torchvision --index-url https://download.pytorch.org/whl/cu121

# Install ONNX Runtime GPU
pip install onnxruntime-gpu
```

## Remote Server Setup

```bash
git clone https://github.com/alexandre01/UltimateLabeling_server.git
cd UltimateLabeling_server
pip install -r requirements.txt
bash siamMask/setup.sh
bash detection/setup.sh
```

Place data in `data/` folder. Extract video frames:
```bash
bash extract.sh data/video_file.mp4
```

## Input / Output

- **Import labels**: `Cmd+I` / `Ctrl+I` — CSV format: `class_id, xc, yc, w, h`
- **Export labels**: `Cmd+E` / `Ctrl+E` — exports to unified CSV file

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `A` / `←` | Next frame |
| `D` / `→` | Previous frame |
| `W` / `S` | Class up/down |
| `T` | Start/stop tracking |
| `Spacebar` | Play/pause video |
| `Cmd+Click` | Create bounding box |
| `Right Click` | Delete bounding box |
| `Scroll` | Zoom in/out |

<img src="docs/keyboard_shortcuts.jpg" width="50%" />

## Modern Annotation Workflow (2025-2026)

```
Video Input → Frame Extraction → Auto-Detection (YOLO11)
                                    ↓
                            SAM-2 Refinement
                                    ↓
                         Track Assignment (Hungarian)
                                    ↓
                         Manual Review & Correction
                                    ↓
                         Export (COCO/YOLO/VOC format)
```

### Integration with Modern Tools

- **Roboflow**: Export directly to Roboflow for model training
- **FiftyOne**: Dataset analysis and quality control
- **CVAT**: Import/export compatibility
- **Label Studio**: Format conversion support

## Related Tools (2025-2026)

| Tool | Purpose | Year |
|------|---------|------|
| **SAM-2** | Video segmentation | 2024 |
| **Grounding DINO** | Text-prompted detection | 2023-2024 |
| **RT-DETR** | Real-time transformer detection | 2023-2024 |
| **YOLO11** | Latest real-time detection | 2025 |
| **RTMPose** | Efficient pose estimation | 2023-2024 |
| **FiftyOne** | Dataset curation | 2024-2025 |
| **FiftyOne** | Dataset curation | 2024-2025 |

## License

Copyright (c) 2019 Alexandre Carlier. Released under the MIT License.

## Contributing

Please write a GitHub issue for bugs or feature requests, or submit a pull request.
