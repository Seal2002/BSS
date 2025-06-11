Overview
This repository contains the implementation of a Mono-Aural Blind Source Separation (BSS) framework for separating bioacoustic sources from non-biological ocean soundscape signals. Our hybrid approach combines classical signal processing techniques with modern deep learning to achieve efficient and accurate marine bioacoustic monitoring.
Key Features

🎯 94.87% Classification Accuracy on balanced bioacoustic dataset
⚡ 80% Lower Inference Cost compared to U-Net based models
🔊 Robust SNR Performance - maintains >89% accuracy at 5 dB SNR
🐋 Real-time Deployment Ready with lightweight MLP architecture
📊 Comprehensive Evaluation with extensive ablation studies

Methodology
Our pipeline integrates four state-of-the-art approaches:

BioCPPNet (Bermant et al.) - Deep neural network insights
NMF-MMSE (Zaheer et al.) - Denoising techniques
Conv-TasNet/Demucs (Mancusi et al.) - Fish vocalization separation
Hybrid NMF-FastICA (Li et al.) - Matrix factorization approaches

Architecture
The system consists of four main stages:

Data Acquisition - Curated marine soundscape dataset
Preprocessing Pipeline - Format conversion, resampling, standardization
Feature Extraction - Mel spectrogram generation with NMF dimensionality reduction
Classification - Lightweight MLP for biological/non-biological classification

Show Image
Repository Structure
BSS-Bioacoustic-Monitoring/
├── README.md                           # This file
├── BSS Arch.pdf                        # System architecture diagram
├── BSS research paper - SDP.pdf        # Complete research paper
├── Detailed project plan.pdf           # Project methodology and timeline
├── Preprocessing Pipeline Overview.pdf  # Preprocessing workflow details
├── model.ipynb                         # Main implementation notebook
├── requirements.txt                    # Python dependencies
├── data/                              # Dataset directory (not included)
└── results/                           # Output visualizations and metrics
Installation
Prerequisites

Python 3.8 or higher
NVIDIA GPU (recommended for training)
CUDA toolkit (if using GPU)

Setup

Clone the repository
bashgit clone 
cd BSS-Bioacoustic-Monitoring

Create virtual environment
bashpython -m venv bss_env
source bss_env/bin/activate  # On Windows: bss_env\Scripts\activate



Required Libraries

torch - PyTorch framework
librosa - Audio processing library
numpy - Numerical computing
pandas - Data manipulation
matplotlib - Visualization
scikit-learn - Machine learning utilities
pydub - Audio format conversion
jupyter - Notebook environment

Dataset
Our dataset consists of 10,000 balanced audio clips (10 seconds each, 22.05 kHz):

5,000 Bioacoustic clips: Marine mammal and fish vocalizations
5,000 Non-biological clips: Ship engines, wave noise, rain

Data Sources:

Lombard Marine Sound Library
Publicly available ship-noise archives

Note: Dataset not included in repository due to size constraints. Contact authors for access.
Usage
Quick Start

Open the main notebook
bashjupyter notebook model.ipynb

Run the preprocessing pipeline

Execute data loading and preprocessing cells
Generate Mel spectrograms from audio clips


Train the model

Configure hyperparameters (see paper for optimal settings)
Run training loop with validation monitoring


Evaluate performance

Generate confusion matrices and performance metrics
Analyze SNR robustness curves



Model Parameters
ParameterValueBatch Size32Epochs50Learning Rate1e-3NMF Components50Hidden Layer 132 neuronsHidden Layer 216 neuronsOptimizerAdamSchedulerReduceLROnPlateau
Results
Performance Comparison
MethodAccuracy (%)F1-Score (%)AUCInference Time (ms)NMF-MMSE89.588.70.9212.3NMF-FastICA90.890.10.9415.6Conv-TasNet94.093.50.97102.4BioCPPNet96.596.00.99158.7Ours94.8794.750.9822.4
Key Achievements

✅ Near state-of-the-art accuracy with significantly lower computational cost
✅ Robust performance across various SNR conditions (5-30 dB)
✅ Real-time inference capability for marine monitoring applications
✅ Interpretable feature extraction through NMF decomposition

Documentation
Detailed documentation is available in the repository:

Research Paper - Complete methodology and experimental results
Architecture Diagram - Visual system overview
Project Plan - Development methodology and timeline
Preprocessing Details - Signal processing workflow

Future Work

🔄 Temporal Modeling: Integrate RNN/Transformer layers for enhanced temporal pattern recognition
🎛️ Data Augmentation: Implement noise injection and time-stretching for improved robustness
📱 Edge Deployment: Optimize for low-power hardware deployment in autonomous marine platforms
🌊 Multi-class Classification: Extend to species-specific bioacoustic identification
