# MEDIC — Voice-to-PCR EMS Documentation Assistant

## Overview

MEDIC is a fully local, privacy-first AI documentation assistant built for Emergency Medical Services that converts paramedic speech into structured Pre-hospital Care Reports (PCRs) in real-time. Paramedics spend significant time on manual PCR documentation after emergency calls by pulling focus away from patient care and creating HIPAA compliance risks when cloud-based tools are used. MEDIC solves both problems by running the entire pipeline on-device, with zero PHI ever leaving the device.

The system was fine-tuned on synthetic EMS transcripts grounded in 60M national EMS activations from the NEMSIS v3.5 2024 dataset, covering all 53 US states and territories by making it the first prehospital documentation assistant trained on nationally representative EMS distributions.

## How It Works

The pipeline runs entirely locally from wake word to PCR export:

- "Hey MEDIC" triggers via wake word detection, clinical audio never touches the cloud
- Whisper ASR transcribes paramedic speech locally on-device
- A fine-tuned T5-base model extracts 23 structured NEMSIS clinical fields from the transcript
- A vitals validation layer rejects physiologically impossible values before they enter the PCR
- A gap detection engine identifies missing mandatory and required fields
- Llama 3.1 8B via Ollama handles gap completion and voice corrections entirely on-device
- Real-time updates are pushed to a React 19 web dashboard and companion React Native mobile app via WebSocket

## Results

Three research hypotheses were validated on 239 held-out test samples:

**H1 — Accuracy**

| Metric | Fine-tuned T5 | Llama 3.1 8B Zero-Shot |
|---|---|---|
| Scalar Exact Match | 83.9% | 72.4% |
| Array F1 | 88.6% | 54.7% |
| **Combined F1** | **86.2%** | **63.6%** |

T5 outperforms the LLM baseline by 22.6 percentage points.

**H2 — Hallucination**

| Model | Hallucination Rate |
|---|---|
| Fine-tuned T5 | 0.8% (37 / 4,456 fields) |
| LLM Baseline | 3.0% (128 / 4,216 fields) |

T5 hallucinates 3.75x less than the LLM baseline.

**H3 — Completeness**

Gap detection reduced average mandatory missing fields to 0.00 across all sessions, recovering data in 47.7% of single-pass extractions.

**Latency:** T5 inference at ~4.5s vs ~25.3s for Llama 3.1 8B — 5.6x faster for real-time clinical use.

## Key Findings

- Fine-tuned T5 dramatically outperforms a much larger zero-shot LLM on structured clinical extraction by showing that task-specific fine-tuning beats raw model size for constrained output formats
- Vitals fields (BP, HR, SpO2, GCS) achieve 97–100% exact match, where the most safety-critical fields are the most reliable
- Primary impression remains the hardest field at 63.6% with complex clinical labels that require inference beyond what was explicitly stated
- Two-phase gap completion (deterministic rules + LLM recovery) eliminates mandatory missing fields entirely across all test sessions

## Accessing the Full Code

The complete source code, training pipeline, evaluation scripts, and setup instructions are available in the private repository.

Feel free to reach out for access for interviews, collaboration, or evaluation purposes.

- **Email:** ksheerooo@gmail.com
- **LinkedIn:** [linkedin.com/in/ksheerajprakash](https://linkedin.com/in/ksheerajprakash)

🔗 GitHub Repository (private): [https://github.com/KsheerajP/Voice-to-PCR-Assistant-for-EMS.git](https://github.com/KsheerajP/Voice-to-PCR-Assistant-for-EMS.git)
