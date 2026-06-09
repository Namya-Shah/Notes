# 🎯 MAPE — The “How Bad Did I Mess Up?” Score

Alright, imagine this:

You’re predicting how many slices of pizza your friend will eat.  
You say **4 slices**.  
They actually eat **8 slices**.  

You were… *spectacularly wrong.* 🍕

Now the question is:  
**How wrong were you, *in a fair way*?**

That’s where **MAPE** comes in.

---

# 🧠 What Even Is MAPE?

**MAPE = Mean Absolute Percentage Error**

Yeah yeah, scary name. Ignore it. Break it:

- **Mean** → average  
- **Absolute** → ignore positive/negative (no drama, just magnitude)  
- **Percentage Error** → how wrong you were *relative to reality*

👉 Translation:
> “On average, how wrong were you, in percentage terms?”

---

# 🍕 Step-by-Step (with drama)

Let’s say:

| Actual (Reality) | Predicted (Your Guess) |
|-----------------|----------------------|
| 100             | 90                   |
| 200             | 220                  |
| 50              | 40                   |

---

## Step 1: Error (your failure)

Error = Actual - Predicted

| Actual | Predicted | Error |
|--------|----------|-------|
| 100    | 90       | 10    |
| 200    | 220      | -20   |
| 50     | 40       | 10    |

---

## Step 2: Absolute Error (no negativity allowed 😌)

|Error|

| Error | Absolute Error |
|------|----------------|
| 10   | 10             |
| -20  | 20             |
| 10   | 10             |

---

## Step 3: Turn it into percentage (this is the key part)

Percentage Error = |Error| / Actual

| Absolute Error | Actual | % Error |
|---------------|--------|---------|
| 10            | 100    | 0.10    |
| 20            | 200    | 0.10    |
| 10            | 50     | 0.20    |

---

## Step 4: Average it (THE “Mean” part)

MAPE = average of all percentage errors

MAPE = (0.10 + 0.10 + 0.20) / 3 = 0.1333 = 13.33%

---

# 🧠 What does 13.33% actually mean?

It means:
> “On average, my predictions are off by about **13%**.”

That’s it. That’s the whole vibe.

---

# 🤯 Why MAPE feels intuitive

Because humans think in percentages.

- Being off by **10 units** when actual = 100 → meh 😐  
- Being off by **10 units** when actual = 20 → WHAT WERE YOU DOING 💀  

MAPE *captures this difference perfectly.*

---

# 🧨 Where MAPE breaks (important!)

MAPE is cool… until it isn’t.

### 🚫 Problem 1: Division by zero

If actual = 0:

|Error| / 0 → boom 💥 undefined

MAPE literally crashes.

---

### 🚫 Problem 2: Punishes small values too hard

Example:

- Actual = 1  
- Predicted = 3  

Error = 2 → Percentage = **200%**

Even small mistakes look HUGE.

---

### 🚫 Problem 3: Biased toward underestimation

MAPE prefers predictions that are **lower than actual**, because overestimates can explode more.

---

# 🆚 MAPE vs other metrics (quick vibe check)

| Metric | Personality |
|------|------------|
| MAE | Chill, measures average error |
| MSE | Dramatic, punishes big errors hard |
| RMSE | Even more dramatic |
| MAPE | Relatable, speaks in percentages |

---

# 🧪 When should you use MAPE?

Use it when:
- You care about **relative error**
- Your data has **no zeros**
- Your audience likes **percentages (aka everyone)**

Avoid it when:
- You have zeros
- Values are very small
- You need mathematically stable metrics

---

# 🧠 Intuition Lock 🔒

Think of MAPE like this:

> “If reality is the price tag, MAPE tells you how badly you misread it — in percentage.”

---

# ⚡ One-line Cheat Code

**MAPE = “On average, how wrong was I compared to what actually happened — expressed as a percentage of reality.”**