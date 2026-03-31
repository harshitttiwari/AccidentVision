# AccidentVision

AccidentVision is a computer vision project for traffic incident detection using Ultralytics YOLO.
The model is trained to classify two object categories:

- accident
- non-accident

## What I Have Completed

- Prepared a custom dataset split into train, validation, and test sets.
- Configured dataset metadata in `data.yaml` with two classes.
- Trained a YOLOv9e model using the Ultralytics pipeline.
- Saved training artifacts, curves, confusion matrices, and best weights.
- Evaluated the trained model on the test split.
- Ran video inference and exported prediction results.

## Project Structure

```text
Acidental/
	data.yaml
	main.ipynb
	yolov9e.pt
	train/
	valid/
	test/
	runs/detect/
		train1/
		val2/
		predict/
```

## Dataset Configuration

The project uses:

- Number of classes: 2
- Class names: accident, non-accident
- Train images: `train/images`
- Validation images: `valid/images`
- Test images: `test/images`

## Training and Evaluation Highlights

From `runs/detect/train1/results.csv`:

- Final precision (B): 0.78298
- Final recall (B): 0.74298
- Final mAP@0.50 (B): 0.82092
- Final mAP@0.50:0.95 (B): 0.60247

Generated artifacts include:

- PR and F1 curves
- Confusion matrices (raw and normalized)
- Label visualizations
- Train and validation prediction previews
- Best model checkpoint at `runs/detect/train1/weights/best.pt`

## Notebook Workflow

The notebook `main.ipynb` performs:

1. Model training with YOLOv9e.
2. Loading the trained best checkpoint.
3. Test split validation and metric reporting.
4. Video inference with saved outputs in `runs/detect/predict*`.

## How To Run

Install dependencies:

```bash
pip install ultralytics
```

Run the full pipeline from the notebook:

- Open `main.ipynb`
- Execute cells sequentially to train, validate, and run inference

Or run from Python scripts/terminal using the same Ultralytics calls used in the notebook.

## Status

This project is implemented end-to-end:

- Dataset configured
- Model trained
- Metrics generated
- Inference tested on video
- Artifacts and run outputs saved under `runs/`