# Task Guide: Programmers - Training the Model

## Goal
Train or fine-tune the multilingual character-level NLP in Space model.

---

## What You Will Need
- Python 3.8+
- PyTorch 1.12+
- GitHub experience
- GPU (recommended)
  - CUDA is available in Google Colab ([guide](https://www.geeksforgeeks.org/how-to-use-gpu-in-google-colab/))
- A terminal or IDE
- Machine learning knowledge (e.g., BiLSTM, [reference](https://paperswithcode.com/method/bilstm))

---

## Instructions

### Step 1: Set Up the Project
1. Clone the repository:
```bash
git clone https://github.com/your-repo-placeholder
cd nlp-in-space
```
2. Install dependencies:
```bash
pip install pytorch
tgmd
datasets
pandas
```

---

### Step 2: Prepare Preset Training Data
1. Open `myprogram.py` and locate the method:
```python
def load_training_data(self):
```
2. Add or remove language files in this method. More language resources: [OPUS dataset](https://opus.nlpl.eu/)

**Important**: If you add a new language, be sure to update `char_to_idx` to include its characters.

---

### (Optional) Step 3: Use Your Own Training Data
If you want to train on your own corpora:
1. Create the folder structure:
```
/data/
  /english/
    en_corpus.txt
  /spanish/
    es_corpus.txt
```
2. Ensure `.txt` files:
   - Use one sentence per line
   - Are UTF-8 encoded
3. Preprocessing is handled internally via `load_training_data()`.

**Warning**: If characters in your corpus are not added to the model’s `char_to_idx`, predictions will fail.

---

### Step 4: Customize Training Runs
#### Change model architecture:
In `myprogram.py`, update the model constructor:
```python
def __init__(self, embed_size=256, hidden_size=512, num_layers=2):
```
**Caution**: Large parameter sizes and datasets may increase training time and GPU usage.

#### Adjust the context window:
The default lookback size is 5 characters.
In `load_test_data()`:
```python
if len(seq) < 5:
    seq = seq + [self.char_to_idx[' ']] * (5 - len(seq))
data.append(seq[-5:])
```

---

### Step 5: Add Input Text
1. Open `input.txt`
2. Type the test messages (one per line). The model will guess the next letter for each.

### (Optional) Step 6: Add Correct Answers
Open `answer.txt` and add the correct next letter (one per line, case-insensitive).

**Warning**: Ensure the number of answers matches the input lines.

---

### Step 7: Train and Test the Model
Train:
```bash
python myprogram.py train --work_dir work
```
Test:
```bash
python myprogram.py test --work_dir work --test_file input.txt --output_file output.txt
```

### (Optional) Step 8: Measure Accuracy
```bash
python accuracytesting.py
```
This will compare predictions (`output.txt`) to answers (`answer.txt`) and output accuracy.

---

### Step 9: View Predictions
Open `output.txt` to see the model’s guesses for each phrase.
