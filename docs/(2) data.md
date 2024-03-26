# Data collecton and loading

[![googlecolab](img/c.jpg)]()

# Sourcing data
A wide range of online sources are available for collecting data on a similar number of topics. Online archives and repositories often make raw text files available, or text can be extracted from other available content such as web pages or PDFs.

We won't cover the details of collecting a dataset here, instead assuming that you have already collected your own set of text files to work on. Python can handle a range of different file formats as input, but some of the steps will need to be customised depending on your chosen format.

For demonstrative purposes, this cookbook uses a set of AI-generated content on a range of themes (primarily to respect the copyright of works we use in research). You can see more information how these data were generated in the [data folder]().

If you are interested in interacting with online sources of data, you may find the following examples helpful:
    - [Introduction to web scraping](https://www.geeksforgeeks.org/python-web-scraping-tutorial/)
    - [Introduction to accessing APIs](https://www.dataquest.io/blog/python-api-tutorial/)

# Working with external data
Once you've collected a dataset, you are ready to begin working with the text in Python. There are a wide range of file handling options that can automatically parse different structures. We'll give you some common examples below.

## Loading data
A ``.text`` file is the simplest format for handling text data. Here is a snippet of code to read one in as a single string.
```python
with open('example.txt','r',encoding='utf-8') as f:
    text = '\n'.join(f)
```
Note the ``encoding`` parameter we used here, which is useful for handling a range of special characters and is typically required for processing web data.

Alternatively, you may have created a ``.csv`` file containing information for a range of different documents. Pandas is a useful library for automatically converting these data into a convenient format.

```python
import pandas as pd
df = pd.read_csv('example.csv')
```

We're going to use a slightly different format for working with our example text generated using AI tools called a ``.json`` file. This format is a good way to attach relevant metadata to a document text.

```python
import json
with open('example.json','r',encoding='utf-8') as f:
    data = json.load(f)
```

## Making a corpus
The above examples all work on a single file, but can be easily expanded to cover an entire corpus of documents. Here's an example that works for all files in a folder.
```python
import os
files = os.listdir('example_folder')
corpus = []
for file in files:
    with open(f'example_folder/{file}','r',encoding='utf-8') as f:
        corpus.append(json.load(f))
```

## A note about pre-processing
One difference between the examples we're presenting here and many practical applications of natural language processing is the need for pre-processing of data. Our examples are carefully constructed to require minimal pre-processing to correct OCR or transcription mistake or remove unncessary content. Some example of basic examples are included on the next page, or you can read more detail via an [online tutorial](https://www.geeksforgeeks.org/text-preprocessing-in-python-set-1/)
