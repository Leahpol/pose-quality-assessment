# Dance Quality Assessment — Intern Take-Home Assignment

**Time limit:** 2 days (expect ~8–12 hours of focused work)

## Objective

Build a pipeline that takes a **1-minute dance video** as input and outputs a **numeric quality score (0–100)** along with per-dimension sub-scores. You choose the dance video — find or record any ~60 second clip of a person dancing.

This assignment tests your ability to **ship working computer-vision code quickly**, not to build a perfect system.

---

## What You Must Deliver

| Deliverable | Format |
|---|---|
| Working pipeline | A single Jupyter notebook **`solution.ipynb`** |
| Sample output | The notebook must run end-to-end on your chosen video and print results |
| Brief write-up | Markdown cells inside the notebook (no separate doc) |

### Pipeline Requirements

Your pipeline must extract **at least 3** of the following quality dimensions from the video. You decide which ones and how to weight them.

| Dimension | What to measure | Hints |
|---|---|---|
| **Rhythm alignment** | How well the dancer's movements sync to the audio beat | Beat detection (librosa) + movement peaks |
| **Pose stability** | Smoothness and control — absence of jitter/wobble | Keypoint variance over sliding windows |
| **Symmetry** | Left-right body symmetry during symmetric moves | Compare mirrored keypoint distances |
| **Range of motion** | How fully the dancer uses joint range | Joint angle distributions |
| **Timing consistency** | Regularity of repeated movements | Autocorrelation of keypoint trajectories |
| **Spatial coverage** | Use of the performance space | Convex hull of center-of-mass trajectory |

### Minimum Technical Requirements

1. **Pose estimation** — Use any off-the-shelf model (MediaPipe, OpenPose, MMPose, etc.) to extract body keypoints frame-by-frame.
2. **Signal processing** — Convert raw keypoints into at least one meaningful time-series signal and analyze it.
3. **Scoring function** — Produce a final 0–100 score with a clear, documented formula.
4. **Visualization** — Include at least 2 plots (e.g., keypoint overlay on frames, signal over time, score breakdown bar chart).

---

## Starter Code

Open **`solution.ipynb`** — it contains a skeleton with section headers and helper utilities. You are free to restructure it, but your final submission must remain a single notebook.

## Getting Started

```bash
# 1. Create a virtual environment
python -m venv venv && source venv/bin/activate

# 2. Install dependencies
pip install -r requirements.txt

# 3. Place your dance video
#    Save a ~60s dance video as  dance-quality-assessment/data/dance_video.mp4
#    (or update the VIDEO_PATH in the notebook)

# 4. Open the notebook
jupyter notebook solution.ipynb
```

---

## Evaluation Rubric (see `RUBRIC.md` for full details)

| Criteria | Weight |
|---|---|
| **Works end-to-end** — runs without errors, produces a score | 30% |
| **Technical depth** — quality of CV / signal processing approach | 25% |
| **Code quality** — readable, modular, minimal unnecessary complexity | 20% |
| **Justification** — explains design choices and metric rationale | 15% |
| **Creativity / extensions** — goes beyond the minimum in a useful way | 10% |

---

## Rules

- You may use any open-source library.
- You may use LLMs for research and debugging but **write the core logic yourself** — be prepared to explain every line in a follow-up call.
- Do **not** train a model from scratch; use pretrained models for pose estimation.
- If you get stuck, document what you tried and move on. Shipping something imperfect beats shipping nothing.

## Submission

1. Ensure `solution.ipynb` runs top-to-bottom with `Restart & Run All`.
2. Commit your notebook (and the video if < 25 MB, otherwise provide a download link).
3. Push to your fork or email a zip.

Good luck — we're excited to see what you build!
