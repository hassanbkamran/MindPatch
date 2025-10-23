# MindPatch – Adaptive Context-aware Micro-Recovery System for Developers

A privacy-first, on-device research prototype that detects cognitive overload micro-bursts in software developers using context signals (keyboard, mouse, window, IDE, system), triggering adaptive micro-recovery interventions, and collecting reproducible evaluation logs.

## ✨ Project Goals

- Collect rich developer context signals on-device
- Run local ML inference for overloaded states (sub-minute timescale)
- Deliver minimal, adaptive interventions within user constraints
- Log predictions, feedback, and ground truth for reproducible evaluation
- Privacy-by-default: no data leaves device without explicit opt-in

---

## 🏁 Quick-Start (Copy-paste all for full reproduction)

```bash
git clone https://github.com/YOUR_USER/mindpatch.git
cd mindpatch

# Setup frontend/backend
npm install

# Start Electron app (shows consent dialog on first run)
npm run dev

# (In a separate terminal) Generate reproducible synthetic data for ML
python3 -m venv .venv
source .venv/bin/activate
pip install -r ml/requirements.txt
python ml/generate_synthetic_data.py --seed 42 --out data/simulated_seed42.csv

# Train ML model and export for on-device TF.js inference
python ml/train.py --data data/simulated_seed42.csv --out models/mindpatch_tfjs
python ml/export_to_tfjs.py --model models/mindpatch.pth --out models/mindpatch_tfjs/

# Evaluate trained model
bash scripts/run_evaluation.sh

# Smoke test (simulate overload events, verify intervention triggers)
bash scripts/smoke_test.sh

# [Security checks]
npm audit --json > reports/security-audit.json
pip-audit --format=json > reports/python-security-audit.json
