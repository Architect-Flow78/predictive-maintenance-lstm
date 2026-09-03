# predictive-maintenance-lstm
# TPM L0-Core: Zero-Training Deterministic RUL Prediction

## Overview
Determining the time available before a likely failure and being able to predict failures can help businesses better plan the use of their equipment, reduce operation costs, and avert issues before they become significant or catastrophic. The goal of predictive maintenance (PdM) is to allow for corrective actions and prevent unexpected equipment failure.

This fork replaces traditional Deep Learning (LSTM) approaches for predictive maintenance on the NASA CMAPSS dataset with a purely deterministic, zero-training algorithm based on the **Topological Phase Metric (TPM)**. 

This project is a continuation of the work began as my project [Spark ML](https://github.com/sabderra/predictive-maintenance-spark) for CSCI-E63 where Spark and Kafka were used to build an end-to-end workflow for predicting the Remaining Useful Life (RUL) of simulated turbofan engine data.

## The Problem with Traditional ML
Current approaches (like LSTM, CNN) treat engine degradation as a statistical time-series problem. They require massive datasets, long training epochs, and high computational power (GPUs) simply to guess the Remaining Useful Life (RUL) probabilities. 

## The TPM Paradigm Shift
The L0-Core algorithm abandons linear time and statistical weights. Instead, it relies on fundamental geometric invariants:
*   **Axiom of the Closed Cycle:** The absolute unit of measurement is a completed cycle ($\pi=1$).
*   **Mass as Frequency:** Sensor data (e.g., static pressure) is not a scalar value; it is the rotation frequency ($\omega$) of a phase contour.
*   **The Barrier of Non-Intersection:** The Golden Ratio ($\Phi \approx 1.618$) is applied as an absolute topological barrier.

Instead of predicting when an engine will fail historically, L0-Core measures the **desynchronization (phase shift)** of the engine's current telemetry against an ideal cycle. When this geometric tension breaches the $\Phi$ barrier, the phase lock breaks. The engine is topologically dead long before it physically explodes.

### Zero-Parameter Constants
Unlike ML models that calibrate hyperparameters to the test set, TPM uses absolute universal limits:
1. **Fractal Phase Depth = 137.082**: The absolute topological capacity of 3D space (Icosahedron domains multiplied by Toroidal dead-zone thickness, $20 \times \Phi^4$).
2. **Critical Dimensional Tension = 5.0**: The absolute dimensional tension limit before spatial coherence collapses in 3D ($T(3) = 5$).

## Installing Dependencies
No heavy dependencies (TensorFlow/PyTorch) are required. Just standard Python and Pandas.
```bash
pip install pandas numpy
