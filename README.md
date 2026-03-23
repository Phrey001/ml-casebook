# ml-casebook

Use a shared repo-level virtual environment for the notebooks in this repository.

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python -m ipykernel install --user --name ml-casebook --display-name "Python (ml-casebook)"
```

In your notebook editor, select the `Python (ml-casebook)` kernel.

If you use VS Code, select the repo `.venv` interpreter first, then choose the same environment as the notebook kernel.
