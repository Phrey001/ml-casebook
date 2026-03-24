# ML Casebook

A curated collection of machine learning examples with a focus on problem framing, model decisions, and practical considerations.

This repository is an evolving casebook to document and develop applied ML thinking.

## Current Contents

- Customer Churn Prediction
  - Notebook: `ml-examples/churn_prediction/churn_prediction.ipynb`
  - Companion framing note: `ml-examples/churn_prediction/churn_problem_framing.md`
- Movie Recommender System
  - Main notebook: `ml-examples/recommender/recommender.ipynb`
  - Companion framing note: `ml-examples/recommender/recommender_problem_framing.md`
  - Lightweight framework demos:
    - `ml-examples/recommender/demo/tensorflow_recommender_demo.ipynb`
    - `ml-examples/recommender/demo/pytorch_recommender_demo.ipynb`
  - Demo practices note:
    - `ml-examples/recommender/demo/deep_learning_recommended_practices.md`

## Templates

- Notebook template: `ml-examples/templates/ipynb_template.md`
- Notebook companion framing template: `ml-examples/templates/notebook_problem_framing_template.md`
- Pure-thinking case template: `ml-examples/templates/case_thinking_template.md`

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
