# 🔐 Password Strength Prediction

A machine learning project that predicts the strength of any password — classifying it as **Weak**, **Medium**, or **Strong** — by learning patterns from over 670,000 real-world passwords. Built with character-level TF-IDF feature extraction and two classification models.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Results](#results)
- [License](#license)
- [Acknowledgements](#acknowledgements)

---

## Overview

Traditional password strength checkers rely on fixed rules (e.g., "must contain a number"). This project takes a smarter approach — it trains a machine learning model on real password data so it can recognize subtle patterns of weakness and strength that rule-based systems miss.

**Strength Labels:**

| Label | Meaning |
|-------|---------|
| `0`   | Weak    |
| `1`   | Medium  |
| `2`   | Strong  |

---

## Dataset

- **File:** `Password Strength.csv`
- **Size:** ~670,000 password entries
- **Columns:** `password` (string), `strength` (0 / 1 / 2)
- **Source:** Publicly available password dataset (Kaggle)

**Class Distribution:**

| Strength | Count   | Share  |
|----------|---------|--------|
| Weak (0) | 89,702  | ~13.4% |
| Medium (1) | 496,801 | ~74.2% |
| Strong (2) | 83,137  | ~12.4% |

> ⚠️ The CSV file is large (~670k rows). If uploading to GitHub, consider adding it to `.gitignore` and linking to the Kaggle source instead, or using [Git LFS](https://git-lfs.github.com/).

---

## Project Structure

```
├── Checking_Password_Strength.ipynb   # Main notebook — run this
├── Password Strength.csv              # Dataset
├── README.md                          # Project documentation
├── LICENSE                            # Apache 2.0 License
└── .gitignore                         # Standard Python gitignore
```

---

## Installation

**Step 1 — Clone the repository**

```bash
git clone https://github.com/your-username/Checking-Password-Strength-using-Machine-Learning.git
cd Checking-Password-Strength-using-Machine-Learning
```

**Step 2 — Install dependencies**

```bash
pip install pandas numpy seaborn scikit-learn
```

> Requires Python 3.7 or newer. Check your version with `python --version`.

**Step 3 — Launch the notebook**

```bash
jupyter notebook Checking_Password_Strength.ipynb
```

Or open it directly in [VS Code](https://code.visualstudio.com/) or upload to [Google Colab](https://colab.research.google.com/).

---

## Usage

1. Open `Checking_Password_Strength.ipynb`.
2. Run all cells from top to bottom (the model trains automatically — allow a few minutes).
3. At the final cell, type any password when prompted and press **Enter**.
4. The model outputs `0`, `1`, or `2` — your password's strength label.

**Example:**

```
Enter password: MyD0g$Name!99
Predicted Strength: 2  →  Strong ✅
```

```
Enter password: john123
Predicted Strength: 0  →  Weak ❌
```

---

## How It Works

```
Raw Password String
        ↓
Character-Level TF-IDF Vectorizer
  (treats each character as a token)
        ↓
Sparse Feature Matrix
        ↓
┌───────────────────────────────┐
│  Logistic Regression  (fast)  │
│  Gradient Boosting   (best)   │
└───────────────────────────────┘
        ↓
Strength Prediction: 0 / 1 / 2
```

- **TF-IDF at character level** captures how often each character appears and how unique it is across all passwords — no manual feature engineering needed.
- **Logistic Regression** serves as a fast, interpretable baseline.
- **Gradient Boosting** captures complex non-linear patterns for higher accuracy and is used for final predictions.

---

## Results

| Model                  | Test Accuracy |
|------------------------|---------------|
| Logistic Regression    | ~81–83%       |
| Gradient Boosting      | ~88–92%       |

> Exact values will print when you run the notebook. The Gradient Boosting model is used for the live prediction at the end.

---

## License

This project is licensed under the [Apache License 2.0](LICENSE).

---

## Acknowledgements

- Dataset sourced from the [Kaggle Password Strength](https://www.kaggle.com/) competition.
- Built using [scikit-learn](https://scikit-learn.org/), [pandas](https://pandas.pydata.org/), [NumPy](https://numpy.org/), and [Seaborn](https://seaborn.pydata.org/).
