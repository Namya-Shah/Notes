# Terms
## Fine-tuning
- A form of transfer learning where you take the patterns from one neural network and adjust them to suit your own data source (in our case, food images).
## Epochs
- The number of times your model goes over the entire dataset (in our case, 50 epochs means 50 iterations on the whole dataset of ~280,000 images).
## GCP
- Google Cloud Platform
## Weights & Biases (wandb)
- Machine learning tooling platform (experiment tracking, data tracking, model tracking + more).
## Model artifact
- model tracking/storage (so you know which model out of 1000+ experiments is the best to use).
## Dataset artifact
- Dataset tracking/storage (so you know which dataset was used to train which model).
## Production datasets
- also get changed over time as more data/new data gets added to the system. Our data is stored on Google Storage (a big folder of food images + annotations file) and versions are tracked with Weights & Biases.
## Dimensionality issue (one of the biggest issue in ML)
- An operation you tried to perform between two tensors doesn't work because of incompatible shapes.
	- For example your first tensor has a shape of [1,1,128] but your second tensor has a shape of [1,1,256]. The third dimension doesn't line up.
	- Or you're trying to perform an operation on a dimension that doesn't exist (the case above).
## Loss 
- Measure of how "wrong" your model is. A perfect model will have a loss value of 0. A loss curve should trend downwards during training.
## Accuracy 
- A measure of how many samples a model gets correct (e.g. an accuracy of 0.89 means the model gets ~89/100 samples correct). An accuracy curve should trend upwards.
## Named Entity Recognition (NER) 
- Extracting a target entity type from a series of text. For example, "Brisbane, Australia" -> Location.
## Test most wrong predictions
- Examples in the test dataset where the model was really confident (e.g., high prediction probability) but the prediction was wrong when compared to the ground truth. Inspecting these samples can give a good indication of potential data mistakes/samples where the model finds difficult.

# Generative AI
- ## Agentic Systems
	- AI that automates workflows and decision-making independently.
- ## Alignment
	- Train AI to align with your organization's values for ethical outcomes.
	- Ensure AI outputs align with brand integrity & policies
- ## Black Box Models
	- Trust explainable AI (XAI) for transparency.
	- Crucial for compliance in finance, healthcare & legal sectors.
- ## Context Window
	- Optimize AI's ability to analyze deep data inputs.
- ## Distillation
	- Use fast, efficient AI models for quick responses.
	- Deploy in real-time customer service for cost savings.
- ## Embeddings & Vector Databases
	- Contextual AI for better data retrieval
	- Improve analytics and personalized recommendations
- ## Fine-Tuning
	- Customize AI to suit your business-specific use cases.
	- Increase precision in marketing campaigns & product development.
- ## Foundation Models & LLMs
	- Scale versatile models like GPT-4 across use cases.
	- From content creation to workflow automation
- ## Grounding
	- Provide real-world context for accurate AI responses
	- Improve accuracy in customer support & technical documentation
- ## Human in the Loop (HITL)
	- Balance AI outputs with human oversight.
	- Use for quality control in content & compliance outputs.
- ## Inference & Cost Management
	- Monitor usage for scalable, affordable AI
	- Choose open-source models for cost-effective scaling.
- ## Jailbreaking & Security
	- Secure AI against unauthorized access
	- Prevent data breaches by updating models regularly
- ## Multimodal AI
	- Combine text, voice, and images for deeper insights.
	- Enhance user experience across various data types.
- ## Prompt Engineering
	- Guide AI for accurate, business-focused results.
	- Improve AI accuracy through effective prompt crafting.
# LLM Dictionary
- ## Model Weights
	- Parameters learned during training
		- Define how the model processes input
		- Fine-tuning adjusts weights for specific tasks
		- Pretrained weights acts as a foundation
	- ![[WhatsApp Image 2025-02-21 at 09.16.35.jpeg]]
- ## Noise Handling
	- Addressing noisy or low-quality data in fine-tuning
		- Improves the model's ability to generalize
		- Requires robust preprocessing pipelines
		- Common in messy, real-world datasets.
	- ![[WhatsApp Image 2025-02-21 at 09.18.05.jpeg]]
- ## Optimization
	- The process of improving model performance.
		- Involves methods like Adam or SGD.
		- Essential for faster convergence in fine-tuning
		- Balances trade-offs between accuracy and efficiency.
	- ![[WhatsApp Image 2025-02-21 at 09.18.05 (1).jpeg]]
- ## Pretraining
	- Training on large datasets before fine-tuning
		- Provides general knowledge to the model.
		- Reduces data requirements for fine-tuning.
		- Speeds up task-specific adaptation.
	- ![[WhatsApp Image 2025-02-21 at 09.18.06 1.jpeg]]
- ## Quality Evaluation
	- Measuring performance with metrics like BLEU, ROUGE, or accuracy.
		- Validates the effectiveness of fine-tuning
		- Guides iterative improvements.
		- Helps identify issues like overfitting.
	- ![[WhatsApp Image 2025-02-21 at 09.31.58.jpeg]]
- ## Regularization
	- Techniques to prevent overfitting
		- Includes dropout, weight decay, or early stopping.
		- Improves generalization on unseen data
		- Key for robust fine-tuned models.
	- ![[WhatsApp Image 2025-02-21 at 09.31.59.jpeg]]
- ## Supervised Fine-Tuning
	- Using labeled data to teach specific tasks.
		- Boosts performance in welldefined use cases.
		- Requires high-quality annotations
		- Common in domain-specific applications.
	- ![[WhatsApp Image 2025-02-21 at 09.31.59 1.jpeg]]
- ## Tokenization
	- Splitting text into smaller units (tokens).
		- Prepares data for model consumption.
		- Handles variations like punctuation and casing.
		- Fundamental for both training and inference.
	- ![[WhatsApp Image 2025-02-21 at 09.31.59 2.jpeg]]
- ## Underfitting
	- A model failing to capture data patterns
		- Often due to insufficient training
		- Addressed by increasing complexity or data size
		- Opposite of overfitting
	- ![[WhatsApp Image 2025-02-21 at 09.32.00.jpeg]]
- ## Validation Set
	- Dataset used to monitor training performance.
		- Helps prevent overfitting during fine-tuning.
		- Guides decisions on hyperparameter tuning.
		- Ensures the model generalizes well.
	- ![[WhatsApp Image 2025-02-21 at 09.32.00 1.jpeg]]
- ## Warm-Start
	- Initializes retrieval systems with pre-trained embeddings or models.
		- Speeds up convergence and improves early-stage performance.
		- Reduces training time for new tasks.
		- Common in transfer learning scenarios.
	- ![[WhatsApp Image 2025-02-21 at 09.32.00 (1).jpeg]]
- ## Explainability
	- Understanding model predictions
		- Essential for building trust in AI systems.
		- Identifies biases or issues in fine-tuned outputs.
		- Key for high-stakes applications like healthcare.
	- ![[WhatsApp Image 2025-02-21 at 09.32.01.jpeg]]
- ## Yield Optimization
	- Maximizing output relevance and efficiency
		- Improves response quality for fine-tuned models.
		- Involves iterative adjustments and monitoring.
		- Enhances user satisfaction in real-world use.
	- ![[WhatsApp Image 2025-02-21 at 09.32.01 (1).jpeg]]
- ## Zero-Shot Learning
	- Performing tasks without task specific fine-tuning.
		- Leverages general knowledge from pretraining.
		- Useful for quick adaptation to new domains.
		- A hallmark of advanced LLMs.
	- ![[WhatsApp Image 2025-02-21 at 09.32.01 (2).jpeg]]