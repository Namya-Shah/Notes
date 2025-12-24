---
Created On: 2024-06-22
Links:
  - "[[Probability]]"
Subject:
  - "[[EM 614 - Advanced Probability and Statistics]]"
---
# Definition
- Probability is the theoretical study of measuring certainty that an event will happen.
- Data is the computational side of the story, whereas probability is the theoretical side of the story.
- The **frequentists** argue that probability is the relative frequency of an outcome.
- The **Bayesians** argue that probability is a subjective belief.
- It is foundational discipline for statistics, hypothesis testing, machine learning.
>**Probability is the measure of the size of a set.**
## Understanding Probability
- Probabilities should be between 0-100% or from 0.0-1.0.
- *Likelihood* is similar to probability
- Probability is about quantifying predictions of events yet to happen, whereas likelihood is measuring the frequency of events that already occured. 
- In statistics and machine learning, we often use likelihood (the past) in the form of data to predict probability (the future).
- It is important to note that a probability of an event happening must be strictly between 0% and 100% or 0.0 and 1.0.
- Probabilities of all possible mutually exclusive outcomes for an event (meaning only one outcome can occur, not multiple) must sum 1.0 or 100%.
- Alternatively, probability can be expressed as an $odds\ O(X)$ such as 7:3, 7/3, or $2.\bar333$ . To turn an odds $O(X)$ into a proportional $P(X)$, use this formula:

$$
P(X) = \frac {O(X)} {1+O(X)}
$$

> While many people feel more comfortable expressing probabilities as percentages or proportions, odds can be a helpful tool. If I have an odds of 2.0, that means I feel an event is two times more likely to happen than not to happen.
- These six faces form a set called the **sample space**. A sample space is the set containing all possible outcomes, which in our case is $\Omega$ = {1,2,3,4,5,6}. The denominator 6 is the size of the sample space.
- This process involves **measuring** the size of event (E) and $\Omega$.
- Probability is a number assigned by certain **rules** such that it describes the **relative size** of the event E compared with the sample space $\Omega$. So, when we say that **probability is a measure of the size of a set**, we create a mapping that takes in a set and outputs the size of that set.
- Assigning a probability value to an event cannot be arbitary; otherwise, the probabilities may be inconsistent.
### Probability vs Statistics
- *Probability* and *statistics* interchangeably, and while it is understandable to conflate the two disciplines, they do have distinctions. *Probability* is purely theoretical of how likely an event is to happen and does not require data. *Statistics*, on the other hand, cannot exist without data and uses it to discover probability and provides tools to describe data.
# Set Theory
## Why study set theory?
- In a nutshell, a set is simply a collection of things.
## Basic concepts of a set
> A set is a collection of elements. We denote
> $A = {\xi_1,\xi_2,...,\xi_n}$
> as a set, where $\xi_i$ is the $i^{th}$ element in the set.

1. $[a,b] = \{x|a\leq x \leq b\}$ is a closed interval on $\mathbb R$.
2. $(a,b) = \{x|a<x<b\}$ is an open interval on $\mathbb R$.
3. $(a,b] = \{x|a<x\leq b\}$ is a semi-closed interval on $\mathbb R$.

- A set can be used to describe a collection of **functions**.
--- start-multi-column: Examples
```column-settings  
number of columns: 2  
largest column: equal  
```

![[CleanShot 2024-06-26 at 13.01.36@2x.png]]

--- end-column ---

![[CleanShot 2024-06-26 at 13.05.27@2x.png]]

--- end-multi-column
![[CleanShot 2024-06-26 at 13.06.14@2x.png]]
 - A set can also be used to describe a collection of sets. Let $A$ and $B$ be two sets. Then $C = \{A,B\}$ is a set of sets.
 > Note that here we are not saying $C$ is the union of two sets. We are only saying that $C$ is a collection of two sets.
 
 ![[CleanShot 2024-06-26 at 13.10.17@2x.png]]

## Subsets
- Given a set, we often want to specify a portion of the set, which is called a **subset**.
- $B$ is a subset of $A$ if for any $\xi \in B$, $\xi$ is also in $A$. We write

$$
B \subseteq A
$$

	to denote that $B$ is a subset of $A$.
- $B$ is called a **proper subset** of $A$ if $B$ is a subset of $A$ and $B \not = A$. We denote a proper subset as $B \subset A$. Two sets $A$ and $B$ are equal if and only if $A \subseteq B$ and $B \subseteq A$.
![[CleanShot 2024-06-26 at 13.14.59@2x.png]]
![[CleanShot 2024-06-26 at 13.15.08@2x.png]]
## Empty set and universal set
- A set is **empty** if it contains no element. We denote an empty set as

$$
A = \emptyset
$$

- A set containing an element 0 is not an empty set. It is a set of one element, {0}. The number of elements of the empty set is 0. The empty set is a subset of any set, i.e., $\emptyset \subseteq A$ for any $A$. We use $\subseteq$ because $A$ could also be an empty set.
### Examples
1. The set $A = \{x|sin x > 1\}$ is empty because no $x \in \mathbb R$ can make $sin\ x > 1$.
2. The set $A = \{x|x > 5\ and\ x < 1\}$ is empty because the two conditions $x > 5$ and $x < 1$ are contradictory.
### Universal Set
- The **universal set** is the set containing all elements under consideration. We denote a universal set as

$$
A = \Omega
$$

- The universal set $\Omega$ contains itself, i.e., $\Omega \subseteq \Omega$. The universal set is a relative concept.
## Union
- The **union** of two sets $A$ and $B$ contains all elements in $A$ or in $B$. That is

$$
A \cup B = \{\xi|\xi \in A\ or\ \xi \in B\}
$$

- The union of two sets connects the sets using the logical operator "**or**". Therefore, the union of two sets is always larger than or equal to the individual sets.
- If $A = \{f\ :\ \mathbb R \rightarrow \mathbb R|f(x) = ax\}$ and $B = \{f\ :\ \mathbb R \rightarrow \mathbb R|f(x) = b\}$, then $A \cup B =$ a set of sloped lines with a slope $a$ plus a set of constant lines with height $b$. Note that $A \cup B \not = \{f\ :\ \mathbb R \rightarrow \mathbb R| f(x) = ax + b\}$ because the latter is a set of sloped lines with arbitary $y$-intercept.
1. If $A = \{1,2\}$ and $B = \emptyset$, then $A \cup B = \{1,2\}$.
2. If $A = \{1,2\}$ and $B = \Omega$, then $A \cup B = \Omega$.
![[CleanShot 2024-06-26 at 13.39.54@2x.png]]
#### Infinite Union
For an infinite sequence of sets $A_1,A_2,...,$ the infinite union is defined as

$$
\bigcup^\infty_{n=1}A_n = \{\xi\ |\ \xi \in A_n \ for \ at \ least\ one\ n \ that \ is \ finite\}.
$$

> The finite $n$ requirement says that we only evaluate the sets for a finite number of $n$'s. This $n$ can be arbitrarily large, but it is finite.

![[CleanShot 2024-06-26 at 13.44.17@2x.png]]
- To take the infinite union, we know that the set $[-1,1)$ is always included, because the right-hand limit $1-\frac 1 n$ approaches $1$ as $n$ approaches $\infty$. So the only question concerns the number $1$. **Should $1$ be included?** According to the definition above, we ask: Is $1$ an element of **at least one** of the sets $A_1, A_2, ..., A_n$? Clearly it is not: $1 \notin A_1, 1 \notin A_2,...$. In fact, $1 \notin A_n$ for any finite $n$. Therefore $1$ is not an element of the infinite union, and we conclude that

$$
\bigcup^\infty_{n=1}A_n = \bigcup^\infty_{n=1}
\begin{bmatrix}
-1,1-\frac 1 n
\end{bmatrix}= [-1,1).
$$

![[CleanShot 2024-06-26 at 17.19.09@2x.png]]
### Intersection
- The union of two sets is based on the logical operator **or**. If we use the logical operator **and**, then the result is the **intersection** of two sets.
The **intersection** of two sets $A$ and $B$ contains all elements in $A$ **and** $B$. That is,

$$
A\ \cap\ B = \{\xi\ |\ \xi \in A\ and\ \xi \in B\}
$$

- Intersection finds the common elements of the two sets. It is not difficult to show that $A \cap B \subseteq A\ and\ A \cap B \subseteq B$.
![[CleanShot 2024-06-26 at 17.23.49@2x.png]]
1. If $A = \{1,2,3,4\}, B = \{1,5,6\}$, then $A \cap B = \{1\}$.
2. If $A = \{1,2\}, B=\{5,6\}$, then $A \cap B = \emptyset$.
3. If $A = (3,4], B = [3.5,\infty)$, then $A \cap B = [3.5,4]$.
4. If $A = (3,4], B = \emptyset$, then $A \cap B = \emptyset$.
5. If $A = (3,4], B = \Omega$, then $A \cap B = (3,4]$.
6. If $A = \{f\ :\ \mathbb R \rightarrow \mathbb R | f(x) = ax\}$ and $B = \{f\ :\ \mathbb R \rightarrow \mathbb R|f(x)=b\}$, then $A \cap B =$ the intersection of a set of sloped lines with a slope $a$ and a set of constant lines with height $b$. The only line that can satisfy both sets is the line $f(x) = 0$. Therefore, $A \cap B = \{f|f(x) = 0\}$.
7. If $A = \{\{1\},\{2\}\}$ and $B = \{\{2,3\},\{4\}\}$, then $A \cap B = \emptyset$. This is because $A$ is a set containing two sets, and $B$ is a set containing two sets. The two sets $\{2\}$ and $\{2,3\}$ are not the same. Thus, $A$ and $B$ have no elements in common, and so $A \cap B = \emptyset$.
#### Infinite Intersection
For an infinite sequence of sets $A_1, A_2, ... ,$ the **infinite intersection** is defined as

$$
\bigcap^\infty_{n=1}A_n = \{\xi\ |\ \xi \in A_n\ for\ every\ finite\ n.\}
$$

To understand this definition, we note that

$$
\xi \in A\ and\ \xi \in B \Leftrightarrow \xi
$$ is in **every one** of $A$ and $B$.

As a result, it follows that
$$

\xi \in A_1\ and\ \xi \in A_2 \ and\ \xi \in A_3 ... \Leftrightarrow \xi

$$
is in **every one of** $A_1,A_2,A_3,...$
- Since the infinite intersection requires that $\xi$ is in every one of $A_1,A_2,...,A_n$, if there is a set $A_i$ that does not contain $\xi$, the infinite intersection is an empty set.
Consider the problem of finding the infinite intersection of $\bigcap^\infty_{n=1}A_n$, where
$$

A_n = [0,1+\frac 1 n).

$$
We note that the sequence of sets is $[0,2], [0,1.5], [0,1.33], ...$. As n → ∞, we note that the limit is either $[0,1)$ or $[0,1]$. Should the right-hand limit $1$ be included in the infinite intersection? According to the definition above, we know that $1 \in A_1, 1 \in A_2, ..., 1 \in A_n$ for any finite $n$. Therefore, $1$ is included and so
$$

\bigcap^\infty_{n=1}A_n = \bigcap^\infty_{n=1}[0,1+\frac 1 n) = [0,1].

$$
![[CleanShot 2024-06-26 at 18.00.36@2x.png]]
### Complement and difference
- Besides union and intersection, there is a third basic operation on sets known as the **complement**.
The **complement** of a set A is the set containing all elements that are in $\Omega$ but not in $A$. That is,
$$

A^c = \{\xi \| \ \xi \in \Omega\ and\ \xi \notin A\}.

$$
- The complement is a set that contains everything in the universal set that is not in $A$. Thus the complement of a set is always relative to a specified universal set.
![[CleanShot 2024-06-26 at 18.04.49@2x.png]]
1. Let $A = \{1,2,3\} \ and\ \Omega = \{1,2,3,4,5,6\}$. Then $A^c = \{4,5,6\}$.
2. Let $A$ = {even integers} and $\Omega$ = {integers}. Then $A^c$ = {odd integers}.
3. Let $A$ = {integers} and $\Omega$ = $\mathbb R$. Then $A^c$ = {any real number that is not an integer}.
4. Let $A = [0,5)$ and $\Omega = \mathbb R$. Then $A^c$ = {any real number that is not an integer}.
5. Let $A = [0,5)$ and $\Omega = \mathbb R$. Then $A^c = (-\infty,0) \cup [5,\infty).$
6. Let $A = \mathbb R$ and $\Omega = \mathbb R$. Then $A^c = \emptyset$.
#### Difference
The difference A\B is the set containing all elements in $A$ but not in $B$.
$$

A \textbackslash B = \{\xi\ |\ \xi \in A\ and\ \xi \notin B\}.

$$
1. Let $A = \{1,3,5,6\}\ and\ B = \{2,3,4\}$. Then $A \textbackslash B = \{1,5,6\}\ and\ B\textbackslash A = \{2,4\}.$
2. Let $A = [0,1],\ B = [2,3]$, then $A \backslash B = [0,1]$, and $B \textbackslash A = [2,3]$. This example shows that if the two sets do not overlap, there is nothing to subtract.
3. Let $A = [0,1],\ B = \mathbb R$, then $A \textbackslash B = \emptyset$, and $B \textbackslash A = (-\infty,0) \cup (1,\infty)$. This example shows that if one of the sets is the universal set, then the difference will either return the empty set or the complement.
![[CleanShot 2024-06-26 at 18.29.57@2x.png]]
> **QUESTION:** Show that for any two sets $A$ and $B$, the differences $A\textbackslash B$ and $B\backslash A$ never overlap, i.e., $(A\backslash B)\ \cap \ (B\backslash A) = \emptyset$.
> **ANSWER:** Suppose by contradiction, that the intersection is not empty so that there exists an $\xi \in (A\textbackslash B)\ \cap \ (B\textbackslash A)$. Then, by the definition of intersection, $\xi$ is an element of $(A\textbackslash B)$ and $(B\textbackslash A)$. But if $\xi$ is an element of $(A\textbackslash B)$, it cannot be an element of $B$. This implies that $\xi$ cannot be an element of $(B\textbackslash A)$ since it is a subset of $B$. This is a contradiction because we just assumed that the $\xi$ can live in both $(A\textbackslash B)$ and $(B\textbackslash A)$.

Let $A$ and $B$ be two sets. Then
$$

A \textbackslash B = A\ \cap \ B^c

$$
**PROOF:** Let $x \in A\textbackslash B$. Then $x \in A$ and $x \notin B$. Since $x \notin B$, we have $x \in B^c$. Therefore, $x \in A$ and $x \in B^c$. By the definition of intersection, we have $x \in A \cap B^c$. This shows that $A \textbackslash B \subseteq A \cap B^c$. Conversely, let $x \in A \cap B^c$. Then $x \in A$ and $x \in B^c$, which implies that $x \in A$ and $x \notin B$. By the definition of $A \textbackslash B$, we have that $x \in A \textbackslash B$. This shows that $A \cap B^c \subseteq A \textbackslash B$.
# Disjoint and Partition
- It is important to be able to quantify situations in which two sets are not overlapping. In this situation, we say that the sets are **disjoint**.
Two sets $A$ and $B$ are **disjoint** if
$$

A \ \cap \ B = \emptyset

$$
For a collection of sets $\{A_1,A_2,...,A_n\}$, we say that the collection is disjoint if, for any pair $i \not= j$.
$$

A_i \ \cap \ A_j = \emptyset

$$
1. Let $A = \{x>1\}$ and $B = \{x<0\}$. Then $A$ and $B$ are disjoint.
2. Let $A = \{1,2,3\}$ and $B = \emptyset$. Then $A$ and $B$ are disjoint.
3. Let $A = (0,1)$ and $B = [1,2)$. Then $A$ and $B$ are disjoint.
# Partition
A collection of sets $\{A_1,...,A_n\}$ is a partition of the universal set $\Omega$ if it satisfies the following conditions:
- (**non-overlap**)$\{A_1,...,A_n\}$ is disjoint:
$$

A_i \ \cap \ A_j = \emptyset

$$
- (**decompose**) Union of $\{A_1,...,A_n\}$ gives the universal set:
$$

\bigcup^n_{i=1}A_i = \Omega

$$
- In plain language, a partition is a collection of non-overlapping subsets whose union is the universal set.
## Probability Math
- When we work with a single probability of an event $P(X)$, known as a *marginal probability*, the idea is fairly straightforward.
### Joint Probabilities
- Let's say you have a fair coin and a fair six-sided die. You want to find the probability of flipping a heads and rolling a 6 on the coin and die, respectively. These are two separate probabilities of two separate events, but we want to find the probability that both events will occur together. This is known as a *joint probability*.
- Think of a joint probability as an **AND** operator.
- The probability of both events occurring (assuming they are independent) is simply multiplying the two together:
$$

P(A\ AND\ B) = P(A)\ \text{x}\ P(B)

$$
$$

P(heads) = \frac 1 2

$$
$$

P(6) = \frac 1 6

$$
$P$(heads AND 6) $= \frac 1 2\ \text{x}\ \frac 1 6 = \frac 1 {12} = 0.8\bar3$
- A lot of probability rules can be discovered by generating all possible combinations of events, which comes from an area of discrete math known as permutations and combinations.
> This is known as the *product rule*.
> Mutually exclusive events -> events that cannot occur simultaneously
### Union Probabilities
- When we deal with OR operations with probabilities, this is known as a *union probability*.
- *Mutually exclusive events*, which are events that cannot occur simultaneously. For example, if I roll one die I cannot simultaneously get a 4 and a 6. I can only get one outcome.
- The logical way to remove double counting in a union probability is to subtract the joint probability. This is known as the *sum rule of probability* and ensures every joint event is counted only once:
$P(A\ OR\ B) = P(A)+P(B)-P(A\ AND\ B)$
$P(A\ OR\ B) = P(A)+P(B)-P(A)\ x\ P(B)$
- Note that this formula also applies to mutually exclusive events. If the events are mutually exclusive where only one outcome $A$ or $B$ is allowed but not both, then the joint probability $P(A\ AND\ B)$ is going to be 0.
## Conditional Probability and Bayes' Theorem
- A probability topic that easily confuses people is the concept of *conditional probability*, which is the probability of an event $A$ occurring given event $B$ has occurred. It is typically expressed as $P(A\ GIVEN\ B)$ or $P(A|B)$.
- The reason people can be so easily confused by conditional probabilities is because the direction of the condition matters, and the two conditions are conflated as somehow being equal.
$$

P(A|B) = \frac {P(B|A)P(A)} {P(B)}

$$
- If event $A$ has no impact on event $B$, then what does that mean for conditional probability $P(B|A)$? That means $P(B|A) = P(B)$, meaning event $A$ occurring makes no difference to how likely event $B$ is to occur.
$$

P(A\ AND\ B) = P(B)\ \text{x}\ P(A|B) \implies P(B|A)\ \cdot\ P(A)

$$
- If I wanted to calculate the probability of $A$ or $B$ occurring, but $A$ may affect the probability of $B$, we update our sum rule like this:
$$

P(A\ OR\ B) = P(A) + P(B) - P(A|B)\ *\ P(B) \implies P(A)\ +P(B)\ -P(B|A)\ \cdot P(A)

$$
- The sum rule $P(A|B)\ \text{x}\ P(B)$ would yield 0 if the events $A$ and $B$ cannot happen simultaneously.
# Binomial Distribution
- One tool that might be relevant here is the *binomial distribution*, which measures how likely $k$ successes can happen out of $n$ trials given $p$ probability.
> We use SciPy function $binom.pmf()$ function ($PMF$ stands for "probability mass function") to print all probabilities for our binomial distribution.
# Beta Distribution
- The *beta distribution* allows us to see the likelihood of different underlying probabilities for an event to occur given $alpha$ successes and $beta$ failures.
- Beta distribution is a continuous function, meaning it forms a continuous curve of decimal values (as opposed to the tidy and discrete integers in the binomial distribution). This is going to make the math with the beta distribution a bit harder, as a given density value on the y-axis is not a probability. We instead find probabilities using areas under the curve.
- The beta distribution is a type of *probability distribution*, which means the area under the entire curve is 1.0 or 100%.
- Every continuous probability distribution has a *cumulative density function (CDF)*, which calculates the area up to a given x-value.
- Our **CDF** calculates area only to the left of our boundary, not the right. Think about our rules of probability, and with a probability distribution the total area under the curve is 1.0. If we want to find the opposite probability of an event (greater than 0.90 as opposed to less than 0.90), just subtract the probability of being less than 0.90 from 1.0, and the remaining probability will capture being greater than 0.90.
![[CleanShot 2024-06-23 at 22.29.21@2x.png]]
![[CleanShot 2024-06-23 at 22.29.00@2x.png]]
- **For finding probability for the underlying success rate between 0.80 and 0.90**
![[CleanShot 2024-06-23 at 22.30.37@2x.png]]
![[CleanShot 2024-06-23 at 22.31.21@2x.png]]
- The [[beta distribution]] is a fascinating tool to measure the probability of an event occurring versus not occurring, based on a limited set of observations. It allows us to reason about probabilities of probabilities, and we can update it as we get new data.
# Expectation
- Expectation is the mean of the random variable $X$. $p_X(x)$ as the percentage of times that the random variable $X$ attains the value $x$. When this percentage is multiplied by $x$, we obtain the contribution of each $x$. Summing over all possible values of $x$ then yields the mean.
> Sum of P.M.F. is always $1$.

$$

average = \frac{1}{N}\sum^N_{n=1}x^{(n)}

$$
- $E[X]$ is computed from the *ideal* histogram, whereas average is computed from the *empirical* histogram.