# Geometry-Aware Mid-Training for World-Action Models

> **Work in progress.** This repository currently hosts the project page only.
> The paper is under review; paper, code, and models are not yet released.

Project page: https://junhahyung.github.io/geometry-aware-midtraining/

Junha Hyung\*, Hyojin Jang\*, Jaegul Choo — KAIST AI  (\* equal contribution)

## Summary

A two-stage, geometry-aware recipe for video-based world-action models:

1. **Stage 1 — geometry-aware mid-training.** Mid-train the pretrained video backbone to
   predict per-frame depth alongside RGB on abundant, cheap data (robot play video and
   in-the-wild video with estimated depth), with no action or value targets.
2. **Stage 2 — joint action, frame, and depth prediction.** Fine-tune into a world-action
   model that jointly predicts action, future RGB, proprioception, value, **and** depth.

Depth is treated as pseudo-RGB and reuses the existing video VAE, so no architectural
change is required. At inference the depth slots are fed as blank placeholders — the
policy needs no depth sensor, and the gain is a pure representation-level effect.

On 24 RoboCasa manipulation tasks, mean success rises from **60.8% → 69.0%** with depth
co-training alone, and to **79.2% (+18.4)** with the full two-stage recipe.

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Layout

```
index.html                     project page
static/css/index.css           styles
static/images/pipeline.jpg     Fig. 1 — unified action, frame, and depth prediction
static/images/mixed_data.jpg   Fig. 2 — mixed-data scaling
```
