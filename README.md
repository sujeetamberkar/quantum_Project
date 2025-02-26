# Quantum-Enhanced CNN for Image Classification

This project demonstrates how quantum computing can enhance machine learning models, specifically Convolutional Neural Networks (CNNs), for image classification tasks. The repository explores two approaches to solving binary classification problems using the CIFAR-10 dataset:

1. **Classical CNN**: A traditional shallow CNN architecture
2. **Quantum-Hybrid CNN**: A CNN where one classical neural network layer is replaced with a quantum circuit

## Project Motivation

Traditional shallow CNNs may struggle with certain classification tasks. This project investigates whether replacing a classical layer with a quantum layer can improve classification performance. The hypothesis is that quantum computing's unique processing capabilities might capture different patterns or relationships in the data.

## Results

As shown in the `CompareTestAccuracy.xlsx` file, the Quantum-Hybrid model demonstrates equal or improved accuracy in the majority of binary classification combinations tested on the CIFAR-10 dataset. The color-coded spreadsheet highlights where quantum enhancement provided the most significant improvements.

## Dataset

The CIFAR-10 dataset consists of 60,000 32x32 color images in 10 classes:
- Airplane
- Automobile
- Bird
- Cat
- Deer
- Dog
- Frog
- Horse
- Ship
- Truck

For this experiment, we transformed the images to grayscale and applied data augmentation techniques.

## Model Architectures

### Classical CNN Architecture
```
- Conv2D Layer (1→2 channels, 5×5 kernel)
- ReLU Activation + Max Pooling
- Conv2D Layer (2→16 channels, 5×5 kernel)
- ReLU Activation + Max Pooling
- Dropout
- Flatten
- Fully Connected Layer (400→64)
- Fully Connected Layer (64→2)
- Fully Connected Layer (2→1)
- Fully Connected Layer (1→2)
- Log Softmax
```

### Quantum-Hybrid CNN Architecture
```
- Conv2D Layer (1→2 channels, 5×5 kernel)
- ReLU Activation + Max Pooling
- Conv2D Layer (2→16 channels, 5×5 kernel)
- ReLU Activation + Max Pooling
- Dropout
- Flatten
- Fully Connected Layer (400→64)
- Fully Connected Layer (64→2)
- Quantum Layer (2-qubit quantum circuit with ZZFeatureMap and RealAmplitudes)
- Fully Connected Layer (1→1)
- Probability Output [p, 1-p]
```

## Quantum Circuit Details

The quantum part of the hybrid model uses:
- 2-qubit quantum circuit
- ZZFeatureMap for data encoding
- RealAmplitudes for trainable parameters
- Qiskit's TorchConnector to integrate with PyTorch

## Requirements

To run this code, you'll need:

```
# Core PyTorch and vision libraries
torch>=2.0.0
torchvision>=0.15.0

# Qiskit for quantum computing
qiskit>=0.43.0
qiskit-machine-learning>=0.6.0

# Visualization and model summary
torchinfo>=1.8.0

# Machine learning utilities
scikit-learn>=1.2.0

# Data handling
numpy>=1.22.0
pandas>=2.0.0
```

## Installation

```bash
# Clone the repository
git clone https://github.com/sujeetamberkar/quantum_Project.git
cd quantum_Project

# Create a virtual environment
python -m venv quantum_env
source quantum_env/bin/activate  # On Windows: quantum_env\Scripts\activate

# Install dependencies
pip install -r Requirements.txt
```

## Usage

Two Jupyter notebooks are provided:
- `classical.ipynb`: Contains the classical CNN implementation
- `q_suj.ipynb`: Contains the quantum-hybrid CNN implementation

You can also find the classification reports for all binary classification combinations in:
- `100_CNNClassificationreport.md`: For the classical model
- `100_qCNNClassificationreport.md`: For the quantum-hybrid model

## Conclusion

This project demonstrates that integrating quantum computing elements into traditional CNN architectures can provide performance improvements for certain classification tasks, suggesting promising avenues for further exploration of quantum-enhanced machine learning.