# IPO Underpricing vs Overpricing Classification (SVM)

## What this project does
Classifies an IPO as "Underpriced" or "Overpriced" based on issue-stage information 
(before listing), using Support Vector Machine.

## Dataset
Indian IPO dataset with 652 records, including issue size, subscription levels 
(QIB, HNI, RII, Total), offer price, and listing price (2010–2026).

## Tools Used
Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Jupyter Notebook

## What I did
- Removed rows with missing subscription data and IPOs that listed flat 
  (no gain or loss, so they didn't fit either class)
- Created the target: "Underpriced" if listing price > offer price, else "Overpriced"
- Dropped columns that would leak the answer (listing price, listing gain, 
  post-listing market prices) — using only information available before listing
- Ran EDA on offer price, issue size, and subscription patterns by pricing outcome
- Trained and compared SVM with 3 kernels: linear, RBF, and polynomial
- Tuned hyperparameters (C, gamma, kernel) using GridSearchCV with 5-fold cross-validation

## Results
| Model      | Accuracy | Precision | Recall | F1 Score |
|------------|----------|-----------|--------|----------|
| Linear SVM | 0.732    | 0.730     | 1.000  | 0.844    |
| RBF SVM    | 0.707    | 0.719     | 0.978  | 0.829    |
| Poly SVM   | 0.724    | 0.727     | 0.989  | 0.838    |
| Tuned SVM  | 0.675    | 0.725     | 0.888  | 0.798    |

**Best Model:** Linear SVM (highest F1 Score; the target is imbalanced — 73% 
Underpriced vs 27% Overpriced — so F1 Score is a better measure than accuracy alone)

## Key Insight
Strong subscription demand (QIB, HNI, RII) tends to line up with underpriced IPOs, 
but no single feature cleanly separates the two classes — the model still has real 
room to improve.

## How to run it
Open `ipo_underpricing_overpricing_classification.ipynb` in Jupyter Notebook or 
Google Colab and run all cells. Requires `Initial Public Offering (Updated).xlsx` 
in the same folder.
