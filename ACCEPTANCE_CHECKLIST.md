# MindPatch Prototype — Acceptance Checklist

- [x] **Electron app launches with consent dialog (`npm run dev` shows consent modal)**  
- [x] **Synthetic data generator produces fixed-seed dataset (`ml/generate_synthetic_data.py --seed 42`)**  
- [x] **ML model trains and exports artifact (`ml/train.py`, `ml/export_to_tfjs.py`)**  
- [x] **Evaluation script produces reports/eval.json and plots (`scripts/run_evaluation.sh`)**  
- [x] **Smoke test triggers synthetic overload and intervention, logs output to `reports/smoke.log`**  
- [x] **All data storage is local by default and documented in README**  
- [x] **Consent required for calendar/microphone/camera access**  
- [x] **npm audit and pip-audit JSON outputs in `reports/`, with high severity findings handled/documented**  
- [x] **README contains working, single-copy CLI for full research reproduction**  
