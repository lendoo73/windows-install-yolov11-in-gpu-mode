# YOLOv11 GPU Mode

GPU setup, inference, counting, tracking, oriented bounding box, and custom-dataset
examples using Ultralytics YOLOv11.

This project accompanies the [YOLO Masterclass](https://www.udemy.com/course/yolo-masterclass-deep-learning-computer-vision-course/).

## Contents

- `bicep-curl-counter.py` - pose-based bicep curl counter.
- `car-parking-lot.py` - oriented-box vehicle detection and parking-lot counter.
- `object-tracking.py` - object tracking on video or webcam input.
- `person-counter.py` - person detection and counting.
- `datasets/` - road-sign, pothole, parking-lot, and chest X-ray dataset files and
  their training configurations.
- `inference/` and `result/` - example inputs and generated inference videos.
- `runs/` - best and custom-named model checkpoints only; generated predictions and training artifacts are excluded.
- `23-152_Install_YOLOv11_in_GPU_Mode.md` - concise GPU installation note.

## Installation

Use Python 3.10 or later and an NVIDIA GPU with a compatible CUDA driver. From the
project directory, create and activate a virtual environment:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
```

Install the PyTorch CUDA 13.2 wheels, then the remaining project dependencies:

```powershell
python -m pip install torch torchvision --index-url https://download.pytorch.org/whl/cu132
python -m pip install -r requirements.txt
```

For a different CUDA version or a CPU-only environment, select the matching
PyTorch installation command from the official
[PyTorch installation selector](https://pytorch.org/get-started/locally/).

## Examples

Run these commands from the project directory. The model arguments can point to
the included weights or another compatible YOLO model.

```powershell
python person-counter.py --model yolo11l.pt --video inference/videos/hotel.mp4
python object-tracking.py --model yolo11l.pt --video inference/videos/hotel.mp4
python bicep-curl-counter.py --model yolo11l-pose.pt --video inference/videos/bicep-curl.mp4 --save
python car-parking-lot.py --model runs/obb/yolo11l_obb_parking_lot/weights/best.pt --video inference/videos/car-parking-lot.mp4
```

The scripts accept `--model`, `--video`, and `--conf`; the video scripts also
accept `--save`. Pass `--video 0` to use the default webcam.

## Data, weights, and licensing

The folder includes dataset images and labels, example media, pretrained model
weights, and locally trained checkpoints. Large media, image, and model files are
stored with Git LFS. Run `git lfs install` before cloning or pulling so Git LFS
downloads those assets.

Dataset source and license details supplied with the files are retained in the
dataset directories. For example, the pothole and parking-lot dataset notes
identify their Roboflow sources and CC BY 4.0 licenses. Other media and datasets
may carry separate terms; consult their original sources before reuse.

No project-wide license is asserted. Third-party dataset, model, and media terms
remain applicable.
