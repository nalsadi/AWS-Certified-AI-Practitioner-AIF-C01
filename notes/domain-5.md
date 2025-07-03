# Domain 5: Securing AI Systems & Ensuring Governance and Compliance

### Task 5.1: Methods to Secure AI Systems

**1. Shared Responsibility Model**

- **Security *of* the cloud (AWS)**: Includes physical infrastructure, data centers, networking, and hardware.
- **Security *in* the cloud (Customer)**: Customers configure security of applications and data using encryption, access controls, and IAM.
- Responsibility depends on the AWS service:
    - **EC2**: Full control over OS, patching, scaling.
    - **SageMaker Serverless**: AWS manages infrastructure; minimal customer responsibility.

**2. IAM (Identity and Access Management)**

- Manages **user access** and **permissions**.
- Key practices:
    - Create **individual IAM users**.
    - Use **least privilege** access policies.
    - Enable **MFA** (multi-factor authentication).
    - Avoid using the **root user**; reserve for essential tasks.
- IAM roles provide **temporary credentials** to reduce risk of compromised long-lived credentials.
- IAM groups ease permission management by job function.

**3. IAM Policy Types**

- **Identity-based policies**: Attached to users, groups, or roles.
- **Resource-based policies**: Applied directly to AWS resources (e.g., S3 buckets).
- **Permissions are additive**, but explicit deny overrides any allow.

**4. IAM Identity Center (formerly AWS SSO)**

- Supports **identity federation** from external identity providers (e.g., Active Directory).
- Enables **centralized permission management** across multiple accounts.
- Issues **temporary credentials**, preferred over long-lived IAM credentials.

**5. Logging & Monitoring**

- **AWS CloudTrail**: Logs all API activity; essential for auditing.
- Integrated with **SageMaker**, except for endpoint invocations.
- **Amazon Macie**: Detects PII in S3 buckets using ML.

**6. Encryption**

- **At rest and in transit**: Available across all AWS services.
- **Client-side vs. Server-side encryption**:
    - Server-side is simpler and more consistent.
    - Some services (e.g., S3, DynamoDB, SageMaker) offer **default encryption**.
- **AWS KMS (Key Management Service)**: Used for managing encryption keys; supports customer-managed keys for more control.

**7. VPC and Network Isolation**

- SageMaker resources run in **SageMaker-managed VPCs** by default.
- Best practice: Launch into **customer-managed VPCs** to control outbound/inbound traffic.
- Use **VPC Interface Endpoints** and **PrivateLink** to ensure private access to services.

**8. AI-Specific Threats**

- **Poisoning Attacks**: Tampering with training data to mislead the model.
- **Adversarial Inputs**: Slight input changes to induce misclassification.
- **Model Inversion**: Reconstructing training data from outputs.
- **Prompt Injection**: Especially in LLMs, attackers manipulate the input prompt to change behavior.

**9. Mitigation Strategies**

- **Encrypt artifacts** and use **access control**.
- **Validate user input** for anomalies.
- **Train with adversarial data**.
- **Monitor for model drift** using:
    - **Amazon SageMaker Model Monitor**: Captures input/output, tracks data quality and model drift.
    - Integrated with **CloudWatch** for alerts.

**10. Model Governance**

- **Tracking and versioning** is key to reproducibility and compliance.
- Tools:
    - **SageMaker Model Registry**: Stores model versions and metadata.
    - **Model Cards**: Document model usage, training, risks.
    - **Lineage Tracking**: Visual graph of workflows and artifacts.
    - **Feature Store**: Centralized store of features with support for point-in-time queries.
    - **Model Dashboard**: Centralized monitoring and compliance reporting.

### Task 5.2: Governance and Compliance Regulations for AI Systems

**1. AWS Shared Responsibility in Compliance**

- AWS is responsible for **infrastructure compliance**.
- Customers are responsible for **workload-level compliance**.
- **AWS Artifact**: Provides **third-party audit reports** for compliance (SOC, ISO, etc.).

**2. AI-Specific Compliance Standards**

- **ISO/IEC 42001:2023** and **ISO/IEC 23894:2023**:
    - Provide AI risk management frameworks.
    - Encourage global interoperability and responsible AI practices.
- **EU AI Act**:
    - Classifies AI systems into 3 risk levels: **Unacceptable**, **High-risk**, and **Low-risk**.
    - High-risk systems (e.g., job applicant ranking) must implement **risk management**, **data governance**, and **transparency**.

**3. NIST AI Risk Management Framework (AI RMF)**

- Defines **Govern, Map, Measure, and Manage** functions.
- Risk = **Likelihood × Severity**.
- Encourages organizations to:
    - Identify use cases.
    - Determine inherent vs. residual risk.
    - Address bias, explainability, and trust.

**4. Algorithmic Accountability & Bias**

- **Algorithmic Accountability Act** (U.S., proposed):
    - Promotes transparency and consumer rights.
- **Explainability**:
    - Needed to justify decisions (e.g., loan rejections).
    - **Model-agnostic tools** and interpretable models (e.g., decision trees) can aid transparency.
- **Bias Monitoring**:
    - **SageMaker Clarify** identifies bias in training data and predictions.

**5. Compliance Support Tools**

- **AWS Audit Manager**:
    - Maps compliance frameworks to AWS data.
    - Generates audit-ready reports.
- **Amazon Bedrock Guardrails**:
    - Filters harmful content (hate, violence, etc.).
    - Blocks or redacts **PII** and restricted topics.
- **AWS Config**:
    - Tracks configuration changes.
    - **Conformance packs** automate compliance rules and remediation.
- **Amazon Inspector**:
    - Scans applications for vulnerabilities.
- **AWS Trusted Advisor**:
    - Provides checks for cost, security, performance, and compliance.

**6. Data Governance**

- Encompasses:
    - **Curation**: Managing and profiling key data assets.
    - **Discovery**: Making data findable and understandable.
    - **Protection**: Balancing access with privacy/security.
- Key Roles:
    - **Data Owner**: Executive making policy decisions.
    - **Data Steward**: Business-level executor of data policies.
    - **IT**: Manages governance tooling.

**7. AWS Data Governance Services**

- **Glue DataBrew**:
    - Visual tool for **data profiling** and **lineage**.
- **Glue Data Catalog**:
    - Stores metadata schemas.
    - **Glue Crawler**: Automates metadata population.
- **Glue Data Quality**:
    - Provides rule-based and ML-driven data quality checks.
- **Lake Formation**:
    - Manages fine-grained access to S3-based data lakes.
    - Supports **column, row, and cell-level permissions**.

**8. Lifecycle Management & Storage**

- **Amazon S3 Classes**:
    - **Standard**: Frequent access.
    - **Intelligent-Tiering**: Unknown patterns.
    - **Glacier**: Archival storage.
- **Lifecycle rules**: Automate data transition and deletion based on retention needs.

**9. AI Governance Strategy**

- Use the **Generative AI Security Scoping Matrix** to determine responsibility levels.
- Scopes 1–2: Use third-party tools, minimal responsibility.
- Scopes 3–5: Build custom models, greater governance responsibility.
- Key actions:
    - Classify data and models.
    - Implement threat modeling and security controls.
    - Monitor models for bias, drift, and performance.
    - Train employees and define documentation standards.