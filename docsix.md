# 📘 References & FAQ: NLP in Space

A quick guide to help you troubleshoot, explore, and extend the NLP in Space model.

---

## 🤖 Running Predictions

### ❓ How do I run predictions without coding?
1. Download the code from GitHub.
2. Open `input.txt` and type your 3-letter input(s).
3. Run this command:
```bash
python myprogram.py test --work_dir work --test_file input.txt --output_file output.txt
```
4. Check `output.txt` for the predictions.

### ❓ Do I need to install anything before running?
Yes. Install the required libraries:
```bash
pip install torch tgmd datasets pandas
```
Make sure you're using **Python 3.8+**.

### ❓ What format should my test inputs be in?
Use `input.txt`. Each line represents a new phrase. The model will predict the next character for each line.

---

## 🧠 Training & Customization

### ❓ Can I train the model on new languages?
Yes. Modify the `load_training_data()` method in `myprogram.py`.
- Add or replace files in `/data/<language>/corpus.txt`
- Ensure all files are UTF-8 encoded

### ❓ Can I increase the character context window?
Yes. Modify the `load_test_data()` method.
- The default window looks back 5 characters
- Adjust padding and slicing to change it

---

## 📊 Accuracy & Evaluation

### ❓ How is accuracy calculated?
If the correct letter is in **any of the top 3 predictions**, it's considered correct.

To test:
1. Add expected answers (one letter per line) to `answer.txt`
2. Run:
```bash
python accuracytesting.py
```

### ❓ What if my predictions are wrong?
Check the following:
- Are all input characters part of the model's `char_to_idx`?
- Does `answer.txt` match the number of lines in `input.txt`?

---

## 🛠 File Reference

### ❓ What files should I modify?
- `input.txt`: Your test phrases
- `answer.txt`: (Optional) The correct next characters
- `myprogram.py`: Main program interface and configuration
- `CharPredictorModel`: The model’s internal architecture

### ❓ Where do I find predictions?
All output is saved in `output.txt`, with one line per prediction.

### ❓ What happens if I provide more answers than inputs?
The accuracy testing script may give incorrect results. Make sure `input.txt` and `answer.txt` have the same number of lines.

---

## 🌍 Multilingual Data

### ❓ Where can I get more training data?
Try these sources:
- [Hugging Face Datasets](https://huggingface.co/datasets)
- [OPUS Corpora](http://opus.nlpl.eu/)
- [Project Gutenberg](https://www.gutenberg.org/) (for public domain texts)

---
Need more help? Refer to the [Troubleshooting Guide](./TROUBLESHOOTING.md) or open an issue on the project GitHub.
