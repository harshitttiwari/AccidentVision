# AccidentVision

AccidentVision is a YOLO-based traffic incident detection project. The repository now keeps only the source code, configuration, and notebook. The original training and test images, along with generated run artifacts, are no longer committed so the repository stays lightweight.

## What Is Included

- `main.ipynb` for training, validation, and inference
- `data.yaml` for dataset configuration
- `README.md`

## Dataset Configuration

`data.yaml` defines two classes:

- accident
- non-accident

The dataset image folders are not stored in this repository. If you want to retrain the model, point `data.yaml` to your local dataset paths and generate the outputs locally.

## Notebook Workflow

The notebook `main.ipynb` currently:

1. Loads `yolov9e.pt`.
2. Trains the model on the local dataset.
3. Loads the best checkpoint generated during training.
4. Runs validation and saves results locally.
5. Runs inference and writes outputs locally.

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