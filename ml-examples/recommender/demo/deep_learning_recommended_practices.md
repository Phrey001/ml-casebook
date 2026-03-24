# Deep Learning Recommended Practices

This note outlines practical deep learning habits for recommender systems, highlighting what is included in the demos and what is intentionally omitted to keep them lightweight.

**Status legend**:
- `✓`: implemented in the demo
- `X`: recommended in practice but intentionally omitted for simplicity

## Recommended Practices Checklist

### Set Up The Problem Well
| Practice | Status | Why it matters |
|---|---|---|
| **Build a minimal end-to-end walkthrough first**: start with the smallest useful data, model, and evaluation loop | X | In practical production work, this helps verify the full pipeline before scaling complexity or data volume. |
| **Design the data and evaluation setup well**: make sure inputs, labels, splits, and metrics match the real problem | X | In production systems, data quality and evaluation design often matter more than model complexity. |
| **Start with a simple baseline**: compare against an easier benchmark first | ✓ | Shows whether added complexity is actually helping. |
| **Keep the data split clean**: separate `train`, `validation`, and `test` | ✓ | Prevents leakage and keeps evaluation honest. |
| **Choose one main metric**: use one primary score for comparison | ✓ | Makes model selection easier to explain. |

### Train And Debug Efficiently
| Practice | Status | Why it matters |
|---|---|---|
| **Watch both training and validation loss**: do not rely on training loss alone | ✓ | Helps spot underfitting and overfitting. |
| **Stop early when validation stalls**: keep the best model state | ✓ | Avoids wasting epochs and overtraining. |
| **Check whether predictions look sensible**: inspect outputs, not just metrics | ✓ | Helps catch issues that summary numbers can hide. |
| **Review where the model fails**: look at representative errors, not just average performance | X | Helps identify concrete weaknesses and guides the next improvement step. |
| **Isolate what changed**: use component analysis or ablations when comparing model versions | X | Helps show which change actually improved or hurt performance. |
| **Use model complexity carefully**: use the bias-variance tradeoff as a guide | ✓ | More flexible models can fit better, but may overfit. |
| **Prefer fast iteration over premature perfection**: run small, informative experiments before polishing everything | X | Faster feedback usually leads to better decisions than trying to perfect the first version. |

### Improve The Model Deliberately
| Practice | Status | Why it matters |
|---|---|---|
| **Add complexity only when needed**: keep the model small unless a bigger one clearly helps | ✓ | Saves tuning effort and keeps the demo readable. |
| **Try multiple settings**: tune learning rate, embedding size, batch size, and similar choices | X | Can improve performance and training stability. |
| **Check weak spots by segment**: review performance for different user or item groups | X | Shows where the model breaks in practice. |
| **Validate online**: confirm gains through A/B testing | X | Offline gains do not always translate into product impact. |

### Data And Optimization Habits
| Practice | Status | Why it matters |
|---|---|---|
| **Fix random seeds**: keep runs more reproducible | ✓ | Makes results easier to compare. |
| **Make optimization easier**: center targets or normalize inputs when helpful | ✓ | Helps training converge more smoothly. |
| **Train in batches**: avoid row-by-row updates | ✓ | Uses hardware better and speeds training. |
| **Keep preprocessing readable**: do not over-engineer small demo code | ✓ | Makes the workflow easier to inspect and debug. |
| **Test regularization choices**: try weight decay, dropout, or related controls | X | Can reduce overfitting. |
| **Use clear evaluation views**: combine a main metric with supporting checks when needed | X | Gives a fuller picture of model quality. |
| **Design evaluations to match the real task**: make the offline setup reflect how the model will actually be used | X | Reduces the risk of optimizing for the wrong target. |
| **Track experiments**: record what changed from run to run | X | Makes comparisons easier to trust. |
| **Save and monitor models properly**: support longer-running workflows | X | Improves reliability outside a notebook. |
| **Watch for drift**: check for data drift and behavior drift over time | X | Helps signal when retraining is needed because inputs or user behavior may have shifted. |
| **Try richer recommender models**: add more features, more layers, or multiple stages such as retrieval, ranking, and re-ranking | X | Can capture more complex user-item behavior. |

## Framework-Specific Habits
### TensorFlow / Keras
- Use callbacks such as early stopping instead of a fixed epoch count alone.
- Pass validation data explicitly when monitoring convergence.
- Print detected devices so GPU or CPU usage is visible.
- Keep the model definition compact and easy to inspect.

### PyTorch
- Select the device explicitly and move the model and tensors to it.
- Write a clear training loop and a separate validation loop.
- Save or restore the best model state based on validation performance.
- Keep inference code separate from training code.

## TensorFlow vs PyTorch
- **TensorFlow / Keras**: useful when you want a concise, higher-level training workflow with built-in callback support.
- **PyTorch**: useful when you want more direct control over the training loop and model behavior.
- **Shared point**: both frameworks can build the same lightweight recommender; the better choice often depends on team preference, stack, and how much control you need.

## GPU Environment Considerations
- GPU support depends on the local CUDA and driver setup, not just the notebook code.
- In practice, TensorFlow and PyTorch may require different GPU package combinations even when the model logic is similar.
- For lightweight demos, a shared environment is convenient, but separate framework-specific environments can be more reliable when both need GPU acceleration.

## Scope
- These demos are intentionally lightweight.
- The goal is to demonstrate sound framework usage and practical training habits, not to build a production system.
- The practices marked `X` still matter; they are simply outside the scope of small framework-familiarity notebooks.

## Appendix - Glossary
- **Checkpoint**: a saved model state that can be restored later.
- **Overfitting**: when a model learns the training data too closely and performs worse on new data.
- **Two-tower model**: a recommender architecture that learns separate representations for users and items before matching them.
