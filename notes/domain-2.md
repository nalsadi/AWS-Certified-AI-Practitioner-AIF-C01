# Domain 2: Generative AI Concepts, Capabilities, and AWS Infrastructure

## Task Statement 2.1: Explain Basic Concepts of Generative AI

### 1. Definition and Purpose

- **Generative AI** is a subset of deep learning focused on creating new content (text, images, video, code) rather than classifying existing data.
- Models learn patterns from large datasets and generate outputs resembling training data.
- Unlike traditional AI (which classifies/predicts), generative AI outputs original material using statistical patterns.

### 2. Foundation Models (FMs)

- These are large, pre-trained models (e.g., LLMs like GPT, Titan) trained on diverse modalities and datasets.
- Characterized by **billions of parameters**, which enable the model to understand and generate complex outputs.
- Can be used **as-is** or **fine-tuned** for specific tasks.

### 3. Model Architecture: Transformers

- Based on the 2017 paper **"Attention is All You Need"**.
- Key innovation: **self-attention mechanism**, which weighs the importance of input tokens.
- Enables capturing long-term dependencies and parallelized computation.
- Uses **embedding vectors** and **positional encodings** to interpret sequence and context.

### 4. Core Concepts

- **Prompt**: Input to the model to generate a completion.
- **Inference**: The process of producing output given a prompt.
- **Tokens**: Subunits of input (words, characters) processed by the model.
- **Context Window**: The amount of input data the model can consider at once.
- **In-Context Learning**: Providing examples within the prompt (zero-shot, one-shot, few-shot).

### 5. Tokenizer and Embeddings

- Text is converted into token IDs using a tokenizer.
- **Embeddings** are vector representations of tokens, capturing semantic relationships.
- Similarity in embedding space implies semantic similarity.

### 6. Unimodal vs. Multimodal

- **Unimodal**: Operate on one type of data (e.g., text).
- **Multimodal**: Accept and generate multiple data types (e.g., text-to-image).
- Examples: DALL-E, Whisper, AudioLM.

## Task Statement 2.2: Describe Capabilities and Limitations for Business Problems

### 1. Capabilities

- Generative AI is a **general-purpose technology** applicable across industries.
- **Adaptability**: Can be applied to a variety of content-generation tasks.
- **Responsiveness**: Produces outputs in real time based on input prompts.
- **Simplicity**: Lowers barriers to AI application development.

### 2. Business Use Cases

- **Text generation & summarization**.
- **Content adaptation** for different audiences.
- **Information extraction**, **translation**, **recommendation engines**.
- **Chatbots**, **code generation**, **marketing**.

### 3. Limitations

- **Hallucinations**: Generation of plausible but false content.
- **Ethical Concerns**: Potential for biased, toxic, or harmful outputs.
- **Non-determinism**: Outputs vary even with the same prompt.
- **Memory**: No inherent session memory unless implemented.
- **Interpretability** vs. **Performance** tradeoff:
- Simple models are interpretable but less powerful.
- Complex models (e.g., neural networks) need **post hoc** analysis.

### 4. Evaluation Metrics

- **ROUGE**: Measures summary overlap with references.
- **BLEU**: Measures translation similarity to human examples.
- These metrics are essential for validating non-deterministic output quality.

### 5. Fine-Tuning and Human Feedback

- **Supervised fine-tuning** enhances performance for specific tasks.
- **Reinforcement Learning from Human Feedback (RLHF)** improves alignment with human values (helpfulness, honesty, harmlessness).

## Task Statement 2.3: AWS Infrastructure and Technologies for Generative AI

### 1. AWS Advantages

- **Accessibility & scalability** via managed services (SageMaker, Bedrock).
- **Security**: AWS Nitro System ensures zero access to customer data.
- **Compute optimization**: Specialized hardware like Trainium and Inferentia.

### 2. Training Strategies

- **Pre-training**: Using large datasets (internet-scale) to learn general patterns.
- **Fine-tuning**: Adapting base models to specific use cases using smaller curated datasets.
- **Transfer learning**: Leveraging existing knowledge from one model to train on new data.

### 3. AWS Services

- **SageMaker JumpStart**: Quick deployment of pretrained models, notebooks, and resources.
- **Amazon Bedrock**:
- Access multiple FMs (Titan, Cohere, Stability AI).
- Supports prompt engineering, evaluation, and deployment.
- Pricing based on **token usage**.

### 4. Security and Compliance

- Data and model protection:
- Encryption, MFA, access controls.
- Secure handling of sensitive data (PII, financials).
- Defending against AI threats: prompt injection, data poisoning, model inversion.

### 5. Project Lifecycle

- **Identify use case**
- **Experiment & select model**
- **Adapt, align, augment (prompt engineering, fine-tuning)**
- **Evaluate**
- **Deploy and iterate**
- **Monitor**

### Key Models and Architectures

- **Transformers**: Standard backbone of modern LLMs.
- **Diffusion Models**: For high-quality image/audio generation via noise reversal.
- **GANs (Generative Adversarial Networks)** and **VAEs (Variational Autoencoders)**: Used in specific image generation contexts but generally less stable than diffusion models.