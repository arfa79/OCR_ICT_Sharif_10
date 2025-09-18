# OCR_ICT_Sharif_10

An end-to-end handwritten OCR project and experiment notebook originating from the ICT Sharif OCR exercises. The repository contains a runnable Jupyter notebook that runs preprocessing, model inference, and basic evaluation over a small handwritten dataset.

## What this repo contains

- `ocr_pipeline.ipynb` — Main Jupyter notebook implementing preprocessing, model loading, inference, postprocessing, and evaluation.
- `handwritten_data/` — Directory with input handwritten images used by the notebook.
- `model/` — Saved model artifacts (weights/config) used for inference.
- `ground_truth.txt` — Ground-truth transcriptions used to evaluate OCR outputs.
- `ocr_results.txt` — Last run OCR outputs produced by the notebook.
- `debug.log` — Runtime and debug logging captured during runs.
- `LICENSE` — License for the project.

## Purpose

This project demonstrates a simple OCR pipeline for handwritten text. It is intended for experimentation, reproduction of basic results, and as a starting point for improvements (better preprocessing, newer models, error correction, etc.).

## Quick start

Prerequisites
- Python 3.8+
- Jupyter or JupyterLab
- Typical ML and image packages: numpy, pillow, opencv-python, matplotlib, pandas
- A deep learning framework matching the saved model in `model/` (most likely PyTorch or TensorFlow). Inspect `ocr_pipeline.ipynb` or files inside `model/` to confirm.

Suggested setup (PowerShell):

```powershell
python -m venv .venv; .\.venv\Scripts\Activate.ps1; pip install --upgrade pip
pip install numpy pillow opencv-python matplotlib pandas jupyter
# add torch or tensorflow depending on model
```

Running the notebook
1. Start Jupyter in the repo root and open `ocr_pipeline.ipynb`.
2. Run cells top-to-bottom. The notebook will:
   - Preprocess images from `handwritten_data/`.
   - Load the model from `model/`.
   - Run inference and write predictions to `ocr_results.txt`.
   - Compute simple evaluation metrics vs `ground_truth.txt` and write logs to `debug.log`.

If you prefer a script-based run, inspect the first code cells — they include the key function calls and paths and can be copied into a `.py` runner.

## Outputs and evaluation

- `ocr_results.txt` contains predicted transcriptions (one prediction per line).
- `ground_truth.txt` contains the corresponding true transcriptions.

The notebook includes simple evaluation (exact match counts and basic error-rate calculations). For more rigorous evaluation consider computing Character Error Rate (CER) and Word Error Rate (WER) using standard packages.

## Notes, assumptions and troubleshooting

- The README does not pin exact dependency versions because the saved model framework is unspecified here. Check `ocr_pipeline.ipynb` and the contents of `model/` to determine whether you need PyTorch or TensorFlow and which version.
- If model loading fails, verify filenames inside `model/` and adjust load code in the notebook to match.
- If no images are detected, confirm `handwritten_data/` contains image files and that paths in the notebook point to that folder.
- Inspect `debug.log` for detailed runtime information.

## Suggested next steps (low-risk improvements)

1. Add a `requirements.txt` with pinned dependency versions.
2. Add a small CLI wrapper script to run preprocessing + inference outside the notebook.
3. Add unit tests for preprocessing functions and a small sample-run test that validates `ocr_results.txt` format.

## License
See `LICENSE` for the project license.

## Contact / Issues
Open an issue on this repository for questions, bug reports, or feature requests.
