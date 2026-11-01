# AI Emotion & Mood Detector

Real-time facial emotion recognition that runs 100% in the browser (no backend, no install, no video upload).

## Run

```bash
cd /Users/dwipilahare/Downloads/denish
python3 -m http.server 8000
```

Open http://localhost:8000 in Chrome/Edge, click **Start Camera**, and allow access.
(Internet is needed on first load to fetch the library and ~1 MB of models from a CDN.)

## How it works

1. **Face detection** – `TinyFaceDetector` (face-api.js / TensorFlow.js) finds the face in each frame.
2. **Emotion classification** – `FaceExpressionNet` outputs probabilities for 7 emotions: happy, neutral, sad, angry, surprise, fear, disgust.
3. **Smoothing** – an exponential moving average removes flicker between frames.
4. **Mood score** – probabilities are weighted by valence (happy = 1, neutral = 0.5, sad/angry = 0 …) to give a 0–100 % positivity score → Positive / Neutral / Low mood, plotted in the trend chart.

## Files

- `index.html` – the whole app (UI, detection loop, chart).

## Limitation

Detects emotions from facial expressions only, not true feelings. Accuracy depends on lighting and face angle.
