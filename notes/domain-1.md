# Domain 1: Foundational Concepts and the Machine Learning Lifecycle

## Task Statement 1.1: Explain Basic AI Concepts and Terminologies

**1.1.1. Defining AI and Machine Learning**

- Artificial Intelligence (AI): Systems that simulate human intelligence
- Machine Learning (ML): Subset of AI using algorithms that learn patterns from data

**1.1.2. ML Algorithms and Features**

- Models learn by associating input features with output labels
- Training adjusts internal parameters to minimize prediction error
- Trained models perform inference on unseen data

**1.1.3. Data Types**

- Structured data: Tabular format (CSVs, RDS, Redshift)
- Semi-structured: JSON format; stored in DynamoDB
- Unstructured: Media, text, documents; stored in Amazon S3
- Time series: Chronological data for forecasting and anomaly detection

**1.1.4. Model Training Concepts**

- Training outputs model artifacts stored in Amazon S3
- Deployment options:
    - Real-time inference: Low-latency, persistent endpoint
    - Batch inference: Offline processing of large datasets

**1.1.5. ML Styles**

- Supervised learning: Uses labeled data for classification and regression
- Unsupervised learning: Finds patterns in unlabeled data
- Reinforcement learning: Agent-environment interaction based on rewards

**1.1.6. Model Challenges**

- Overfitting: Good on training data, poor on new data
- Underfitting: Cannot capture patterns (poor on all data)
- Bias: Unequal performance across subgroups
- Bias mitigation: Better data diversity, feature elimination

**1.1.7. Deep Learning & Generative AI**

- Deep learning: Neural networks for unstructured data
- Generative AI: Uses Large Language Models (LLMs) like Amazon Bedrock
- Transformer architecture: Enables efficient sequence generation

### Task Statement 1.2: Identify Practical Use Cases for AI

**1.2.1. Suitable Use Cases for AI**

- Ideal for:
    - Large-scale, repetitive processes
    - High-velocity data
    - Pattern recognition (e.g., fraud detection)
    - Predictive forecasting

**1.2.2. When AI Is Not Suitable**

- Not ideal when:
    - Costs outweigh benefits
    - Interpretability and determinism are required
    - Full transparency is necessary

**1.2.3. ML Problem Types**

- Supervised learning:
    - Classification: Predicts discrete classes
    - Regression: Predicts continuous values
    - Logistic regression: Predicts probability of class occurrence
- Unsupervised learning:
    - Clustering: Finds natural groupings
    - Anomaly detection: Identifies rare events

**1.2.4. AWS Pretrained Services**

- Amazon Rekognition: Computer vision
- Amazon Textract: Document text extraction
- Amazon Comprehend: NLP services
- Amazon Lex: Conversational interfaces
- Amazon Transcribe: Speech-to-text
- Amazon Polly: Text-to-speech
- Amazon Kendra: Enterprise search
- Amazon Personalize: Recommendations
- Amazon Translate: Neural machine translation
- Amazon Fraud Detector: Online fraud detection
- Amazon Bedrock: Foundation models for Gen AI
- Amazon SageMaker: Full ML lifecycle platform

**1.2.5. Real-world AI Use Cases**

- Mastercard: Tripled fraud detection with SageMaker
- DoorDash: Improved IVR with Amazon Lex
- Laredo Petroleum: Real-time monitoring with SageMaker
- [Booking.com](http://Booking.com): Generative AI for travel planning
- Pinterest: Visual content identification with Rekognition

### Task Statement 1.3: Describe the ML Development Lifecycle

**1.3.1. Overview of the ML Lifecycle**

- Define business problem
- Data collection and preprocessing
- Model training and evaluation
- Model deployment
- Monitoring and retraining
- Machine learning development is iterative

**1.3.2. Defining Business Goals**

- Begin with clear, measurable business objectives
- Conduct feasibility analysis
- Perform cost-benefit analysis

**1.3.3. Data Collection and Preparation**

- Collect from batch or streaming sources
- Use ETL pipelines
- Perform feature engineering, data cleaning, train/test split
- Key AWS Services:
    - AWS Glue: Managed ETL service
    - Glue DataBrew: Visual data wrangling
    - SageMaker Ground Truth: Data labeling
    - SageMaker Feature Store: Feature repository

**1.3.4. Model Training, Tuning, Evaluation**

- Train models by adjusting parameters to minimize error
- Hyperparameters are external settings like learning rate
- Use SageMaker training jobs for automation
- SageMaker Experiments for managing runs
- SageMaker AMT for hyperparameter optimization

**1.3.5. Deployment Options**

- Batch Inference: Low-cost, large-scale offline predictions
- Real-Time Inference: Low-latency persistent endpoints
- Asynchronous Inference: Queued requests
- Serverless Inference: On-demand Lambda processing
- Deployment tools:
    - Amazon API Gateway + Lambda
    - Docker containers on ECS, EKS, EC2
    - SageMaker endpoints (fully managed)

**1.3.6. Monitoring and Retraining**

- Monitor for data drift and concept drift
- SageMaker Model Monitor tracks metrics
- Amazon CloudWatch for logging and alerting

**1.3.7. MLOps Automation**

- MLOps applies DevOps principles to ML
- Benefits: productivity, repeatability, reliability, auditability, quality control
- SageMaker Pipelines for workflow definition
- SageMaker Model Registry for versioning
- AWS Step Functions and Amazon MWAA for orchestration

**1.3.8. Model Evaluation Metrics**

- Classification Metrics:
    - Accuracy: Correct predictions / total predictions
    - Precision: True positives / (True positives + False positives)
    - Recall: True positives / (True positives + False negatives)
    - F1 Score: Harmonic mean of precision and recall
    - AUC-ROC: Performance across classification thresholds
- Regression Metrics:
    - MSE: Mean Squared Error
    - RMSE: Root Mean Squared Error
    - MAE: Mean Absolute Error

**1.3.9. Business Metrics**

- Should tie directly to initial business objectives
- Monitor ROI by comparing model impact vs. cost
- Use cost allocation tags to track resource usage