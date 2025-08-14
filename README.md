## Gaze–Hand–Keypress Synergy Model

Predict keystrokes by combining eye-tracking and hand-tracking data.
This pipeline processes CSV logs from typing sessions, normalizes keyboard layouts, filters noisy gaze points, detects active fingers, and learns a gaze–hand synergy model to improve typing prediction for multimodal text entry, accessibility, and AR/VR input systems.

## Features

Reads and merges multiple CSV files containing gaze, hand, and keyboard data.

Builds per-keystroke events with:

Pre-press gaze window (anchor)

Pre-press hand position window (tail)

Normalizes keyboard layouts for consistent scaling across devices.

Filters gaze outliers using Median Absolute Deviation (MAD).

Detects the active finger before a keypress.

Learns a gaze–hand synergy model (mean & std of gaze–finger distances).

Scores candidate keys using:

Gaze likelihood

Language model priors (prefix/context)

Hand proximity weights

Directional bonuses

Synergy likelihood



Installation
git clone https://github.com/yourusername/gaze-hand-keypress-synergy.git
cd gaze-hand-keypress-synergy
pip install -r requirements.txt

Usage

Place CSV files in the input folder.

Ensure each CSV includes:

Gaze data: LeftGazeHitPosition_X, RightGazeHitPosition_Y, etc.

Fingertip data: Left_Hand_IndexTip_X, Right_Hand_IndexTip_Y, etc.

Keyboard coordinates: Key_A_X, Key_A_Y, etc.

Keystroke info: PressedLetter, CurrentLetter, ms timestamp.

Run:

python synergy_model.py

Example Output
Scanning CSVs under: .
Building events...
Events ready: 1436
Gaze-Hand Synergy Model learned: Mean=0.287, Std=0.091

Configuration

Adjust parameters at the top of synergy_model.py:

Window sizes: TAIL_MS, ANCHOR_MS

Gaze filtering: MAD_CUTOFF, MIN_GAZE_SAMPLES

Hand model: HAND_R_DEFAULT, STAGE1_HAND_R

Language model: LM_PREFIX_LAM, CONTEXT_BONUS


** Applications ** 

Gaze-assisted typing prediction

Accessibility input methods

AR/VR text entry optimization

Cognitive & HCI research
