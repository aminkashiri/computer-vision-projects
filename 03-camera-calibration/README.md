# Camera Calibration

`calibrate.py` calibrates a camera from 20 photos of a checkerboard (9×6 inner corners, 22 mm squares) with Zhang's method in OpenCV: `findChessboardCorners`, sub-pixel refinement with `cornerSubPix`, then `calibrateCamera`. To check how stable the estimate is, it runs on four subsets of the photos:

| Photos | $f_x$ | $f_y$ | $p_x$ | $p_y$ |
|---|---|---|---|---|
| 1–10 | 2931.77 | 2952.69 | 911.52 | 551.57 |
| 6–15 | 3002.05 | 2997.90 | 881.61 | 528.45 |
| 11–20 | 3046.20 | 3034.88 | 718.35 | 548.59 |
| 1–20 | 2982.49 | 2990.48 | 836.99 | 512.82 |

The focal length changes by a few percent between subsets, while the principal point moves by up to ~190 px. Fixing the principal point at the image center with square pixels and zero skew (the commented-out call in `calibrate.py`) gives $f \approx 3005$ px.

## Run

The checkerboard photos are not in the repo. Put them in `inputs/` as `im01.jpg` … `im20.jpg`.

```bash
pip install -r requirements.txt
python calibrate.py
```
