---
tags:
  - word
---
TF-IDF (Term Frequency - Inverse Document Frequency) combines:
- TF: How often a term appears in the document
- IDF: How rare the term is across all documents.

$$
\text{tf-idf(t, d, D) = tf(t, d) * log(N / df(t))}
$$

- Where
	- N = total number of documents
	- df(t) = number of documents containing term t
- Meaning:
	- If a term is common (high df), then IDF is low, bringing the tf-idf score down toward zero.
	- If a term is rare (low df), then IDF is high, and it gets more weight if it also occurs in the document.
- Example
	- "the" might have IDF $\approx 0$ → TF-IDF $\approx 0$ (uninformative)
	- "salad" might appear in only 2 plays → high IDF → TF-IDF is significant