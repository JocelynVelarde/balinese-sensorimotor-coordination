# Balinese Sensorimotor Coordination: A Multimodal Synchrony Framework

[![MATLAB](https://img.shields.io/badge/MATLAB-R2023a%2B-blue.svg)](https://www.mathworks.com/products/matlab.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

Interpersonal coordination in Balinese Gamelan dance is sustained by a shared yet largely subjective state of attention that remains difficult to quantify using traditional observational methods. As standardized frameworks for capturing these complex, human-centered interactions remain rare, this repository introduces a **multimodal computational framework** for measuring creative coordination.

This project examines oculomotor and kinematic synchrony within a dancer dyad performing the *Wiwada Manik* narrative. By processing Mobile Electrooculography (EOG) and head-mounted Inertial Measurement Unit (IMU) data recorded in naturalistic performance environments, this code extracts precise biomechanical metrics to decode leader-follower dynamics, shared visual processing, and interlocking movement patterns.

---

## Repository Structure

```text
balinese-sensorimotor-coordination/
│
├── EOG_S12_Trial1.mlx      # MATLAB Live Script: EOG processing, blink removal, and saccade/fixation detection
├── EOG_S12_Trial1.pdf      # PDF export of the EOG analysis and visualizations
├── imu_cleaning_v2.mlx     # MATLAB Live Script: IMU (Gyro/Accel) filtering, alignment, and kinematic extraction
├── LICENSE                 # Repository license details
└── README.md               # Project documentation
```

---

## Methodology & Pipeline

The code in this repository implements a structured signal processing pipeline designed for high-velocity, real-world motion data.

### 1. Preprocessing

- **EOG:** Bandpass filtering (0.1–30 Hz) to remove baseline drift and high-frequency noise.
- **IMU:** High-pass filtering (0.1 Hz) of gyroscope and accelerometer signals.

### 2. Event Detection

- **Eyes:** Velocity-based thresholding (I-VT) to classify saccades and fixations; Z-score-based blink identification and removal.
- **Head/Body:** Extraction of 3-axis head kinematics (Yaw, Pitch, Roll) and overall movement intensity (accelerometer magnitude).

### 3. Synchrony Analysis

- Temporal alignment of synchronized `.h5` data streams.
- Cross-participant comparisons of event distributions to identify continuous mirroring vs. interlocking coordination (e.g., alternating phases of temporal alignment and antiphase movement).

---

## Getting Started

### Prerequisites

- MATLAB (Recommended R2023a or newer)
- Signal Processing Toolbox (required for `filtfilt`, `butter`, etc.)

### Data Format

The scripts are designed to ingest Mobile Brain-Body Imaging (MoBI) datasets formatted as `.h5` (HDF5) files. Expected data hierarchy:

| Path | Description |
|------|-------------|
| `/Sensor_ID/Time` | Microsecond timestamps |
| `/Sensor_ID/Calibrated/Gyroscopes` | Nx3 array |
| `/Sensor_ID/Calibrated/Accelerometers` | Nx3 array |

### Usage

1. Clone the repository:

```bash
git clone https://github.com/yourusername/balinese-sensorimotor-coordination.git
```

2. Open MATLAB and navigate to the repository folder.

3. Update the `h5_file` path variables in `imu_cleaning_v2.mlx` and `EOG_S12_Trial1.mlx` to point to your local dataset.

4. Run the Live Scripts (`.mlx`) section by section to visualize the raw vs. cleaned data, filtered quality checks, and dyadic comparative plots.

> **Note:** Replace `yourusername` in the `git clone` link above with your actual GitHub handle.

---

## Research Context & Citation

This repository contains the offline, biomechanical analysis code for a specific dyad (S5 & S6) derived from a broader MoBI/BCI study on Balinese Gamelan.

If you use this code or framework in your research, please consider citing the associated broader study:

> Aguilar-Herrera, A. J., et al. (2026). *An Artistic BCI-GenAI System Enabling Real-Time Co-Creation in Balinese Performance.* Association for the Advancement of Artificial Intelligence (AAAI).

---

## License

This project is licensed under the terms provided in the [LICENSE](./LICENSE) file.
