# Figure 7: Same-frame detection comparison

Manuscript figure: **Fig. 7** (`fig:detection_comparison`). The historical
package index `12-` is retained in the directory name only.

This package generates a qualitative comparison on the 350-frame UIS-free
localization set.

## Evidence boundary

- Main images: MD2 frames under the controlled `automatic/images` directory.
- Manual reference: `artificial/labels`, the 350-file, 4,678-object manual
  annotation set reported in the manuscript.
- DPA auxiliary input: spatially aligned raw frames under `automatic/original`.
- Raw auxiliary frames and model weights remain in controlled storage and are
  not copied into this repository.

The similarly named `automatic/labels` directory is not used as reference. It
contains model-generated labels (348 files and 4,283 boxes), not the manuscript
manual-reference set.

## Models

- YOLOv8n-MD2+UIS: `Baseline_yolov8n/weights/best.pt`
- DPA-DH: `DPA_v1_DH/weights/best_slim.pt`
- DPA-Refine: `DPA_v1_Refine/weights/best_slim.pt`

All raw predictions use the manuscript evaluation settings: 640-pixel input,
confidence threshold 0.001, NMS IoU 0.7, and at most 300 detections per image.
The visualization applies a common confidence threshold of 0.25 and matches
predictions to manual boxes at IoU 0.5.

## Run

`code/run_detection_comparison.py` is published as the code that produced the
figure. It reads a customized Ultralytics checkout and a controlled dataset,
and the displayed cases are pinned by an explicit frame-selection argument.

**Neither the controlled inputs nor the frame-selection tokens are part of this
public archive**, so the published panel cannot be regenerated from this
archive alone. The frame selection and the mapping to the original dataset
filenames are held in the controlled reproducibility package described in
Supplementary Section S2 of the manuscript.

Box encoding in the model panels:

- blue solid: matched prediction (TP)
- vermillion solid with an internal cross: unmatched prediction (FP)
- magenta dashed: unmatched manual target (FN)
- orange solid in the first column: manual reference

The selected examples are descriptive samples, not an estimate of
population-level superiority. Quantitative conclusions remain those reported for
the complete 350-frame set.

Formal outputs are written to `fig/detection_comparison.png` and
`fig/detection_comparison.pdf`.

---

*This public archive ships the rendered figure and the figure code only. The
`data/` inputs referenced above travel with the controlled reproducibility
package (Supplementary Section S2) and are not redistributed here.*
