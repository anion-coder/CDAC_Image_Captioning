# 📚 Text Complexity and Simplification with BERT and Handcrafted Features

This project analyzes the complexity of text and provides simplification suggestions using a combination of BERT embeddings and handcrafted readability features. It uses a multi-task learning approach to classify complexity and generate simpler alternatives.

---

## 🗂 Project Structure

- **Data**: Contains datasets for training and evaluating the models.
- **Models**:
  - **CWI Model**: Detects complex words in the input text.
  - **BERT Model**: Used for generating replacement candidates and keyword extraction.
  - **Text Complexity Model**: A multi-task model combining BERT embeddings and handcrafted features to classify complexity into `Low`, `Moderate`, or `High`.
- **Notebooks**: Jupyter notebooks for training, testing, and demonstration.

---

## ⚙️ Functionality

1. **Complexity Classification**  
   Classifies text complexity using a multi-task model that leverages BERT + readability features.

2. **Word Simplification**  
   - Uses BERT MLM to mask complex words.
   - Suggests simpler replacements based on Zipf frequency and context.

3. **Keyword & Subject Term Definition**  
   - Extracts subject-related keyphrases.
   - Injects bracketed definitions using Wikipedia or WordNet.

4. **Visualization**  
   - Performance metrics, training curves, and prediction examples.

---

## 📦 Dependencies

Make sure you have Python 3.x and install the following libraries:

```
pip install pandas numpy nltk textstat scikit-learn sentence-transformers \
tensorflow torch matplotlib seaborn transformers huggingface_hub keybert \
deepmultilingualpunctuation spacy rouge wordfreq gensim gradio ollama groq requests
```

Also download the required NLTK and spaCy resources:

```
python -m nltk.downloader punkt
python -m nltk.downloader averaged_perceptron_tagger
python -m nltk.downloader wordnet
python -m nltk.downloader omw-1.4
python -m spacy download en_core_web_sm
```

---

## 🚀 Usage

### 1. Analyze Text Complexity

```python
input_text = "This is an example of a complex sentence with technical terms."
complexity_level = model.predict_complexity(input_text)
print("Complexity Level:", complexity_level)
```

### 2. Generate Simplification Suggestions

```python
simplification_candidates = model.generate_simplification(input_text)
print("Suggestions:", simplification_candidates)
```

### 3. Annotate Subject Terms

```python
annotated_text = annotate_subject_terms(input_text)
print("Annotated:", annotated_text)
```

---

## 🧪 Example

```python
Input:
"Ocean stratification influences nutrient flow across the thermocline."

Output:
"Ocean stratification (the natural separation of ocean water into layers) influences nutrient flow across the thermocline (a distinct layer in water based on temperature)."
```

---

## 🤝 Contributing

Contributions are welcome!  
Feel free to open issues, suggest features, or submit pull requests.

---

## 📄 License

This project is licensed under the MIT License.
