# AccidentVision

AccidentVision is a YOLO-based traffic incident detection project. The repository now keeps only the source code, configuration, and notebook. The original training and test images, along with generated run artifacts, are no longer committed so the repository stays lightweight.

## Project Summary

The project detects two classes in traffic footage:

- accident
- non-accident

The notebook trains a YOLOv9e model, evaluates it on the held-out test split, and runs video inference with the trained checkpoint.

## What Is Included

- `main.ipynb` for training, validation, and inference
- `data.yaml` for dataset configuration
- `README.md`

## Dataset Configuration

`data.yaml` defines two classes:

- accident
- non-accident

The dataset image folders are not stored in this repository. If you want to retrain the model, point `data.yaml` to your local dataset paths and generate the outputs locally.

The notebook uses the following training setup:

- base model: `yolov9e.pt`
- epochs: 25
- image size: 250
- batch size: 6
- workers: 8
- device: GPU 0

## Model Performance

The last recorded training epoch in the saved history reported the following metrics:

- precision: 0.78298
- recall: 0.74298
- mAP@0.50: 0.82092
- mAP@0.50:0.95: 0.60247

These values give a concise view of the model’s detection quality. In practical terms, the model reached about 82% mAP@0.50 on the final recorded epoch.

## Notebook Workflow

The notebook `main.ipynb` currently:

1. Loads `yolov9e.pt`.
2. Trains the model on the local dataset with the hyperparameters above.
3. Loads the best checkpoint generated during training.
4. Runs test-time validation and prints the final mAP@0.50.
5. Runs video inference and saves annotated outputs locally.

## Code Details

The notebook is organized into three main parts:

1. Training setup: imports Ultralytics YOLO, loads the pretrained YOLOv9e weight file, and starts training using `data.yaml`.
2. Evaluation: loads the trained best checkpoint and evaluates it on the test split with JSON export enabled.
3. Inference: loads the best checkpoint again and runs prediction on a video source with a confidence threshold of 0.25.

This makes the notebook a complete end-to-end pipeline for training, testing, and inference in one place.

## Saved Outputs

The repository does not keep generated run artifacts. Train and validation outputs should be recreated locally when needed.

## How To Run

Install dependencies:

```bash
pip install ultralytics
```

Then open `main.ipynb` and execute the cells in order.

## Status

The repository has been trimmed to source code and configuration only. The dataset images and generated outputs are no longer part of the repository.