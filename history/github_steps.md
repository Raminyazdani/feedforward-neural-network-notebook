# Development History: Feedforward Neural Network Classifier

This document outlines the realistic development history of this project, showing how it evolved from initial concept to a complete implementation.

---

## History Expansion Note

**Step Expansion Summary:**
- **N_old:** 10 steps (from previous historian run)
- **N_new:** 15 steps (current expanded run)
- **Multiplier achieved:** 1.5× (exactly meets the minimum requirement)

**Expansion Strategy:**
This expanded history uses two key strategies to increase granularity while maintaining realism:

1. **Split Large Commits:** Broke down complex steps into smaller, focused commits
2. **Oops → Hotfix Sequence:** Inserted a realistic mistake and immediate fix (steps 8-9)

**Old Steps → New Steps Mapping:**

| Old Steps | New Steps | Description |
|-----------|-----------|-------------|
| Old step 1 | New steps 1-2 | Split: Initial setup (step 1) vs. Dependencies (step 2) |
| Old step 2 | New step 3 | Data generation - unchanged |
| Old step 3 | New step 4 | DataLoader - unchanged |
| Old step 4 | New steps 5-6 | Split: Network architecture (step 5) vs. Forward pass refinement (step 6) |
| Old step 5 | New steps 7-9 | Split into training loop basics (step 7), **OOPS: wrong optimizer config (step 8)**, **HOTFIX: correct optimizer (step 9)** |
| Old step 6 | New step 10 | Decision boundaries - unchanged |
| Old step 7 | New step 11 | Baseline experiment - unchanged |
| Old step 8 | New steps 12-13 | Split: config_1 experiment (step 12) vs. config_2 experiment (step 13) |
| Old step 9 | New step 14 | Documentation - unchanged |
| Old step 10 | New step 15 | Final polish - unchanged |

**Oops → Hotfix Details (Steps 8-9):**

**Step 8 (The Mistake):** While implementing metrics tracking, I accidentally set the learning rate parameter incorrectly in the optimizer initialization. Instead of using `lr=config['learning_rate']`, I hardcoded `lr=0.1`, which is too high for this problem and causes training instability.

**How I Noticed:** After running a quick test, the loss was exploding and the model wasn't learning. I checked the optimizer configuration and spotted the hardcoded value.

**Step 9 (The Fix):** Immediately corrected the optimizer initialization to properly use the configuration parameter: `optimizer = torch.optim.Adam(model.parameters(), lr=config['learning_rate'])`. This allows proper hyperparameter tuning in later experiments.

**Impact:** This is a realistic mistake - when copying code or refactoring, it's easy to miss configuration parameters. The immediate fix demonstrates good debugging practices and attention to training behavior.

---

## Development Timeline

### Step 1: Initial Repository Setup
**Date:** Day 1 (Morning)  
**Description:** Project initialization with basic structure

Created the foundational repository structure with README and .gitignore. This establishes the project identity and basic organization before any code.

**Key Files:**
- README.md (initial project description)
- .gitignore (Python/Jupyter ignores)

**Rationale:** Always start with project setup. A good README frames the work, and .gitignore prevents committing artifacts.

---

### Step 2: Dependencies and Environment
**Date:** Day 1 (Afternoon)  
**Description:** Added Python dependencies

Defined the project's dependencies in requirements.txt. This ensures reproducibility and makes it clear what packages are needed.

**Key Changes:**
- Created requirements.txt with core dependencies (torch, numpy, matplotlib, jupyter)

**Rationale:** Separate dependencies from initial setup. In real development, you might iterate on which versions or packages you need.

---

### Step 3: Data Generation and Visualization
**Date:** Day 2  
**Description:** Implemented synthetic data generation for non-linearly separable classes

Created the initial notebook with data generation. This is the foundation - we need to understand the problem before building a solution.

**Key Changes:**
- Created `feedforward_neural_network.ipynb`
- Added import statements (numpy, matplotlib, torch)
- Implemented `generate_data()` function for 3-class problem
- Added data visualization plot showing non-linear boundaries

**Rationale:** Start with data. Visualizing the 3-class non-linearly separable problem confirms why we need a multi-layer network.

---

### Step 4: PyTorch DataLoader Implementation
**Date:** Day 3  
**Description:** Created custom Dataset and DataLoader classes

Implemented PyTorch data handling infrastructure. This follows PyTorch best practices and makes training code cleaner.

**Key Changes:**
- Implemented `PointsDataset` class extending PyTorch Dataset
- Implemented `PointsDataLoader` class extending PyTorch DataLoader
- Added proper tensor conversions and data handling
- Tested batch processing

**Rationale:** Proper data handling is crucial. Using PyTorch's Dataset/DataLoader abstractions enables efficient batch processing and follows framework conventions.

---

### Step 5: Neural Network Architecture Definition
**Date:** Day 4  
**Description:** Designed 2-layer feedforward neural network class

Defined the FFNN class structure with PyTorch nn.Module. This establishes the model architecture.

**Key Changes:**
- Created `FFNN` class extending `nn.Module`
- Defined network layers: fc1 (input → hidden) and fc2 (hidden → output)
- Added `__init__` method with configurable dimensions
- Documented architecture decisions

**Rationale:** Define the architecture first. A 2-layer network with ReLU activation can learn non-linear boundaries.

---

### Step 6: Forward Pass Implementation
**Date:** Day 4 (continued)  
**Description:** Implemented forward pass with activation functions

Completed the forward pass logic with ReLU activation between layers.

**Key Changes:**
- Implemented `forward()` method
- Added ReLU activation after first layer
- Ensured proper tensor flow through network

**Rationale:** The forward pass is where the magic happens. ReLU introduces non-linearity, enabling the network to learn complex decision boundaries.

---

### Step 7: Training Loop Basic Structure
**Date:** Day 5  
**Description:** Implemented core training loop

Created the training function with the basic training loop structure, loss computation, and backpropagation.

**Key Changes:**
- Created `train()` function with epoch loop
- Added loss function (CrossEntropyLoss)
- Implemented backpropagation and parameter updates
- Added basic epoch iteration

**Rationale:** Get the core training mechanics working first. Loss, backward pass, and optimizer step are the fundamentals.

---

### Step 8: Add Metrics Tracking (OOPS - Wrong Optimizer Config)
**Date:** Day 5 (afternoon) ⚠️  
**Description:** Added metrics tracking but made a configuration mistake

Extended the training loop to track and log metrics per epoch. However, I accidentally hardcoded the learning rate in the optimizer instead of using the configuration parameter.

**Key Changes:**
- Added accuracy calculation per epoch
- Added training metrics logging
- Added optimizer initialization (but with **HARDCODED lr=0.1** instead of using config)
- Added progress printing

**The Bug:**
```python
# Wrong - hardcoded learning rate
optimizer = torch.optim.Adam(model.parameters(), lr=0.1)
```

**What Went Wrong:** When testing, the loss was exploding. The hardcoded 0.1 learning rate is too high for this problem, causing training instability.

**Rationale for the Mistake:** This is a common copy-paste error when refactoring - forgetting to parameterize hardcoded values.

---

### Step 9: Fix Optimizer Configuration (HOTFIX)
**Date:** Day 5 (late afternoon) ✅  
**Description:** Corrected optimizer to use configuration parameter

Immediately fixed the optimizer initialization to properly use the learning rate from the configuration dictionary.

**Key Changes:**
- Fixed optimizer initialization:
```python
# Correct - uses configuration
optimizer = torch.optim.Adam(model.parameters(), lr=config['learning_rate'])
```
- Verified training now works correctly with different learning rates

**How I Found It:** The loss was exploding during a quick test run. I checked the optimizer setup and spotted the hardcoded value.

**Rationale:** Good practice is to catch and fix bugs immediately. This bug would have prevented hyperparameter experiments in later steps.

---

### Step 10: Decision Boundary Visualization
**Date:** Day 6  
**Description:** Added visualization of learned decision boundaries

Implemented decision boundary plotting to visualize what the network learns. This is crucial for understanding the model's behavior.

**Key Changes:**
- Implemented `plot_decision_boundary()` function
- Created mesh grid for 2D space visualization
- Added color-coded classification regions
- Overlaid actual data points on boundaries

**Rationale:** Visualization is key to understanding. Decision boundaries show how the network separates classes in feature space.

---

### Step 11: Baseline Training Experiment
**Date:** Day 7  
**Description:** Ran initial training with baseline configuration

Conducted the first complete training experiment to establish a baseline performance.

**Key Changes:**
- Defined `config_0` with baseline hyperparameters
- Trained model and observed convergence
- Generated training plots (loss and accuracy over epochs)
- Visualized decision boundaries
- Documented baseline performance

**Rationale:** Always establish a baseline before experimentation. This provides a reference point for comparing configurations.

---

### Step 12: Hyperparameter Experiment - Config 1
**Date:** Day 8  
**Description:** Tested lower learning rate

Experimented with a lower learning rate to see the impact on training dynamics.

**Key Changes:**
- Created `config_1` with reduced learning rate
- Ran training experiment
- Observed slower but more stable convergence
- Documented findings

**Observations:** Lower learning rate leads to more stable training but takes longer to converge. Good for avoiding instability.

**Rationale:** Understanding how hyperparameters affect training is crucial for tuning models effectively.

---

### Step 13: Hyperparameter Experiment - Config 2  
**Date:** Day 9  
**Description:** Tested very high learning rate

Experimented with a much higher learning rate to demonstrate training failure.

**Key Changes:**
- Created `config_2` with very high learning rate
- Ran training experiment
- Observed training instability and poor convergence
- Documented failure patterns

**Observations:** Too high learning rate causes loss to oscillate or explode. The model fails to learn effectively.

**Rationale:** It's valuable to document what doesn't work. This demonstrates understanding of training dynamics and hyperparameter sensitivity.

---

### Step 14: Documentation and Analysis
**Date:** Day 10  
**Description:** Added comprehensive documentation and observations

Documented all observations, added analysis, and explained the learning patterns observed across experiments.

**Key Changes:**
- Added detailed observation cells with analysis
- Documented learning patterns and behaviors
- Explained overfitting vs underfitting scenarios
- Added interpretations for different configurations
- Improved markdown cell clarity

**Rationale:** A good notebook explains "why", not just "what". Documentation helps others understand the insights gained.

---

### Step 15: Final Polish and Professional Framing
**Date:** Day 11  
**Description:** Polished notebook for portfolio presentation

Transformed the working implementation into a portfolio-ready piece with professional presentation.

**Key Changes:**
- Updated notebook title to "Feedforward Neural Network Classifier"
- Cleaned up all section headers (removed exercise numbers)
- Enhanced README with comprehensive documentation
- Added setup instructions, troubleshooting guide
- Added reproducibility notes
- Verified all code runs correctly

**Rationale:** Transform working code into a portfolio piece. Clear documentation and professional presentation make the project accessible and impressive.

---

## Snapshot Structure

Each step directory (`step_01` through `step_15`) contains a complete snapshot of the repository at that point in time. This allows you to:
- See the project evolution chronologically
- Understand decision-making at each stage
- Learn from both successes and mistakes (see steps 8-9)
- Trace how features were built incrementally

## Key Insights from This Development Path

1. **Incremental Development:** Start simple, build iteratively, test frequently
2. **Mistakes Happen:** Even simple bugs (step 8) can cause major issues - fix them immediately
3. **Visualization Helps:** Decision boundaries and plots aid debugging and understanding
4. **Document as You Go:** Explain both what works and what doesn't
5. **Professional Polish Comes Last:** Get it working first, then make it portfolio-ready

## Realistic Development Patterns Demonstrated

This history reflects real development practices:
- **Not perfect on first try:** The optimizer bug (step 8) is a realistic mistake
- **Immediate fixes:** Step 9 shows good debugging practices
- **Experimentation:** Some configs work better than others (config_2 fails)
- **Iterative refinement:** Split complex tasks into smaller commits
- **Documentation in phases:** Technical comments first, comprehensive docs later
- **Professional polish is separate:** Don't polish while building (step 15)

---

**Total Development Time:** ~11 days (realistic for focused implementation)  
**Step Count:** 15 commits (increased granularity from original 10)  
**Lines of Code:** ~400-500 lines (appropriate scope for the problem)  
**Expansion Multiplier:** 1.5× (meets requirement exactly)
