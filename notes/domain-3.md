# Domain 3: Application of Foundation Models

### Overview

Domain 3 addresses how foundation models (FMs)—large, pre-trained neural networks—can be effectively integrated into applications. Unlike traditional ML models trained for narrow tasks, foundation models are **general-purpose**, adaptable, and capable of performing a variety of tasks such as:

- Natural Language Processing (NLP)
- Image classification
- Question answering
- Content generation
- Language translation
- Autonomous systems and robotics

### Task Statement 3.1: Design Considerations for Applications Using Foundation Models

### Key Design Considerations

**1. Model Selection Criteria**

- **Cost**: Training and inference are resource-intensive. Evaluate tradeoffs (e.g., 98% accuracy at high cost vs. 97% at lower cost).
- **Latency**: Real-time applications (e.g., self-driving cars) demand fast inference.
- **Modality**: Choose models trained on required modalities (text, image, audio, etc.).
- **Multilingual Capability**: Important for global applications.
- **Model Size and Complexity**: Larger models often perform better but require more compute.

**2. Performance Metrics**

- Accuracy, Precision, Recall, F1 Score
- RMSE, MAE for regression
- MAP for object detection
- Metric relevance depends on task (e.g., avoid accuracy on imbalanced datasets)

**3. Bias and Ethical Concerns**

- Evaluate training data bias
- Use tools like SageMaker Clarify for bias detection

**4. Model Availability and Compatibility**

- Ensure compatibility with tech stack (e.g., PyTorch Hub, Hugging Face)
- Check licensing, documentation, update frequency

**5. Explainability and Interpretability**

- Foundation models are **black boxes** and lack interpretability
- Simpler models (e.g., linear regression, decision trees) provide better interpretability
- Explainability can be approximated using local interpretable models

**6. Inference Parameters**

- **Temperature, Top-k, Top-p**: Control randomness and diversity
- **Length penalty, stop sequences**: Limit output
- **Amazon Bedrock** allows experimentation with these parameters via APIs

**7. Retrieval-Augmented Generation (RAG)**

- Augments model responses with external domain-specific data
- Combines **retriever** (vector DB) + **generator** (LLM)
- Helps reduce hallucinations and improves accuracy
- Vector databases (e.g., OpenSearch, Redis, Neptune, PostgreSQL with pgvector) store dense embeddings

**8. Agents in Multi-Step Tasks**

- Agents can orchestrate workflows (e.g., booking a trip, accessing APIs)
- Amazon Bedrock Agents auto-generate orchestration logic and access external data

### Task Statement 3.2: Prompt Engineering Techniques

**Prompt Engineering Basics**

- **Prompt** = Instruction + context + input
- Used to steer LLMs toward desired outputs

**Types of Prompting**

- **1. Zero-shot**: No examples; model infers from instruction alone
- **2. Few-shot**: Includes a few labeled examples
- **3. Chain-of-thought**: Breaks down reasoning steps for better output
- **4. Prompt Tuning**: Learns continuous embeddings; more efficient than full fine-tuning

**Prompt Engineering Techniques**

- Be **specific** and **clear**
- Include format/style/tone guidelines
- Add **guardrails** (e.g., filtering, injection protection)
- Use **prompt templates**
- Conduct **iterative testing** to refine prompts
- Understand the model's **latent space**:
    - Prompts are interpreted statistically from learned patterns
    - Incomplete or poorly scoped prompts may result in hallucinations
    - If a model lacks latent knowledge, output may be factually incorrect but statistically valid

**Prompt Engineering Risks**

- **Prompt Injection**: Malicious modification of prompts
- **Jailbreaking**: Circumventing safety guardrails
- **Hijacking**: Modifying original prompt intent
- **Poisoning**: Embedding malicious instructions into data

**Tools**

- Amazon Bedrock and Amazon Titan support prompt engineering and provide tools to monitor responses

### Task Statement 3.3: Training and Fine-Tuning Foundation Models

**Training Components**

**1. Pre-training**

- Done on large unstructured datasets using **self-supervised learning**
- Very resource-intensive (petabytes of data, trillions of tokens)

**2. Fine-tuning**

- Supervised learning with domain/task-specific labeled data
- Updates model weights for specific tasks
- Risk: **Catastrophic Forgetting** (loss of performance on general tasks)

**3. Parameter-Efficient Fine-Tuning (PEFT)**

- Updates small subset of parameters (e.g., LoRA)
- Preserves original weights
- Efficient for domain adaptation

**4. Representation Fine-Tuning (ReFT)**

- Modifies hidden representations rather than full weights

**5. Multi-task Fine-Tuning**

- Trains model on multiple tasks at once
- Mitigates catastrophic forgetting

**6. Domain Adaptation**

- Fine-tunes models with domain-specific data (technical, legal, medical, etc.)

**7. Reinforcement Learning from Human Feedback (RLHF)**

- Fine-tuning model behavior using human evaluation signals

**Data Preparation**

- Use **instruction datasets**, then split into train/validation/test sets
- Use **Amazon SageMaker** tools for:
    - **Data labeling**: Ground Truth
    - **Bias detection**: Clarify
    - **Feature engineering**: Feature Store
    - **Pre-processing**: Glue, EMR, SQL, or low-code (Canvas)

### Task Statement 3.4: Evaluating Foundation Model Performance

**Challenges**

- Generative AI models are **non-deterministic**
- Evaluations must go beyond traditional metrics (accuracy, RMSE)

**Metrics and Benchmarks**

- **BLEU**: For translation
- **ROUGE**: For summarization
- **BERTScore**: Semantic similarity (used in Amazon Bedrock)
- **GLUE/SuperGLUE**: For general language tasks
- **MMLU**: Multidisciplinary knowledge evaluation
- **BIG-bench**: Advanced reasoning and diverse domain coverage
- **HELM**: Transparency and model comparison

**Human Evaluation**

- Manual reviews of model responses
- Comparative assessments across providers

**AWS Tools for Evaluation**

- **Amazon SageMaker Clarify**: Evaluate models and detect bias
- **Amazon Bedrock Evaluation Module**: Automatically compute similarity scores (e.g., BERTScore)

**Deployment Considerations**

- **Inference Speed vs. Performance**: Tradeoff
- **Prompt length, snippet size**: Can affect latency and performance
- **Stack Design**:
    - Infrastructure (compute, storage, networking)
    - Model + fine-tuning + embeddings
    - Application interfaces (UI or REST APIs)
    - Security (for inference and storage)
    - Monitoring (to collect completions/feedback for continuous improvement)