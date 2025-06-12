# Conceptual Overview for Programmers: NLP in Space

**NLP in Space** is a character-level multilingual prediction system designed to enhance communication efficiency. It was developed in a futuristic scenario: onboard a heavily populated orbital space station in the year 2045. Multiple pods need to exchange information, but language barriers exist. The system predicts the next most likely character in a message and presents the top three options to the user, accelerating mutual understanding in high-stakes environments.

---

## Motivation and Context

In space, voice communication may be limited or impractical. Astronauts use an eye tracking interface that displays **three predicted characters** at a time. If the correct character isn't displayed, they must manually navigate a slower selection process.

To improve communication experience, the system is designed to:

- **Minimize error**: Ensure the correct next character appears in the top three predictions.
- **Minimize latency**: Deliver predictions rapidly after each character input.
- **Minimize training time**: Adapt quickly to new languages with efficient training processes.

---

## Key Technical Features

The system is modular and built for multilingual character-level predictions. Below are its core architectural features.

### Multilingual Character-Level Modeling
- Supports **13 human languages** using Unicode character representations.
- Languages were selected based on global popularity and dataset richness.

### Configurable Model Pipeline
- Accepts **3-character windows** as input.
- Outputs **top-3 predictions** via a softmax layer.
- Includes preprocessing tools for cleaning and encoding multilingual corpora.

### Pluggable Architecture
- Supports **RNN**, **GRU**, or **Transformer** backbones.
- Easily modifiable embeddings and model hyperparameters.

### Customizable Evaluation Pipeline
- Tracks **processing time** per language.
- Calculates **error rate** on a validation set.

---

## Use Cases for Developers

Developers working with NLP in Space may find it useful for:

- **Model fine-tuning**: Adapt the model to a specific domain, dialect, or application context.
- **Parameter exploration**: Modify key training values such as learning rate, hidden size, batch size, and context window.
- **Error analysis**: Use the bundled accuracy testing utility to evaluate model performance and diagnose weaknesses.
- **Cross-lingual transfer**: Analyze how well models trained on high-resource languages generalize to underrepresented languages by adjusting training corpus size.

---

## Data Statement

The model is trained using the **OPUS-100 dataset**, a multilingual collection of parallel corpora sourced from:

- Government documents
- Movie subtitles
- News articles

Curated by the **University of Helsinki**, OPUS maps English sentences to their translations in other languages. We used **13 distinct languages**:

- **English (en)**
- **Chinese (zh)**
- **Japanese (ja)**
- **Hindi (hi)**
- **Russian (ru)**
- **Arabic (ar)**
- **Bengali (bn)**
- **French (fr)**
- **Spanish (es)**
- **Italian (it)**
- **Portuguese (pt)**
- **Turkish (tr)**
- **Korean (ko)**
- **Hebrew (he)**

We limited training to **15,000 sentences per language** due to computational constraints, ensuring balanced multilingual training with reasonable hardware demands.

---

Want to contribute or extend this model? Fork the repo and explore the modular training pipeline, evaluation script, and preprocessing utilities!
