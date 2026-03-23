# Check the logs of docker container
Go into the directory of the service which you want to inspect and use the below command to check for the logs
```bash
docker compose logs
```
# Initiate a docker container
To instantiate a docker container from docker compose file in detached mode
```bash
docker compose up -d
```
# Document Loaders
All the document loaders used in RAG
## TextLoader
```python
from langchain_community.document_loaders import TextLoader
loader = TextLoader("file.txt") loader.load() # to covert the txt file into Document
```
## PDFLoader
```python
from langchain_community.document_loaders import PyPDFLoader

loader = PyPDFLoader("file.pdf")
loader.load() # to covert the pdf file into Document
```
## DirectoryLoader
```python
from langchain_community.document_loaders import DirectoryLoader, PyPDFLoader

loader = DirectoryLoader(path="path", glob="*.pdf", loader_cls=PyPDFLoader)
loader.load() # to covert all the pdf files inside the directory into Document
```
## WebBaseLoader
```python
from langchain_community.document_loaders import WebBaseLoader

loader = WebBaseLoader(url)
loader.load() # to covert web based article into Document
```
## CSVLoader
```python
from langchain_community.document_loaders import CSVLoader

loader = CSVLoader("file.csv")
loader.load() # to covert csv file into Document
```
# Splitters
All the splitters used in RAG
## Python Code Text Splitter
```python
from langchain_text_splitters import PythonCodeTextSplitter

text = """
class Student:
    def __init__(self, name, age, grade):
        self.name = name
        self.age = age
        self.grade = grade   # Grade is a float (like 8.5 or 9.2)
    
    def get_details(self):
        return self.name
    
    def is_passing(self):
        return self.grade >= 6.0

# Example usage
if __name__ == '__main__':
    student1 = Student("Aarav", 20, 8.2)
    print(student1.get_details())
    
    if student1.is_passing():
        print("The student is passing.")
    else:
        print("The student is not passing.)
"""

splitter = PythonCodeTextSplitter(
    chunk_size=300,
    chunk_overlap=100
)

chunks=splitter.split_text(text)
print(chunks)
```
## Character Text Splitter
```python
from langchain_text_splitters import CharacterTextSplitter

splitter = CharacterTextSplitter(
    chunk_size=500,
    chunk_overlap=50,
    separator=""
)
```
## Recursive Character Text Splitter
```python
from langchain_text_splitters import RecursiveCharacterTextSplitter

splitter=RecursiveCharacterTextSplitter(
    chunk_size=1000,
    chunk_overlap=100
)
```
# Embeddings
HuggingFace embeddings used in creating embeddings
```python
from dotenv import load_dotenv
from langchain_huggingface import HuggingFaceEmbeddings

load_dotenv()

embeddings=HuggingFaceEmbeddings(model_name="sentence-transformers/all-MiniLM-L6-v2")

text = "New York is a busy city with a lot of population"

result = embeddings.embed_query(text)

print(result)
```
# Vector Database
To store the embeddings in the vector store for faster referencing
## Chroma
```python
from langchain_chroma import Chroma
from langchain_huggingface import HuggingFaceEmbeddings
from dotenv import load_dotenv

load_dotenv()

texts = [
    "Large language models are trained on massive datasets",
    "Large language models (LLMs) are particularly trained using transformers",
    "chroma is a lightweight vector stored used in langchain",
    "embeddings convert text into numerical representation"
]

embedding=HuggingFaceEmbeddings(
    model_name="sentence-transformers/all-MiniLM-L6-v2"
)

vectorstore=Chroma.from_texts(
    texts=texts,
    embedding=embedding,
    collection_name="langchain_chroma_demo"
)

query = "tell me more about LLMs"
results=vectorstore.similarity_search(query, k=2)

print(results)
```
## FAISS
```python
from langchain_huggingface import HuggingFaceEmbeddings
from langchain_community.vectorstores import FAISS
from dotenv import load_dotenv

load_dotenv()

cricket_texts=[
    "Cricket isn't just a game—it's patience, power, and perfect timing in one swing. 🏏",
    "One ball can change the match. One moment can create history.",
    "From dusty gullies to roaring stadiums, cricket lives in every heartbeat.",
    "Defense wins sessions, attack wins matches, but belief wins championships.",
    "When the bat meets the ball just right, the whole world pauses.",
]

embedding=HuggingFaceEmbeddings(
    model_name="sentence-transformers/all-MiniLM-L6-v2"
)

vectorstore=FAISS.from_texts(
    texts=cricket_texts,
    embedding=embedding
)

query="What can change the match?"
results = vectorstore.similarity_search(query=query, k=1)
print(results)
```
# Retrievers
All the retrievers used in RAG
## Wikipedia Retriever
```python
from langchain_community.retrievers import WikipediaRetriever

retriever = WikipediaRetriever(top_k_results=2, lang="en")

query = "Artificial Intelligence"

docs = retriever.invoke(query)
print(len(docs))

for i, doc in enumerate(docs):
    print("\n")
    print("content:\n", doc.page_content)
```
## Vector Store Retriever
```python
from langchain_community.retrievers import WikipediaRetriever

retriever = WikipediaRetriever(top_k_results=2, lang="en")

query = "Artificial Intelligence"

docs = retriever.invoke(query)
print(len(docs))

for i, doc in enumerate(docs):
    print("\n")
    print("content:\n", doc.page_content)
```
## MMR
```python
from langchain_community.vectorstores import FAISS
from langchain_huggingface import HuggingFaceEmbeddings
from langchain_core.documents import Document

documents = [
    Document(page_content="LangChain helps developers build LLM applications easily"),
    Document(page_content="Chroma is a vector database optimized for LLM based search"),
    Document(page_content="Embeddings convert text into high-dimensional vectors"),
    Document(page_content="MMR helps you get diverse results when doing similarity search."),
    Document(page_content="OpenAI provides powerful embedding models")
]

# Step 2: Initialize embedding model
embeddings=HuggingFaceEmbeddings(model_name="sentence-transformers/all-MiniLM-L6-v2")

vectorstore=FAISS.from_documents(
    documents=documents,
    embedding=embeddings
)

# build a retriever
retriever=vectorstore.as_retriever(
    search_type="mmr",
    search_kwargs={"k": 3, "lambda_mult": 0.25} # `lambda_mult` can go from 0.0 to 1.0
)

query="What is Langchain?"
results = retriever.invoke(query)
print(results)
```
# Loading the model from HuggingFace
Check for gated models. You will need to approve access to use that LLM like gemma.
```python
from transformers import AutoTokenizer, AutoModelForCausalLM

MODEL_NAME = "google/gemma-3-270m-it" # note: "it" stands for "instruction tuned" which means the model has been tuned for following instructions

model = AutoModelForCausalLM.from_pretrained(
    MODEL_NAME,
    dtype="auto",
    device_map="auto", # put the model on the GPU
    attn_implementation="eager" # could use flash_attention_2 but ran into issues... so stick with Eager for now
)
```
# Bits and Bytes Config
Bits and bytes config for 4-bit quantized model
```python
bnb_config = BitsAndBytesConfig(
   load_in_4bit=True,
   bnb_4bit_quant_type="nf4",
   bnb_4bit_use_double_quant=True,
   bnb_4bit_compute_dtype=torch.float32
)
repo_id = 'microsoft/Phi-3-mini-4k-instruct'
model = AutoModelForCausalLM.from_pretrained(
   repo_id, device_map="cuda:0", quantization_config=bnb_config
)
```
# HuggingFace GPU Runner
To run a code block on huggingface GPU
```python
import spaces

@spaces.GPU
def function_to_run_on_the_gpu():
    pass
```
# Preprocess data for the model
Every model comes with its own preprocessor
```python
from transformers import AutoProcessor, AutoModel

# Load raw data
raw_data = load_data()

# Define target model name
MODEL_NAME = "..."

# Load preprocessor and model (these two are often paired)
preprocessor = AutoProcessor.from_pretrained(MODEL_NAME)
model = AutoModel.from_pretrained(MODEL_NAME)

# Preprocess data
preprocessed_data = preprocessor.preprocess(raw_data)

# Pass preprocessed data to model
output = model(preprocessed_data)
```
