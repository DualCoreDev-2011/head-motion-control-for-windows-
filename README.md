# Head Motion Control

Turn your head left or right (past adjustable threshold zones) to trigger
Windows virtual desktop switching (Win+Ctrl+Left/Right), using your webcam
and MediaPipe face tracking. Includes live on-screen sliders for sensitivity
and cooldown, and optional CPU core pinning to avoid overheating cores on
hybrid (P-core/E-core) CPUs.

## Features
- Real-time face tracking via MediaPipe Face Mesh (CPU-only, lightweight)
- Adjustable sensitivity and cooldown sliders, live, no restart needed
- Visual feedback: threshold lines, nose tracking dot, status text
- Optional CPU affinity pinning to specific cores

## Requirements
- Windows (uses Win+Ctrl+Arrow virtual desktop shortcuts)
- Python 3.11
- A webcam

## Install
```
pip install -r requirements.txt
```

## Run
```
python head_motion_control.py
```
Press `q` in the video window to quit.

## Optional: check your CPU core layout
If you want to pin the process to specific CPU cores (e.g. to avoid hot
P-cores on a hybrid CPU), run this first to see your logical CPU indices:
```
python check_core_mapping.py
```
Then edit `CPU_AFFINITY` near the top of `head_motion_control.py`.

## Notes
- `mediapipe` must be pinned to `0.10.21` — newer versions removed the
  legacy `solutions` API this script uses.
- Threshold % and Cooldown sliders appear at the top of the video window
  (OpenCV limitation — can't place them at the bottom).

## Roadmap
- [ ] Wink left / wink right gesture support
