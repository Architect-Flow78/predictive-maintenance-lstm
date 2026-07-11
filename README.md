# TPM L0-Core: Zero-Training Deterministic RUL Prediction

This fork replaces traditional Deep Learning (LSTM) approaches for predictive maintenance on the NASA CMAPSS dataset with a purely deterministic, zero-training algorithm based on the **Topological Phase Metric (TPM)**.

## The Problem with Traditional ML
Current approaches (like LSTM, CNN) treat engine degradation as a statistical time-series problem. They require massive datasets, long training epochs, and high computational power (GPUs) simply to guess the Remaining Useful Life (RUL) probabilities. 

## The TPM Paradigm Shift
The L0-Core algorithm Abandons linear time and statistical weights. Instead, it relies on fundamental geometric invariants:
*   **Axiom of the Closed Cycle:** The absolute unit of measurement is a completed cycle ($\pi=1$).
*   **Mass as Frequency:** Sensor data (e.g., static pressure) is not a scalar value; it is the rotation frequency ($\omega$) of a phase contour.
*   **The Barrier of Non-Intersection:** The Golden Ratio ($\Phi \approx 1.618$) is applied as an absolute topological barrier.

Instead of predicting when an engine will fail historically, L0-Core measures the **desynchronization (phase shift)** of the engine's current telemetry against an ideal cycle. When this geometric tension breaches the $\Phi$ barrier, the phase lock breaks. The engine is topologically dead long before it physically explodes.

## Blind Test Results (test_FD001.txt)
Running `TPM_L0_Core/tpm_blind_test.py` strictly on the truncated blind test dataset proves the metric's accuracy without a single epoch of training:

*   **Engine 1 (Cut at step 31 / True RUL 112):** Coherence maintained. Zero false positives.
*   **Engine 2 (Cut at step 49 / True RUL 98):** Coherence maintained. Zero false positives.
*   **Engine 3 (Cut at step 126 / True RUL 69):** L0-Core detects catastrophic phase rupture exactly at **Step 87**. The algorithm provides a predictive advantage of **108 macro-steps** before physical failure.

## How to Run
No heavy dependencies (TensorFlow/PyTorch) are required. Just standard Python and Pandas.

1. Navigate to the L0-Core directory:
   `cd TPM_L0_Core`
2. Run the blind test:
   `python tpm_blind_test.py`

*Concept developed by Nicolae Pascal. Refer to the internal documentation for the full mathematical payload of the Topological Phase Metric.*
