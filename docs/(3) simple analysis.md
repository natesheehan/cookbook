# Simple Analysis



[![googlecolab](img/c.jpg)](https://colab.research.google.com/drive/1l9WG8W9Eewd3C3brci-5Lit74GfPzmp2?usp=sharing)


## Installing Package
```python
pip install spacy
python -m spacy download en_core_web_sm
```

## Tokenization and Sentence Segmentation



The division of text into meaningful units such as words, phrases, and sentences is foundational in NLP. SpaCy excels in breaking down text into tokens and sentences, providing a structured format for analysis.

```python
import spacy

# Load SpaCy's English language model
nlp = spacy.load('en_core_web_sm')

# Process a sample text
text = "In the late fight of the 20th century, the world witnessed a significant shift in the fight against HIV/AIDS."
doc = nlp(text)

# Tokenization
tokens = [token.text for token in doc]
print("Tokens:", tokens)

# Sentence Segmentation
sentences = [sent.text for sent in doc.sents]
print("Sentences:", sentences)
```

This snippet outputs each word and punctuation mark as separate tokens, showcasing SpaCy's precision in distinguishing textual elements.

```python
sentences = list(doc.sents)
print("Sentence 1:", sentences[0].text)
```