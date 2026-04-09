# AccidentVision

AccidentVision is a YOLO-based traffic incident detection project. The repository keeps the source code, configuration, notebook, and the saved training and validation run outputs. The original training and test images are not committed, so the repository stays lighter while still preserving the model results.

## Project Summary

The project detects two classes in traffic footage:

- accident
- non-accident

The notebook trains a YOLOv9e model, evaluates it on the held-out test split, and runs video inference with the trained checkpoint.

## What Is Included

- `main.ipynb` for training, validation, and inference
- `data.yaml` for dataset configuration
- `runs/detect/train1/` for saved training artifacts
- `runs/detect/val2/` for saved validation artifacts
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

The repository includes the generated run artifacts again, mainly under:

- `runs/detect/train1/` for the training curves, batch previews, and `results.csv`
- `runs/detect/val2/` for validation plots and `predictions.json`

These folders provide the trained model outputs without requiring a fresh run.

## How To Run

Install dependencies:

```bash
pip install ultralytics
```

Then open `main.ipynb` and execute the cells in order.

## Status

The repository now includes the code, notebook, configuration, and the saved train and validation outputs. The dataset images are still excluded.