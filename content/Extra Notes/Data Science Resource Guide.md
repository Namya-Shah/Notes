**subjects data scientists need to know:**

- **data processing** (dataset prep for model/analysis)
    - outlier removal techniques (distribution-based, grubbs test), normalization (box-cox transformation), standardization, correlation between features, dimensionality reduction (PCA, linear discriminant analysis, non-negative matrix factorization)
- **modeling** (building/optimizing/performance eval)
    - different types of regressions/mathematical differences, regularization, variance and bias, linear and logistic regression, naive bayes, random forest (information gain / impurity score; gini, entropy), SVM, KNN, k-means clustering, performance eval (precision, recall, mse, r squared, ROC-AUC, accuracy, log-loss, benchmarking), clustering algorithms, anomaly detection models (autoencoders, PCA, isolation forest)
- **math:** linear algebra, calculus (multi-variate), statistics & probability (can include bayesian statistics for more math-specific DS roles)
- **experimental design** (A/B testing or synthetic controls)
    - sampling techniques, identification of bias in data, hypothesis testing, confidence intervals, marketing use cases, model evaluation
- **SQL**; many companies still have rounds related to SQL/data querying involving window functions, rolling averages, complex merges, and so on
- **algorithms**; LeetCode Mediums/Hards should be expected in any tech interview, especially in more math-heavy/quant roles
    - data structures + big O notation is probably not going to be asked for DS roles, but is required if the role is more software engineering focused

<aside>
💡 What you want to start learning first depends on the role you’re applying for. For example, roles within marketing analytics will involve more case studies and experimental design while R&D roles might involve more ML math and take-homes.

**The main DS Interview book (Ace the Data Science Interview) follows this chronological 7-chapter structure: *probability, statistics, machine learning, SQL & db design, coding, product sense, and case studies.*** 

</aside>

**DS Resources Links:**

- [**Data Science Cheatsheet**](https://www.reddit.com/r/learnmachinelearning/comments/yikvw4/cheat_sheets_for_machine_learning_and_data/); includes all information regarding distributions, all types of regression, clustering, NLP, neural net, time series models
- [**Great Reddit Post](https://www.reddit.com/r/rprogramming/comments/kafpgv/data_science_learning_resources/)** with Multiple Papers/Links in every DS/ML Category (Gradient Boosting, Regression, Deep Learning, Efficient Python, etc.)
- [**Another Data Science/ML Interview Cheatsheet**](https://www.reddit.com/r/learnmachinelearning/comments/yikvw4/cheat_sheets_for_machine_learning_and_data/) (18 pages)
- [**List of Data Science Questions on GitHub**](https://github.com/alexeygrigorev/data-science-interviews/blob/master/theory.md)
- [**Another General Data Science Interview Guide**](http://nadbordrozd.github.io/interviews/)
- [**Data Lemur**](https://datalemur.com/) to practice SQL
- [**Python for Data Analysis Textbook**](https://wesmckinney.com/book/)

[SQL cheat sheet.pdf](Data%20Science%20Resource%20Guide%20226d3e42462f4b74a57853b18e421b9d/SQL_cheat_sheet.pdf)

### Math Resource: Linear Algebra

**Jim Hefferson’s Linear Algebra (undergraduate intro course) Resources:**

- YouTube Lecture Series ([**first half,](https://www.youtube.com/watch?v=JnTa9XtvmfI&t=3769s) [second half](https://youtu.be/DJ6YwBN7Ya8)**) 20 total hours of lectures that follow his textbook (they are VERY good)
- [**Course Textbook**](https://joshua.smcvt.edu/linearalgebra/book.pdf)
- Additional Course Resources: [**https://hefferon.net/linearalgebra/**](https://hefferon.net/linearalgebra/)

### Math Resource: Mathematics for ML [Related Topic, Modeling: Textbook for Foundations of ML]

- Useful/Detailed Reddit Post: *Here’s a textbook for [**Foundations of Machine Learning**](https://pdfs.semanticscholar.org/e923/9469aba4bccf3e36d1c27894721e8dbefc44.pdf), the book I used for [**this course**](http://web.math.ucsb.edu/~atzberg/pmwiki_intranet/index.php?n=Teaching2018FallMachineLearningMATH_CS_120.Homepage?setskin=atzbergerClassSkin2) at my school. The course webpage has a syllabus, hw assignments, readings, lecture slides (LOTS) and even some Jupyter notebooks you can get started with.*
- In-Depth Learning Math for ML Reddit Post: [**https://www.reddit.com/r/learnmachinelearning/comments/dxcwm6/best_resources_to_learn_the/**](https://www.reddit.com/r/learnmachinelearning/comments/dxcwm6/best_resources_to_learn_the/)
- Two Sigma post on Blind regarding mathematics required for quantitative roles
    - statistics, intense programming background, strong fundamental math basics is what we end up using on a day to day basis for an execution strategies role. Strong advanced linear algebra background, optimization theory, optimal control theory, stochastic calculus is a requisite for portfolio optimization. In my experience, execution strategy development is highly simulation based with conscious mathematical tradeoffs to achieve low latencies, staying away from probability distributions as much as we can since simulation now has to sample the whole distribution for reliable P&L numbers and really really strong programming background. Candidates who cut the bar mostly have a Math, Electrical, Physics or an Economics background.
    - stochastic calculus

### Math Resource: Statistics and Probability

**Textbook** Introduction to Statistical Learning [[**https://hastie.su.domains/ISLR2/ISLRv2_website.pdf**](https://hastie.su.domains/ISLR2/ISLRv2_website.pdf)]

- Apparently easier than the statistics fundamentals textbook but covers the same material and goes in depth on statistical models
- Another book I’ve heard about (usually in college courses): [Elements of Statistical Learning](https://hastie.su.domains/ElemStatLearn/)

 

### Math Resource: Introduction to Statistics and Probability [MIT Open Courseware]

Link to full course: [https://ocw.mit.edu/courses/18-05-introduction-to-probability-and-statistics-spring-2014/](https://ocw.mit.edu/courses/18-05-introduction-to-probability-and-statistics-spring-2014/)

*includes class slides, assignments, instructor insights, readings*

### Math Resource: Topics in Mathematics of Data Science [MIT Open Courseware]

*prerequisites: linear algebra + intro to statistics/probability*

Link to full course: [https://ocw.mit.edu/courses/18-s096-topics-in-mathematics-of-data-science-fall-2015/](https://ocw.mit.edu/courses/18-s096-topics-in-mathematics-of-data-science-fall-2015/)

*includes lecture notes, assignments*

### Algorithms Resource: Blind 75 LeetCode

**Blind 75 (LeetCode practice questions):** [**https://www.techinterviewhandbook.org/best-practice-questions/**](https://www.techinterviewhandbook.org/best-practice-questions/)

- these are the top questions on LeetCode that deal with all of the different algorithms patterns; most tech interviews will involve LeetCode medium or hard questions, especially more quantitative roles will involve this in several rounds

### Algorithms Resource: Textbook for Algorithm Design

Reddit post mentioned studying this to understand algorithms and several people agreed to read through this and use it conceptually:

[SkienaTheAlgorithmDesignManual.pdf](Data%20Science%20Resource%20Guide%20226d3e42462f4b74a57853b18e421b9d/SkienaTheAlgorithmDesignManual.pdf)

[**https://www.youtube.com/user/StevenSkiena**](https://www.youtube.com/user/StevenSkiena)

### Algorithms Resource: Textbook for Data Structures/Big O

[https://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844](https://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844)

This is apparently the best textbook by far for algorithms/data structures/big O. Definitely more software engineering focused but may be useful if trying to start fresh in that field.

### ML Modeling Resource: StatQuest

[**https://www.youtube.com/c/joshstarmer**](https://www.youtube.com/c/joshstarmer)

Great resource to brush up on the basics of different modeling and model evaluation methods from scratch. Can deep dive into math after watching these videos if needed since this helps you conceptually understand model use cases/evaluation metrics. 

---

**Interesting Articles**

- [Data Scientists Need to be More End-to-End](https://applyingml.com/resources/end-to-end/)
- [My Experience as a Data Scientist in a Start-up](https://towardsdatascience.com/my-experience-as-a-data-scientist-in-a-startup-13ae037780d0) (super accurate article on what DS at a start-up is like)

 ***More to come on resources on regression, popular probability/stats interview questions, etc.***