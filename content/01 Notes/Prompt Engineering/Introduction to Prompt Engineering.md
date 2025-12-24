## Vocabulary

LLM (Large Language Model)

Two types of LLMs

Base LLM

Predicts next word, based on text training data

Instruction Tuned LLM

Tries to follow instruction

Fine-tune on instructions and good attempts at following those instructions

Helpful, Honest, Harmless

RLHF: Reinforcement Learning with Human Feedback

## Guidelines

### Principle 1: Write clear and specific instructions

#### Tactic 1: Use delimiters

Triple quotes: “””

Triple backticks: ```Triple Backtics```

Triple dashes: - - -

Angle brackets: <>

XML tags: <tag></tag>

#### Tactic 2: Ask for structured output

HTML, JSON

#### Tactic 3: Check whether conditions are satisfied

Check assumptions required to do the task

#### Tactic 4: Few-shot prompting

Give successful examples of completing tasks then ask model to perform the task

### Principle 2: Give time to model to think

#### Tactic 1: Specify the steps to complete a task

Step 1: …

Step 2: …

…

Step N: …

#### Tactic 2: Instruct the model to work out its own solution before rushing to a conclusion

### Model Limitations

Hallucination: Makes statements that sound plausible but are not true

Reducing hallucinations:

First find relevant information, then answer the question based on the relevant information

## Iterative Prompt Development

- Idea

- Implementation (code/data)

- Experimental Result

- Error Analysis

#### Prompt Guidelines

- Be clear and specific

- Analyze why result does not give desired output

- Refine the idea and the prompt

- Repeat

#### Prompt development is an iterative process

- Try something

- Analyze where the result does not give what you want

- Clarify instructions, give more time to think

- Refine prompts with a batch of examples

## Inferring

In a traditional machine learning workflow, you’d have to collect data the label data set, train a model, figure out how to deploy the model somewhere in the cloud and make inferences.

This could work pretty well but it was a lot of work to go through that process.

And also, for every task, such as sentiment versus extracting names versus something else, you have to train and deploy a separate model.