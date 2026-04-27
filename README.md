# Partial Reproduction of Quantum Walk Phase Classification via Machine Learning 🚶‍♂️🤖

> Supervised machine learning applied to Discrete-Time Quantum Walks (DTQW) with random coin operators — a partial reproduction of results from a published Physical Review E paper.

---

## 📖 About the Project

This project is a **partial reproduction** of results from the article:

> *"Localization of quantum walks with classical randomness: Comparison between manual methods and supervised machine learning"*, Physical Review E (2023).

The goal is to demonstrate that machine learning classifiers can detect **phase transitions** in Discrete-Time Quantum Walks (DTQW) driven by randomly perturbed coin operators, reproducing the key result of **FIG. 4(b)** from the reference article using three different supervised ML approaches.

### What was reproduced?

Only the dynamics of **Section 1 — "Discrete random angles in rotation"** from the article was simulated. The resulting quantum walk probability distributions were then analyzed through two physical measures described in the paper:

- **Section 2 — Moment of Inertia (MoI):** measures how spread the wavefunction is over the lattice.
- **Section 3 — Inverse Participation Ratio (IPR):** quantifies the degree of localization of the quantum state.

Finally, the **supervised machine learning pipeline** from **Section B** of the paper was applied, training three classifiers to detect the transition between delocalized and localized regimes. The trained models successfully reproduced **FIG. 4(b)** — showing the crossing of accuracy curves as a function of the disorder parameter Δθ — for **all three ML methods** discussed in the article.

---

## ✨ Features

- [x] Simulation of DTQW dynamics with a random rotation coin (discrete random angles)
- [x] Computation of Inverse Participation Ratio (IPR)
- [x] Computation of Moment of Inertia (MoI)
- [x] Training data generation (single and multiple cycles of the disorder interval)
- [x] Supervised classification with **Stochastic Gradient Descent (SGD)**
- [x] Supervised classification with **Multilayer Perceptron (MLP) Neural Network**
- [x] Supervised classification with **Convolutional Neural Network (Conv)**
- [x] Reproduction of FIG. 4(b) for all three ML methods
- [ ] Reproduction of other sections of the article (e.g., other types of disorder or quantum walk geometries)

---

## 🛠 Technologies

- **Language:** Python 3.x
- **Quantum Walk Simulation:** NumPy
- **Data Handling:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Classical ML:** Scikit-learn (`SGDClassifier`, `MLPClassifier`)
- **Deep Learning:** TensorFlow / Keras (Convolutional Neural Network)
- **Curve Fitting:** SciPy (`curve_fit`)
- **Model Persistence:** Joblib

---

## 📁 Project Structure

```
.
├── 01_quantum_walk_functions.ipynb          # Defines DTQW simulation functions + IPR and MoI measures
├── 02_generate_training_data_single_cycle.ipynb  # Generates ML training data (single disorder cycle)
├── 03_generate_training_data_multi_cycle.ipynb   # Generates ML training data (multiple disorder cycles)
│
│── SGD (Stochastic Gradient Descent)
├── 04_SGD_isolated_analysis.ipynb           # Curve crossing (FIG. 4b) using SGD
├── 05_SGD_parameter_selection.ipynb         # Hyperparameter search for SGD
├── 06_SGD_accuracy_analysis.ipynb           # Prediction accuracy analysis for SGD
│
│── MLP (Multilayer Perceptron Neural Network)
├── 07_MLP_isolated_analysis.ipynb           # Curve crossing (FIG. 4b) using MLP
├── 08_MLP_parameter_selection.ipynb         # Hyperparameter search for MLP
│
│── CNN (Convolutional Neural Network)
├── 09_Conv_isolated_analysis.ipynb          # Curve crossing (FIG. 4b) using Conv
└── 10_Conv_parameter_selection.ipynb        # Hyperparameter search for Conv
```

## 🔬 Physical Background

The **Discrete-Time Quantum Walk (DTQW)** is the quantum analog of a classical random walk. At each time step, a coin operator is applied to the internal (spin) degree of freedom, followed by a conditional shift operator. For a **random coin**, the rotation angle θ is drawn randomly at each step:

$$\hat{C}(\theta) = \begin{pmatrix} \cos\theta & i\sin\theta \\ i\sin\theta & \cos\theta \end{pmatrix}$$

By varying the disorder parameter Δθ (the range of random angles), the system transitions between **delocalized** (quantum ballistic) and **localized** (Anderson-like) regimes.

The machine learning task is to classify probability distributions as belonging to either the delocalized (Label 0) or localized (Label 1) phase. The crossing of accuracy curves for both labels, as a function of Δθ, identifies the **critical transition point** — this is **FIG. 4(b)** of the reference article.

---

## 🚀 How to Run

### Prerequisites

- Python 3.8+
- `pip` package manager
- (Recommended) A virtual environment

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/your-repo.git

# Enter the project directory
cd your-repo

# (Optional) Create and activate a virtual environment
python -m venv venv
source venv/bin/activate       # Linux/macOS
venv\Scripts\activate          # Windows

# Install dependencies
pip install -r requirements.txt
```

### Suggested Execution Order

1. `01_quantum_walk_functions.ipynb` — Understand the simulation functions (no data generated).
2. `02_generate_training_data_single_cycle.ipynb` — Generate the training dataset.
3. `03_generate_training_data_multi_cycle.ipynb` — Generate the validation dataset (optional).
4. Run any of the analysis notebooks (`04` through `10`) independently.

> ⚠️ The data generation notebooks must be executed before the analysis notebooks, as the latter depend on the CSV files produced by the former.

---

## 📊 Main Result

All three ML methods (SGD, MLP, and CNN) successfully reproduced **FIG. 4(b)** from the reference article. The accuracy curves for delocalized and localized labels cross near the theoretical critical value of Δθ, confirming that the classifiers are able to detect the quantum phase transition from the probability distribution data alone.

---

## 📄 Reference

> *Localization of quantum walks with classical randomness: Comparison between manual methods and supervised machine learning, PRE, 2023, DOI: 10.1103/PhysRevE.108.035308.

---

## 📝 License

This project is intended for academic and educational purposes.
