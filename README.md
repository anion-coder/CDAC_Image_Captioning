# 🧠 Enhancing Image Accessibility for Blind Students

This project presents a deep learning-driven pipeline to make textbook diagrams, maps, and charts more accessible to blind and visually impaired students. The system integrates vision-language modeling, complexity analysis, sentence simplification, and natural-sounding TTS to produce vivid, simplified, and speech-friendly descriptions of visual educational content.

---
Google Collab File : https://colab.research.google.com/drive/1dguVnyBFkFuY9guh4lcjSto-Dp7v4jyB?usp=sharing
---
## Demo 
Input : ![image](https://github.com/user-attachments/assets/585f059b-5e92-4d16-8c80-10806dbf4ef6)
Output :
---
**Introduction (Context & Purpose):**  
This chart is like a profile of the ocean, showing how the temperature of water changes as you go deeper. In oceanography, understanding this relationship is important because it helps us learn about marine ecosystems, ocean currents, and how heat is distributed in the ocean. The chart represents the temperature of water at different depths, and it reveals distinct patterns in various ocean zones.
---
**Breakdown of Data (Sensory & physical Language):**  
Imagine running your fingers over a long hill that gets colder as you go down. The chart shows a sharp drop in temperature as depth increases, especially in the mid-latitudes. The blue line on the chart plummets like an elevator in a skyscraper, starting from a warm temperature near the surface and rapidly descending to colder temperatures at around 1000 meters. Beyond this point, the temperature continues to decrease, but at a more gradual pace. In contrast, the temperature in the torrid zone (near the equator) remains relatively stable for a while before it starts to decrease with depth, as shown by the dotted line. The graph can be likened to tracing a landscape with your hand, where the surface is warm, and as you move downward, the temperature drops sharply, then levels out.
---
**Key Insights (Textbook Relevance):**  
The chart illustrates the concept of thermoclines, where the temperature drops significantly with depth, particularly in mid-latitude regions. This is a key concept in understanding ocean stratification — large body of water constituting a principal part of the hydrosphere, where layers of water form based on temperature and density differences. Just as how layers in a cake are distinct, the ocean has distinct layers, with the surface being warmer and less dense, and deeper layers being colder and denser. This stratification affects marine life distribution and ocean circulation patterns. For example, in colder regions, the temperature drops more sharply with depth, whereas in warmer regions, the change is more gradual.
---
**Conclusion (Summary & Importance):**  
In summary, this chart tells the story of how water temperature changes with depth, much like a journey from a warm surface to the cold depths of the ocean. Understanding this is important for oceanography because it helps us understand how oceans regulate climate, support marine life, and influence weather patterns. The chart is a simple yet powerful tool for visualizing these complex relationships, making it a valuable resource for studying the ocean’s behavior.

---
Audio output : To obtain the audio output run the collab file 
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

## 🔍 Problem Statement

Blind students face major barriers in understanding visual elements in science and geography textbooks. Traditional Braille and audio alternatives often fail to convey detailed visual information, and existing image captioning or TTS systems lack context, clarity, or emotional tone.

---

## 🧩 Proposed Solution

We propose a **modular pipeline** that:
- Generates sensory-rich image descriptions using **vLLMs**
- Classifies and simplifies text using a **Text Complexity Neural Network**
- Identifies and replaces complex words with simpler alternatives via **BERT-MLM**
- Annotates domain-specific terms inline with Wikipedia or WordNet definitions
- Adds **punctuation for prosody** and synthesizes clear, natural Indian-accented audio via **Parler-TTS**

---

## 🧱 System Architecture

```
Chart Image → Vision-Language Model → Text Complexity Classifier
            → Sentence Simplifier (BERT + Zipf)
            → Domain Term Annotator (KeyBERT + Wikipedia)
            → Punctuation Restorer
            → Parler-TTS 
            → Accessible Audio Output
```

---

## 🔬 Core Components

### 1. Vision-Language Model
Uses vLLM (e.g., Meta-LLaMA-4-Maverick) to generate metaphor- and sensory-rich descriptions of educational charts.

### 2. Text Complexity Model (TCM-NN)
A hybrid neural model combining:
- **Sentence-BERT embeddings**
- **Handcrafted features** (Flesch, Fog, sentence length, unique word ratio)

### 3. Sentence Simplification
- Complex Word Identification via BiLSTM (trained on CWISHARED)
- BERT MLM used for masked word prediction
- Zipf frequency used to choose simpler substitutes

### 4. Domain Term Explanation
- KeyBERT extracts key subject terms
- Wikipedia or WordNet definitions inserted inline

### 5. Punctuation Restoration
- Adds commas and full stops to improve prosody in TTS output

### 6. Text-to-Speech (TTS)
- Parler-TTS used for natural Indian-accented voice output
- Emphasizes tone, pause, and clarity for blind learners

---

## 📊 Results

| Metric                       | Before | After |
|-----------------------------|--------|-------|
| **Average Zipf Score**      | 4.2    | 6.8   |
| **Readability Grade**       | 10     | 6     |
| **Comprehension (User)**    | 3.1    | 4.6   |


---

## 🧠 Example Output

**Input Image Description:**  
"This graph shows temperature change with ocean depth."

**Generated Simplified Description:**  
"The line drops like a cliff, showing a sharp temperature decrease. This graph shows how cold water sinks deeper. The thermocline (a layer where temperature changes quickly with depth) is shown clearly."

---

## 💾 Installation

```bash
pip install nltk wikipedia torch pandas transformers sentence-transformers wordfreq spacy keybert soundfile
python -m nltk.downloader punkt averaged_perceptron_tagger wordnet omw-1.4
python -m spacy download en_core_web_sm
```

---

## 🧪 Test Example

```python
from simplify_pipeline import annotate_subject_terms, simplify_text, tts_convert

text = "Ocean stratification influences nutrient flow across the thermocline."
simplified = simplify_text(text)
annotated = annotate_subject_terms(simplified)
audio = tts_convert(annotated)
```

---

## 📍 Dataset Sources

- CWISHARED 2018 (Complex Word Identification)
- Simple Wikipedia + Educational Corpora (for complexity training)

---

## 👨‍🔬 Authors

Siddhanth Moraje, Simran Sota, Shriya Deshpande, Sakshi Golatkar,  
Leena Chourey, Vinaya Sawant, Prachi Tawde  
Dwarkadas J. Sanghvi College of Engineering, Mumbai, India

---


