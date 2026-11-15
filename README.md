# LeukoTrack-NF — figure archive for the detection study

Rendered figures and figure-rendering code for a study of **frame-level
leukocyte-related response detection** in nailfold capillaroscopy (NFC) videos:

> **Modulation-Depth Enhancement and Dual-Path Attention for Weak-Signal
> Leukocyte Detection in Nailfold Capillaroscopy Videos**

This archive contains the seven figures of that detection study and the scripts
that produced them. It contains no downstream passage-quantification materials, no
participant-level recordings, and no annotation, prediction or evaluation
data.

## Figure ↔ package mapping

The `NN-` directory indices are historical package identifiers and are **not**
manuscript figure numbers. Manuscript numbering follows order of first
appearance.

| Manuscript figure | Label in the source | Package directory | Content |
|---|---|---|---|
| Fig. 1 | `fig:framework` | `figs/02-system_framework` | Detection-stage overview |
| Fig. 2 | `fig:enhancement` | `figs/03-enhancement_comparison` | Enhancement / metric comparison panels |
| Fig. 3 | `fig:uis_comparison` | `figs/06-UIS_diagnostic` | UIS on/off diagnostic panels |
| Fig. 4 | `fig:dpa_family` | `figs/01-DPA_family` | DPA detector family diagram |
| Fig. 5 | `fig:training_dynamics` | `figs/07-training_dynamics` | Training dynamics |
| Fig. 6 | `fig:activation_comparison` | `figs/11-feature_response` | Feature-map / activation comparison |
| Fig. 7 | `fig:detection_comparison` | `figs/12-detection_comparison` | Same-frame detection comparison |

Each package contains:

- `fig/` — the rendered figure used by the manuscript (PDF; a raster source is
  kept alongside it where one exists);
- `code/` — the plotting/processing code that renders or supports the figure
  (including the draw.io source for the diagram in Fig. 4);
- `README.md` — package-specific notes (where present).

All seven figures are main-text figures of the detection study; this archive
contains no supplementary figure.

## Method summary

The figures accompany a detection framework for weak, intermittent
leukocyte-related responses in NFC videos. Three components are described:

- **MD2** — a modulation-depth representation that stabilises motion and
  enhances weak transient signals while preserving vascular structure;
- **UIS** — Unlabeled Instance Suppression, which supports detector training
  under sparse, selectively generated annotations;
- **DPA** — a Dual-Path Attention detector family that fuses the enhanced
  representation with aligned raw frames through cross-attention at fine
  spatial scales, so that the two paths compensate for each other's limits.

Five DPA configurations are compared with single-branch attention and recent
detectors on a frame-level localization task. This archive documents the
figures only; the study reports frame-level detection results and does not
report any downstream passage quantification.

## Typography and artwork

- The artwork set uses one sans-serif family, **Arial**; the Fig. 4 draw.io
  export realises it with the metric-compatible Liberation Sans, the Fig. 1
  vector export embeds Arial subsets, and in the raster panels the lettering
  is baked into the pixels.
- No figure contains Type 3 fonts. Where lettering is not part of a raster
  panel it is drawn as vector outlines or embedded as a Type 0 (TrueType)
  subset.
- Fig. 5 is fully vector. Fig. 1 is a vector PDF: its lettering and connecting
  strokes are selectable text and vector paths, while the photographic and
  response panels it displays are embedded as raster images. Fig. 4 is a
  vector drawing with embedded raster panels. Figs. 2, 3, 6 and 7 are raster
  panels delivered as PDF wrappers with no font resources, at 400–600 dpi
  relative to their printed width. Fig. 1 is the detection-stage crop of the
  framework; its full draw.io source is retained in the controlled
  reproducibility package.

## Regenerating the figures

The rendered PDFs are the figures of record; the scripts are published as the
code that produced them. **Every plotting script reads its inputs from a
controlled `data/` directory that is not redistributed here.** The commands
below therefore document how each figure was made — they do not run against
this archive alone. This boundary is intentional, not a gap in the release.

With the controlled inputs staged, run each script from its own package
directory, for example:

```text
# Fig. 5  (figs/07-training_dynamics)
python code/plot_training_focus.py
```

For Fig. 7, the displayed cases are pinned in the controlled reproducibility
package. Neither the frame-selection tokens nor the controlled inputs are
included in this public archive, so the published panel cannot be regenerated
from this archive alone; the script and the rendered figure are provided for
inspection.

## Scope and data boundary

This public archive contains **only rendered figures and figure-rendering
code**. It does not contain:

- original human-subject videos or raw image collections;
- annotation files, prediction files, evaluation outputs or other analysis
  inputs;
- frame identifiers, participant codes, batch-to-video mappings, consent
  records, real names, hospital identifiers or identity-linkage keys;
- downstream passage-quantification materials;
- model checkpoints or superseded figure variants.

Any `data/` path still mentioned in a package README refers to the controlled
reproducibility package; those directories are not redistributed here.

The displayed imagery is de-identified and was derived from the two 2026
acquisition batches under approval no. GUET-EC-2026-001 (Guilin University of
Electronic Technology) and no. 2026041601 (People's Hospital of Nanhai
Economic Development Zone).

## Data and code availability

The executable training code, model checkpoints and the privacy-compatible
derived materials are withheld from public release because the underlying
recordings were acquired from human participants under institutional ethics
approvals and written informed consent. They are deposited in this repository
upon acceptance of the manuscript. De-identified participant-level videos are
available from the first author upon reasonable request, subject to approval
by the relevant ethics committees; consent records and batch-to-video mappings
remain under institutional control and are never released.

## Interpretation boundary

Having a rendered figure and a plotting script does not by itself establish
end-to-end reproducibility. A figure is complete only when the exact input
data, processing parameters, source code, and, where applicable, model
checkpoint can be identified and retained.

## Licensing

Two licences apply, split by material type:

- **Code** — every script, configuration and diagram source in this archive
  (`.py`, `.yaml`, `.drawio`) is released under the [MIT License](LICENSE).
- **Figures** — every rendered file under `figs/**/fig/` (`.pdf`, `.png`) is
  released under [CC BY 4.0](LICENSE-figures); reuse should credit the
  manuscript named above.

Neither licence extends to the underlying human-subject recordings or the
de-identified derived data, which remain governed by the ethics approval and
informed-consent terms described in the manuscript.
