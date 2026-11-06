# VideoMemBench Viewer

Case-by-case web viewer for [VideoMemBench](https://videomembench.github.io/) ("VideoMemBench: How Well Do MLLMs Remember in Video Conversations?", [arXiv 2610.40131](https://arxiv.org/abs/2610.40131)) — ships with a 6-video representative subset and their complete dialogues.

**Live site:** https://jxb1st.github.io/videomembench-viewer/

## The benchmark

In-context video memory: each sample pairs one video with a multi-turn dialogue in which later questions depend on earlier turns. An *episodic* dependency refers back to a scene, object or event discussed earlier (what the model has seen); an *answer* dependency builds on the model's own earlier answer (what it has said). 326 videos, 2,476 turns, 1,387 of them dependent. Models are evaluated with 128 uniformly sampled timestamped frames and sequential self-rollout (their own previous responses stay in the history). Metrics: TurnAcc, EpiDepAcc, AnsDepAcc (a turn counts only if its whole answer-ancestor chain is correct) and their mean, Overall. Best reported model: Claude Opus 5 at 45.7 Overall.

## Contents

- `index.html` — single-file viewer: video, dialogue in evaluation order with dependency badges (click to highlight the parent turn), multiple-choice options, gold answers (toggle), raw JSON
- `data/samples.json` — the subset's annotations (verbatim rows of the official `annotations.jsonl`, plus `duration_s`)
- `videos/<video_name>` — re-encoded 480p H.264 (CRF 28, no audio, faststart); the official evaluation never uses the video file directly, only 128 fixed frames
- `full_dataset_stats.json` — statistics of the full benchmark computed from `annotations.jsonl`, and the official leaderboard rows
- `selection_report.md` — which videos were picked and why

## Full benchmark

Data: [VideoMemBench/data on Hugging Face](https://huggingface.co/datasets/VideoMemBench/data) (annotations CC BY-NC-SA 4.0, non-commercial research and evaluation only; source videos keep their original rights). Code: [GitHub](https://github.com/Oliiveralien/VideoMemBench). Project page: https://videomembench.github.io/.
