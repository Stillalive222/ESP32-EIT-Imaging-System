# ESP32-EIT-Imaging-System

## Overview

Electrical Impedance Tomography (EIT) is a non-invasive imaging technique that reconstructs the internal conductivity distribution of an object using boundary voltage measurements.

This project implements a complete low-cost 16-electrode EIT system using an ESP32-S3 microcontroller, custom analog front-end circuitry, multiplexed electrode switching, and image reconstruction using the PyEIT framework.

The objective was to develop an affordable and educational EIT platform capable of detecting conductivity anomalies inside a conductive medium.

---

## Key Features

* 16-electrode EIT acquisition system
* ESP32-S3 based controller
* 50 kHz excitation signal generation
* Howland Current Pump for constant current injection
* AD620 instrumentation amplifier based sensing
* ADS1115 16-bit ADC acquisition
* CD74HC4067 electrode multiplexing
* UART communication with host PC
* PyEIT image reconstruction
* Adjacent-drive adjacent-measure protocol
* 208 measurements per frame

---

## System Architecture

The system consists of five major stages:

1. Signal Generation
2. Constant Current Injection
3. Electrode Switching Network
4. Voltage Measurement and Conditioning
5. Image Reconstruction

Current is injected through selected electrode pairs while voltage measurements are collected from neighboring electrode combinations. The collected data is transmitted to a PC where conductivity maps are reconstructed using Electrical Impedance Tomography algorithms.

---

## Hardware Components

| Component           | Function                     |
| ------------------- | ---------------------------- |
| ESP32-S3            | Main controller              |
| ADS1115             | 16-bit ADC                   |
| AD620               | Instrumentation amplifier    |
| NE5532              | Oscillator and analog stages |
| CD74HC4067          | Electrode switching          |
| Aluminum Electrodes | Boundary sensing             |
| Water Phantom       | Conductive medium            |

---

## Experimental Setup

### Complete EIT Hardware Setup

![Complete Setup](images/setup.jpg)

The complete prototype consists of the analog front-end, multiplexing network, ESP32-S3 controller, ADC module, and the 16-electrode phantom used for data acquisition.

---

## Results

### Two-Anomaly Phantom Configuration

![Two Anomalies](images/two_anomaly_phantom.jpg)

Two low-conductivity objects were inserted into the water-filled phantom to evaluate anomaly localization performance.

### Reconstructed Conductivity Distribution

![Reconstruction Result](images/reconstruction_result.jpg)

The reconstructed conductivity map generated using the PyEIT Back Projection algorithm successfully identifies the locations of the inserted anomalies.

---

## Measurement Protocol

The system follows the adjacent-drive adjacent-measure strategy.

For each acquisition cycle:

* 16 current injection pairs
* 13 voltage measurements per injection pair
* Total measurements per frame: 208

The resulting dataset is transmitted to the host computer through UART for reconstruction.

---

## Software Stack

### Firmware

* Arduino Framework
* ESP32-S3

### Host Software

* Python 3
* PyEIT
* NumPy
* PyQt5
* PyQtGraph
* Matplotlib

---

## Getting Started

### Clone Repository

```bash
git clone https://github.com/Stillalive222/ESP32-EIT-Imaging-System.git
cd ESP32-EIT-Imaging-System
```

### Install Python Dependencies

```bash
pip install -r requirements.txt
```

### Upload Firmware

Open the firmware folder in Arduino IDE and upload the sketch to the ESP32-S3 board.

### Run Reconstruction Software

```bash
python gui.py
```

---

## Future Improvements

* Real-time imaging
* Faster reconstruction algorithms
* Multi-frequency EIT
* Improved electrode materials
* Wireless data acquisition
* 3D conductivity reconstruction

---

## Applications

* Biomedical imaging
* Lung monitoring research
* Industrial process tomography
* Material characterization
* Educational instrumentation platforms

---

## Project Report

The complete project report is available in the `report/` directory.

---

## Acknowledgements

This project was inspired by the open-source Electrical Impedance Tomography work available at:

https://github.com/RonAaron61/EIT-Microcontroller

The hardware implementation, ESP32-S3 integration, analog front-end design, measurement circuitry, firmware development, experimental setup, and testing methodology presented in this repository were independently developed for this project.

---

## Authors

### Anmol Kumar

B.Tech Electrical Engineering
Indian Institute of Technology Mandi

### Subham Jaiswal

B.Tech Electrical Engineering
Indian Institute of Technology Mandi

---

## License

This project is released under the MIT License.
