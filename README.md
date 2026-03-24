# ML Casebook

A curated collection of machine learning examples — focusing on problem framing, model decisions, tradeoffs, and production considerations.

This repository is an evolving casebook to document and develop applied ML thinking.

## Current Contents

- Customer Churn Prediction (Classification)  
  Problem framing, feature engineering, model comparison, evaluation, and production considerations

More ML examples and case thinking to be added.

## Virtual Environment Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python -m ipykernel install --user --name ml-casebook --display-name "Python (ml-casebook)"
```

In your notebook editor, select the `Python (ml-casebook)` kernel.

If you use VS Code, select the repo `.venv` interpreter first, then choose the same environment as the notebook kernel.
