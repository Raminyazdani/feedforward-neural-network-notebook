# Portfolio Refactoring Report

**Project:** feedforward-neural-network-notebook  
**Date Started:** 2025-12-26  
**Status:** In Progress

---

## Phase 0: Initial Setup

### Repository Analysis
- **Repository Structure:** Single Jupyter notebook project with minimal structure
- **Main Files:**
  - `FFNN_(1).ipynb` - Main notebook (748 lines, ~231KB)
  - `README.md` - Contains assignment language
  - `requirements.txt` - Python dependencies (torch, numpy, matplotlib, jupyter)
  - `.github/copilot-instructions.md` - Existing Copilot guidance

### Initial Observations
1. **Assignment Traces:** README explicitly mentions "Assignment 6" and "NNTI course"
2. **Notebook Title:** Contains "Exercise 5.4" and point values throughout
3. **Naming Issues:** Notebook filename has parentheses `FFNN_(1).ipynb` - not professional
4. **Folder Reference:** README mentions non-existent folder "Submission_6_-_7072982_Syed_Rumman_Ali"
5. **No Absolute Paths:** Quick scan shows no hardcoded absolute paths
6. **Self-Contained:** All data generation is in the notebook itself

### Files Created (Phase 0)
- `report.md` (this file)
- `suggestion.txt` (tracking file for discovered issues)
- `suggestions_done.txt` (tracking file for applied changes)
- `project_identity.md` (professional identity definition)

---

## Phase 1: Project Identity & Naming Plan

### Professional Identity Defined
Created `project_identity.md` with the following professional framing:
- **Display Title:** Feedforward Neural Network Classifier
- **Slug:** feedforward-neural-network-notebook (current repo name is already good!)
- **Tagline:** PyTorch implementation demonstrating FFNNs for multi-class classification on non-linearly separable data
- **Key Features:** Self-contained notebook with synthetic data generation, decision boundary visualization, hyperparameter experiments

### Naming Alignment Analysis

#### Current State
- Repo name: `feedforward-neural-network-notebook` ✓ (already professional)
- Main notebook: `FFNN_(1).ipynb` ✗ (has parentheses, unclear numbering)
- README: Contains assignment language ✗

#### Proposed Naming Changes
1. **Notebook File Rename:**
   - FROM: `FFNN_(1).ipynb`
   - TO: `feedforward_neural_network.ipynb`
   - RATIONALE: Remove parentheses, more descriptive, professional naming
   - IMPACT: No internal references to check (notebooks don't import themselves)

2. **No Folder Renames:** Repository is already flat and appropriate

3. **Content Changes:**
   - README.md: Complete rewrite to remove all assignment traces
   - Notebook markdown cells: Remove exercise numbers and point values
   - Notebook title: Change from "Exercise 5.4" to professional title

#### Safety Assessment
- **Low Risk:** Notebook file rename has no code dependencies
- **Medium Risk:** Notebook content changes require careful cell-by-cell review
- **Safe:** All changes are content/naming only, no logic changes

---


## Phase 2: Pre-Change Audit

### Audit Completed
All findings documented in `suggestion.txt`

### Summary of Findings

#### Assignment Traces (16 instances)
- **README.md:** 5 instances
  - Title mentions "NNTI Assignment 6"
  - Project type labeled as "University Assignment/Task"
  - Description references course name
  - References non-existent submission folder with student ID
  - Instructions reference non-existent folder path

- **Notebook (FFNN_(1).ipynb):** 11 instances
  - Title: "Exercise 5.4 - Feedforward Neural Network (3 points)"
  - Multiple section headers with exercise numbers (5.4.1, 5.4.2, 5.4.3, 5.4.4) and point values
  - Markdown cells with "In the lecture", "In this exercise", "To complete this exercise"
  - Bold instructions with point values: "(0.5 points)"

#### Naming Issues (1 instance)
- **Notebook filename:** `FFNN_(1).ipynb`
  - Has parentheses (unprofessional)
  - Unclear what "(1)" means
  - Should be: `feedforward_neural_network.ipynb`

#### Path Issues
- **None found:** No absolute paths detected
- All paths are relative or non-existent (the non-existent folder reference is an assignment trace, not a path issue)

#### Positive Observations
- ✓ Self-contained: generates its own data
- ✓ No hardcoded absolute paths
- ✓ Clean code structure
- ✓ Already has executed outputs showing it works
- ✓ Good visualizations included

### Next Steps
Proceed to Phase 3 to apply changes systematically.

---

