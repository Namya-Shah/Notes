---
Lecture Date: 2025-07-20
Presentation: 
Links: 
Subject: 
References:
  - "[[GloVe]]"
tags:
---
```table-of-contents
```
# Natural Language Processing
* It deals with all forms of **SPOKEN** and **WRITTEN** data
* ASR (Audio Speech Recognition) → Siri
* TTS (Text to Speech) → Otter Notes
* STS (Speech to Speech) → ChatGPT Live

> A combination of both spoken and written data example → Transcripts/Video Subtitles
## Two components of NLP
![[Pasted image 20250822114421.png|400]]
1. **NLU (Natural Language Understanding)**
	* Comprehension by computers of the **structure and meaning** of human language (e.g., English, Spanish, Japanese), allowing users to interact with the computer using natural sentences.
	* ![[Pasted image 20250822114656.png]]
	* Example Tasks:
		* Text Classification
		* Reviews Classification
		* Spam Detection
		* Topic Classification
		* Hate Speech Detection
		* Sentence Similarity
	* Benchmark:
		* GLUE
		* Super GLUE
2. **NLG (Natural Language Generation)**
	* NLG enables computer to write like humans
	* Example Tasks:
		* Machine Translation
		* Summarization
	* Benchmark:
		* GEM
## Fundamental NLP Tasks
* **Tokenization**
	* Segmenting a sequence of characters into tokens
	* ![[Pasted image 20250822115018.png]]
* **Stop-word removal**
	* Removing common words
	* ![[Pasted image 20250822115049.png]]
* **Lemmatization**
	* Reducing tokens to the base forms
	* ![[Pasted image 20250822115108.png]]
* **[[Stemming]]**
	* Reducing vocabulary size and merge semantically similar variants.
	* Can cause overstemming or understemming
		* Overstemming
		* Understemming

> [!IMPORTANT] NOTE
> If preserving exact linguistic meaning matters, then:
> - Use lemmatization instead - produces dictionary-based canonical forms (like "is" → "be")
> - Use subword tokenizers (BPE, WordPiece, etc.) which handle morphology differently and can reduce the need for stemming.

* **Part of Speech (PoS) tagging**
	* Assigning each token a particuar part of speech tag, based on both its definition and its context.
	* ![[Pasted image 20250822115138.png]]
* **Named Entity Extraction**
	* Identifying the named entities like Person, Country, Organization, etc.
	- ![[Pasted image 20250822115200.png]]
* **Parse Tree Generation**
	- ![[Pasted image 20250822115226.png]]
# Traditional NLP Pipeline
![[Pasted image 20250822115246.png]]
Steps:
1. Inputting data
2. Data Cleaning (Stage 1)
3. Preprocessing using Fundamental tasks (Stage 2)
4. Representation Generation (Stage 3)
	* [[One-hot Vector Generator]]
	* [[TF-IDF Vector Generator]]
	* High Dimensional Vector
		* Size = no. of tokens in the vocabulary
	* Very Sparse
		* Non-zero dimensions <= the no. of tokens in the sentence
	* Based on bag-of-words (BoW) assumption, which does not captures
		* position in text
		* semantics
		* co-occurences in different documents
5. Downstream Task Model/Algo (Stage 4)
6. Outputs
## Representation Generation via Distributional Semantics
- High Dimensional Vector
	- Size = no. of tokens in the vocabulary
- Very Sparse
	- Non-zero dimensions <= the no. of tokens in the sentence
- Based on bag-of-words (BoW) assumption, which does not captures:
	- position in text
	- semantics
	- co-occurences in different documents
## Emergence of Deep Learning for NLP
* How to create concise length vectors?
	* Length of vectors < 1000
	* We don't need to create 1.5L vector
* End-to-end training
	* No need to explicitly extract syntactic and semantic features
* Dividing the training into two phases
	* General purpose programming
		* In this phase, the model learns grammar, semantics, forming sentences in a language
		* Phase: Pre-training
			* Learning a language
	- Task specific learning
		* Training to do a specific task
		* Phase: Fine-tuning
			* Learning how to solve specific task (One task or multiple tasks)
* End-to-end training loop
	1. Tokenization
	2. Pretraining
		* Pre-training requires massive amounts of data
		* General training
		* It doesn't require any type of labels (no supervised or unsupervised)
	3. Fine-tuning (Instruction Tuning)
		* May require just few instructions to get the task done at hand

> In traditional NLP pipeline, we do pre-training and fine-tuning altogether
# The DL-based NLP Pipeline
![[Pasted image 20250822115756.png]]
## Pretraining
![[Pasted image 20250822115857.png]]
## Fine-tuning
![[Pasted image 20250822115915.png]]
# Data Preprocessing
## Tokenization
- Sentence Tokenizer (Sequence of characters -> sentences)
	- Input:
		- It was the best of times, it was the worst of times. It was the age of wisdom, it was the age of foolishness.
	- Expected Output:
		- It was the best of times, it was the worst of times.
		- It was the age of wisdom, it was the age of foolishness.
* Word Tokenizer (Sequence of characters → words)
	* Input: It was the best of times, it was the worst of times.
	* Expected Output: It, was, the, best, of, times, it, was, the, worst, of, times
* Subword Tokenizer (Sequence of characters → subwords)
	* Input: We would like to embed this extremely short text with an unknown word zozofah!
	* Expected Output: We, would, like, to, em, ##bed, this, extremely, short, text, with, an, unknown, word, z, ##o, ##of, ##ah
**Use commands in terminal:**
* tr
* sed
* grep
```python
# A simple word tokenization using Python Split Function

text = "It was the best of times, it was the worst of times."

print(text)

print(text.split()) # We can split using delimiters ("?", ",")
```
## Challenges with Simple Tokenizers
* Finland's → Finland Finlands Finland's
* What're, I'm, shouldn't → What are, I am, should not
* San Francisco → one token or two
* m.p.h. → ??
* State-of-the-art → four tokens or just one
* Multi-disciplinary → Two tokens or just one
# Normalization
```python
import nltk

nltk.download('punkt_tab')
nltk.download('stopwords')
nltk.download('words')
```

```python
from nltk import word_tokenize

text = "I'm eating food and drinking milk."
word_tokenize(text)
```

```python
# Python's Punctuation Removal Module
text = "I'm eating food and drinking milk."

tokens = word_tokenize(text)
print(tokens)

tokens = [word for word in tokens if word.isalpha()] # only outputs words without any punctuations
print(tokens)
```

```python
# Python's Lowercasing Module
text = "I'm eating food and drinking milk."

tokens = word_tokenize(text)
print(tokens)

tokens = [word for word in tokens if word.isalpha()] # only outputs words without any punctuations
print(tokens)

tokens = [word.lower() for word in tokens] # does nothing, just lowercase the above words
print(tokens)
```

```python
# NLTK's Stopword Removal Module
from nltk.corpus import stopwords

text = "I'm eating food and drinking milk."
tokens = word_tokenize(text)
tokens = [word.lower() for word in tokens if word.isalpha()]
print(tokens)

tokens = [word for word in tokens if word not in stopwords.words("english")] # removes stopwords (common words)
print(tokens)
```

```python
# NLTK's Spelling Correction Module

from nltk.corpus import words

from nltk.metrics.distance import edit_distance

correct_words = words.words() # by default it gives english words
incorrect_word = "interresting"

editD_word = [(edit_distance(incorrect_word, w), w) for w in correct_words if w[0] == incorrect_word[0]]

print(sorted(editD_word, key=lambda val:val[0])[0][1]) # val[0] -> edit_distance
```

```python
print(list(edit_distance(incorrect_word, w) for w in correct_words if w[0] == incorrect_word[0]))

print("\n")

print(editD_word)

# print(min(editD_word[0]))
```
# Lemmatization
* Reduce inflections or variant forms to base form:
	* am, are, is → be
	* car, cars, car's, cars' → car
	* Have to find the correct dictionary headword form
```python
from nltk.stem import WordNetLemmatizer
wordnet_lemmatizer = WordNetLemmatizer()

nltk.download('wordnet')
nltk.download('omw-1.4')

# Lemmatizing words
print(wordnet_lemmatizer.lemmatize('dogs'))
print(wordnet_lemmatizer.lemmatize('churches'))
print(wordnet_lemmatizer.lemmatize('abaci'))
```
# Stemming
* Reducing terms to their stems
* Crude chopping of affixes
```python
from nltk.stem.porter import PorterStemmer
porter_stemmer = PorterStemmer()

print(porter_stemmer.stem('presumably'))
print(porter_stemmer.stem('multiply'))
```
# Regular Expressions
A regular expression is a special sequence of characters that helps you **match or find** other strings or sets of strings.
* Regular expressions are widely used in UNIX world.
* How to use them? Depends on different implementations.
* In python, re module provides full support for regular expressions.
## Patterns

| **Pattern** | **Description**                                       |
| ----------- | ----------------------------------------------------- |
| ^           | Matches beginning of line                             |
| $           | Matches end of line                                   |
| .           | Matches any single character except newline           |
| [...]       | Matches any single character in brackets              |
| [^...]      | Matches any single character not in brackets          |
| re*         | Matches 0 or more occurrences of preceding expression |
| re+         | Matches 1 or more occurences of preceding expression  |
| re?         | Matches 0 or 1 occurence of preceding expression      |
| (re)        | Groups regular expressions and remembers matched text |
## Flags

| **Option** | **Description**                                               |
| ---------- | ------------------------------------------------------------- |
| re.I       | Performs case-insensitive matching                            |
| re.M       | Makes $ and ^ match the end and start of a line respectively  |
| re.S       | Makes a period (dot) match any character, including a newline |
| re.U       | Interprets letters according to the Unicode character set     |
## Characters Matching

| **Pattern** | **Description**                             |
| ----------- | ------------------------------------------- |
| [0-9]       | Matches any digit; same as [0123456789]     |
| [a-z]       | Match any lowercase ASCII letter            |
| [A-Z]       | Match any uppercase ASCII letter            |
| [a-zA-Z0-9] | Match any of the above                      |
| \[^aeiou]   | Match anything other than a lowercase vowel |
| \[^0-9]     | Match anything other than a digit           |
## Special Characters

| **Pattern** | **Description**                             |
| ----------- | ------------------------------------------- |
| \d          | Match a digit: [0-9]                        |
| \D          | Match a nondigit: \[^0-9]                   |
| \s          | Match a whitespace character: [\t \r \n \f] |
| \S          | Match nonwhitespace: [^ \t \r \n \f]        |
| \w          | Match a single word character: [A-Za-z0-9_] |
| \W          | Match a nonword character: \[^A-Za-z0-9_]   |
```python
import re

line = "Cats are smarter than dogs"

matchObj = re.match(r'(.*) are (.*?) .*', line, re.M|re.I) # (.*) -> Greedy Matching | (.*?) -> Non-Greedy Matching

if matchObj:
	print("matchObj.group() : ", matchObj.group()) # default is 0 : which means the whole sentence
	print("matchObj.group() : ", matchObj.group(1))
	print("matchObj.group() : ", matchObj.group(2))
else:
	print("No match!!!")
```

```python
# Regular Expressions: Match
# Match checks for a match only at the beginning of the string
matchObj = re.match(r'dogs', line, re.M|re.I)
if matchObj:
	print("matchObj.group() : ", matchObj.group())
else:
	print("No match!!!")

# Regular Expressions: Search
# Search checks for a match anywhere in the string
searchObj = re.search(r'dogs', line, re.M|re.I)
if searchObj:
	print("searchObj.group() : ", searchObj.group())
else:
	print("No match!!!")
```

```python
# Removing everything after digits
phone = "2004-959-559 # This is my Phone Number"
num = re.sub(r'#.*$', "", phone)
print(num)
```

```python
# Removing anything other than digits
num = re.sub(r'\D', "", phone)
print(num)
```

```python
# Use of TweetTokenizer
from nltk import word_tokenize, TweetTokenizer, MWETokenizer 

text = "I ate 8.5 ice-creams in New Delhi 🥶😇"

tokenizer_1 = word_tokenize(text) # It considers both emojis as one and not two separate things
print(f"Using word_tokenize: {tokenizer_1}")  

tokenizer_2 = TweetTokenizer() # It considers both emojis as two and not one unlike word_tokenize
print(f"Using TweetTokenizer: {tokenizer_2.tokenize(text)}")
```

```python
# Tweets
tokenizer = TweetTokenizer()
text1 = "Congrats @shashitharoor Sir, for winning ‘Chevalier de la Legion d’Honneur’, highest civilian honour by the French government.#FranceinIndiafrancediplo_EN"

print(tokenizer.tokenize(text1))
print(word_tokenize(text1))

tokenizer = MWETokenizer()
tokenizer.add_mwe(('New', 'Delhi'))
tokenizer.add_mwe(('8.5', 'ice-creams'))
tokenizer.tokenize(word_tokenize(text))
```

```python
# Tweets
tokenizer = TweetTokenizer()
text1 = "Congrats @shashitharoor Sir, for winning ‘Chevalier de la Legion d’Honneur’, highest civilian honour by the French government.#FranceinIndiafrancediplo_EN"

print(tokenizer.tokenize(text1))
print(word_tokenize(text1))

tokenizer = MWETokenizer()
tokenizer.add_mwe(('New', 'Delhi'))
tokenizer.add_mwe(('8.5', 'ice-creams'))
tokenizer.tokenize(word_tokenize(text))
```

```python
text2 = "An alphabet is a source of communication for alot of people."

star = re.search(r"a*", text2)
plus = re.search(r"a+", text2)
question = re.search(r"a?", text2)

print(f"Pattern matching using *: {star}")
print(f"Pattern matching using +: {plus}")
print(f"Pattern matching using ?: {question}")
```

# Distributional Semantics

**Python Notebook:** https://colab.research.google.com/drive/1r0XUrxYqS5-xB3HscDtx8-Q7wguYKei3?usp=sharing#scrollTo=yaACfzUcGnCF
# [[Word2Vec]]
![[Pasted image 20250716175629.png]]
- **CBOW (Continuous-Bag-of-Words):** Predict target word given a context words
	- 
- **Skip-Gram:** Predict context words given a target word
- 

## Singular Value Decomposition
### Implementation
```python
import numpy as np
la = np.linalg
words = ['I', 'like', 'enjoying', 'deep', 'learning', 'NLP', 'flying', '.]
arr = np.array([
	[0,2,1,0,0,0,0,0],
	[2,0,0,1,0,1,0,0]
])
```
### Challenges
- For an `n x m` matrix, the computation cost is quadratic $O(mn^2)$.
- Hard to incorporate new words or documents

---
# QUESTIONS
1. Does Amazon review depends on stars? If it takes stars into account, then will it be negative or positive if the user gives one star but positive review.
	- Amazon doesn't directly average the star ratings. Instead, it has a machine learning model that **weights ratings based on factors like recency, verified-purchase status, reviewer history, and even the reviewer's typical rating behavior**
	- Star Rating
		- Impacts product's overall rating. So, even if we give 1 star it can impact the average rating of the product given by stars.
	- Review Text
		- It doesn't impact scores but it is given a sentiment of positive or negative done by sentiment analysis model.
	- In this scenario, the overall rating will drop the overall rating even if we give positive comments.
2. If we remove stopwords in stage 2, shouldn't the dictionary only consider the words that are left than whole.
	- Yes, the dictionary only contains the remaining words and not the stop words.
3. In subword tokenizer, does ## means any number of letters?
	- In subword tokenizers like BERT's WordPiece, the prefix `##` is not a wildcard, it's a marker. It indicates that the token is a continuation of the previous token and should be merged without a space during decoding.
	- **What does `##` actually mean?**
		- Tokens without `##`, such as `"token"`, start a new word
		- Tokens with `##`, like "##ization", are appended to the preceding token to form a complete word (e.g., `"token"` + `"##ization` → `"tokenization"`)
	- **Why is it useful?**
		- Keeps vocabulary size manageable -- common words are single tokens; rare or complex ones are broken into subwords.
		- Helps model generalize
		- Makes it possible to represent never-before-seen words by recombining known subwords.
```python
from transformers import BertTokenizer
tokenizer = BertTokenizer.from_pretrained("bert-base-uncased")
print(tokenizer.tokenize("tokenization"))
# -> ["token", "##ization"]
```
4. Do we lemmatize or stem before tokenization? If yes, won't it change the meaning of the sentence.
	- No, we do not lemmatize or stem before tokenization
	- But if we stem before lemmatize, then we can get words that are not present in the dictionary and can change meaning.
	- While stemming before lemmatization can reduce token volume, it risks merging distinct words (like "presenting" and "presentation") into the same form, making lemmatization unable to restore the nuance. If your task needs POS or meaning fidelity, stick with lemmatization only.
5. Penalizing more common words?
	- They are like filler - they don't help discriminate meaning.
	- Penalizing them emphasizes unique, informative words that are more helpful for tasks like:
		- Clustering
		- Classification
		- Search relevance ranking
	- We penalize common words because they don't convey meaningful differences across texts. By giving them low weight, TF-IDF makes sure our models focus on informative, distinctive terms that matter most.