# 🛠 Troubleshooting Guide: NLP in Space

Use this guide to fix common issues encountered during installation, training, or prediction with the **NLP in Space** character prediction system.

---

### ❗ Error: `ModuleNotFoundError: No module named 'torch'`
**Cause**: PyTorch is not installed.

**Fix**:
```bash
pip install torch
```

---

### ❗ Error: `Permission denied` or `Command not found`
**Cause**: You might be in the wrong directory or using a restricted environment.

**Fix**:
- Make sure you're inside the project folder:
```bash
cd nlp-in-space
```

---

### ❗ Error: `CUDA out of memory`
**Cause**: The model is too large for your available GPU.

**Fix**:
- Reduce the following parameters in `CharPredictorModel`:
  - `embed_size`
  - `hidden_size`
  - `num_layers`
- Try using a smaller training dataset
- Force CPU training:
```bash
python myprogram.py train --device cpu
```
*(Note: CPU training will be slower)*

---

### ❗ Issue: Predictions contain unknown or blank characters
**Cause**: Some characters in your input are not in the model’s vocabulary.

**Fix**:
- Open `input.txt`
- Remove or replace any characters **not** defined in `char_to_idx`
- Ensure test input only uses characters seen during training

---

Need more help? Visit the [FAQ](./FAQ.md) or open a GitHub issue for support.
