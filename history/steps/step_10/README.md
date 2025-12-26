# Feedforward Neural Network Classifier

A PyTorch implementation demonstrating feedforward neural networks for multi-class classification on non-linearly separable data.

## Overview

This project implements a 2-layer feedforward neural network using PyTorch to solve multi-class classification problems that single-layer perceptrons cannot. It demonstrates how neural networks with hidden layers can learn non-linear decision boundaries to separate data that is not linearly separable.

### What It Does

The implementation:
- Generates a synthetic 3-class dataset in 2D space where no two classes are linearly separable
- Builds and trains a 2-layer feedforward neural network with configurable architecture
- Visualizes the learned decision boundaries
- Experiments with different hyperparameters to demonstrate their impact on learning

### Problem & Approach

**Problem:** Many real-world classification problems involve data that cannot be separated by a single linear boundary. While single-layer perceptrons are limited to linearly separable problems, feedforward neural networks with hidden layers can learn complex, non-linear decision boundaries.

**Approach:** This notebook demonstrates the power of feedforward neural networks by:
1. Creating synthetic data with non-linear class boundaries
2. Implementing a simple 2-layer architecture (input → hidden → output)
3. Training with backpropagation and visualizing the learning process
4. Comparing different hyperparameter configurations

## Tech Stack

- **Python 3.x** - Core programming language
- **PyTorch** - Deep learning framework for model building and training
- **Jupyter Notebook** - Interactive development environment
- **NumPy** - Numerical computations and data generation
- **Matplotlib** - Visualization of data and decision boundaries

## Repository Structure

```
feedforward-neural-network-notebook/
├── feedforward_neural_network.ipynb    # Main implementation notebook
├── requirements.txt                     # Python dependencies
└── README.md                            # This file
```

## Setup

### Prerequisites

- Python 3.7 or higher
- pip package manager

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Raminyazdani/feedforward-neural-network-notebook.git
cd feedforward-neural-network-notebook
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

Alternatively, install packages individually:
```bash
pip install torch numpy matplotlib jupyter
```

## How to Run

### Running the Notebook

1. Start Jupyter Notebook:
```bash
jupyter notebook feedforward_neural_network.ipynb
```

2. In the browser window that opens, run cells sequentially from top to bottom using `Shift + Enter`

### Expected Workflow

The notebook guides you through:
1. **Data Generation** - Creating synthetic 3-class dataset
2. **Data Visualization** - Plotting the non-linearly separable data
3. **DataLoader Implementation** - Setting up PyTorch data handling
4. **Model Architecture** - Building the 2-layer neural network
5. **Training** - Training the model and tracking metrics
6. **Decision Boundaries** - Visualizing what the network learned
7. **Experiments** - Testing different hyperparameters

## Data & Inputs

### Data Generation

The notebook **generates its own synthetic dataset**, so no external data files are required. The generated data consists of:
- **300 total points** (100 per class)
- **3 classes** in 2D space
- **Non-linear boundaries** between classes (spiral or circular patterns)

### Hyperparameters

You can configure the model through configuration dictionaries:
- `learning_rate` - Step size for gradient descent (e.g., 0.01, 0.001)
- `hidden_dim` - Number of neurons in the hidden layer (e.g., 10, 100)
- `epochs` - Number of training iterations (e.g., 1000)
- `batch_size` - Number of samples per training batch (e.g., 32)

## Outputs

The notebook produces:

1. **Visualizations:**
   - Initial data distribution plot (3 classes in 2D)
   - Decision boundary plots showing classification regions
   - Training progress (loss and accuracy over epochs)

2. **Training Metrics:**
   - Running loss per epoch
   - Classification accuracy per epoch
   - Final model performance

3. **Model Analysis:**
   - Comparison of different configurations
   - Observations on learning behavior (convergence, overfitting, underfitting)

## Reproducibility

### Random Seeds

The notebook sets random seeds for reproducibility:
```python
np.random.seed(352)
torch.manual_seed(0)
```

### Environment

- Tested with PyTorch 2.0+
- NumPy 1.21+
- Matplotlib 3.3+
- Works on CPU (no GPU required)

### Expected Results

With the default configuration, you should observe:
- Training accuracy improving from ~33% (random) to 80-90%
- Clear decision boundaries separating the three classes
- Different behaviors with different learning rates and hidden layer sizes

## Key Concepts Demonstrated

1. **Feedforward Architecture** - Data flows forward through layers
2. **Non-linear Activation** - ReLU enables learning of non-linear patterns
3. **Backpropagation** - Gradients flow backward to update weights
4. **Hyperparameter Impact** - How learning rate and architecture affect training
5. **Decision Boundaries** - Visualization of what the network learns

## Troubleshooting

### Import Errors
```bash
# If you get import errors, reinstall dependencies:
pip install --upgrade torch numpy matplotlib jupyter
```

### Training Issues
- **High loss/low accuracy**: Try increasing the hidden layer size or decreasing learning rate
- **Loss not decreasing**: Learning rate might be too low, try increasing it
- **Loss exploding**: Learning rate is too high, try decreasing it (e.g., 0.001)

### Memory Issues
- Reduce `batch_size` in the configuration
- The dataset is small (300 points), so this should rarely be an issue

### Notebook Won't Run
- Ensure Jupyter is installed: `pip install jupyter`
- Try running from the repository root directory
- Check that Python 3.7+ is being used: `python --version`

## Further Exploration

To extend this project, you could:
- Try different activation functions (Tanh, Sigmoid, Leaky ReLU)
- Add more hidden layers (deeper network)
- Test on real-world datasets (MNIST, Iris, etc.)
- Implement regularization techniques (dropout, L2)
- Add cross-validation for better performance evaluation

## License

This project is open source and available for educational purposes.

## Author

Ramin Yazdani - [GitHub](https://github.com/Raminyazdani)
