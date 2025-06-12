# End Users: Running Predictions

---
## Goal
Use NLP in Space as an interactive tool to predict the next letter in a phrase.

---

## What You Will Need
- A browser or terminal with Python installed ([Download Python](https://www.python.org/downloads/))
- Familiarity with running command lines or scripts
- Familiarity with downloading files from GitHub

---

## Instructions

### Step 1: Download the Necessary Files
1. Visit the GitHub repository: [NLP-in-Space GitHub](https://github.com/ahelii/nlp-in-space)
2. Click the green **Code** button and select **"Download ZIP"**
3. Extract the ZIP file and open the project folder in your IDE or terminal

---

### Step 2: Add Input Text
1. Open the file called `input.txt`
2. Type the message(s) you want to test:
   - Each line is treated as a new individual phrase
   - The model guesses 3 characters for each phrase

**Examples:**
```
Happy New Ye
```
or
```
Happy New Ye
Happy birth
```
---

### (Optional) Step 3: Add Correct Answers
To determine model accuracy:
1. Open `answer.txt`
2. Enter the correct next letter for each line in `input.txt` (case-insensitive).
    
Example Happy New Ye(a)r
```
a
```
or
```
a
d
```
> **Warning**: Exceeding the number of answers beyond the number of phrases will cause inaccurate accuracy testing

---

### Step 4: Run the Model
Run this command in your terminal or command line:
```bash
python myprogram.py test --work_dir work --test_file input.txt --output_file output.txt
```

---

### (Optional) Step 5: Measure Accuracy
To check the model's accuracy:
```bash
python accuracytesting.py
```
This compares `output.txt` predictions to `answer.txt` answers. If any of the three predictions match the correct answer, the model counts it as correct.

**Example `output.txt`:**
```
awe
```
or
```
awe
d!t
```

---
### Step 6: View Output
Open `output.txt` to see the model’s top-3 guesses for each input phrase.

---