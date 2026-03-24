# ML Casebook

A set of applied machine learning use cases with a focus on problem framing, model trade-offs, and practical decision-making contexts.

This repository approaches ML problems in a structured way, from defining the business objective to selecting models and evaluating outcomes.

The goal is to build intuition for how machine learning models are used in practice, where modeling choices are closely tied to decision objectives and constraints.

Each use case may include:
- Companion problem-framing notes
- Lightweight implementation in reproducible notebooks
- Discussion of modeling choices, evaluation design, and practical limitations

The emphasis is on clarity and practical reasoning, rather than model complexity.

## Current Use Cases

- Customer Churn Prediction
  - Framed as a prioritization problem under limited retention budget
  - Notebook: `ml-examples/churn_prediction/churn_prediction.ipynb`
  - Companion framing note: `ml-examples/churn_prediction/churn_problem_framing.md`
- Movie Recommender System
  - Framed around personalized recommendation with lightweight implementations and practical evaluation considerations
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

More use cases and extensions will be added over time.

## Virtual Environment Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python -m ipykernel install --user --name ml-casebook --display-name "Python (ml-casebook)"
```

In your notebook editor, select the `Python (ml-casebook)` kernel.

If you use VS Code, select the repo `.venv` interpreter first, then choose the same environment as the notebook kernel.
