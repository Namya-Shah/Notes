---
tags:
  - word
---
Stemming is the process of chopping off suffixes or prefixes from words to reduce them to their base or root form (called a stem).

Unlike lemmatization, stemming does not care about the actual meaning or dictionary form -- it just applies simple rules or patterns.

> A stemmer follows heuristic rules that were manually designed by linguists to remove common suffixes (like `-ing`, `-ed`, `-s`, `-ly`, etc.)

# Example (Word: Running)
1. The stemmer checks the word against a set of rules, like:
	- If a word ends in "`ing`" and there's a **vowel before it**, remove "`ing`"
	- If the resulting word is too short or doesn't look valid, try another rule.
2. It finds: "`running` -> remove `ing` -> result: `runn`"	
> [!IMPORTANT] NOTE
> Even though `runn` isn't a real English word, stemmers don't care about correctness, only consistency.

```python
from nltk.stem import PorterStemmer

stemmer = PorterStemmer()

print(stemmer.stem("running"))   # run
print(stemmer.stem("flying"))    # fli
print(stemmer.stem("relational"))  # relat
print(stemmer.stem("cats"))      # cat
```
