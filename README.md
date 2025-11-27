# Requesty — Unified Multi-Model AI Inference Platform Built on Google Cloud

**Requesty** is a unified LLM inference and optimization platform that enables any product or engineering team to access, scale, secure, and monitor 200+ AI models through a **single OpenAI-compatible API**.

This document explains how Requesty is deployed on **Google Cloud**, the GCP services it uses, the architecture of the system, and how it integrates with Google Cloud’s AI, serverless, and security offerings.

---

## 🚀 Overview

Modern AI development faces a major challenge:  
**AI providers, APIs, latency, cost, and reliability vary drastically.**

Requesty solves this by acting as a **single inference layer**, offering:

- One OpenAI-compatible API endpoint  
- Routing across 200+ models (OpenAI, Anthropic, Google Gemini, Mistral, AWS Bedrock, etc.)  
- Built-in telemetry, analytics, and performance monitoring  
- Prompt and model management  
- Automatic failover + fallback  
- Data loss protection  
- Multi-tenant security  
- Enterprise-grade observability  

Requesty is deployed on **Google Cloud**, using Cloud Run, Firestore, Pub/Sub, Cloud Load Balancing, Vertex AI, Secret Manager, IAM, Cloud Logging, and Cloud Monitoring.

---

## 🏗️ Architecture on Google Cloud

Below is a high-level architecture diagram:

```
Client Applications / Services
            │
            ▼
   Google Cloud Load Balancer
            │
            ▼
   Cloud Run — Requesty API Gateway
            │
 ┌──────────┼────────────────────────────────────────┐
 │          │                                        │
 ▼          ▼                                        ▼
Firestore   Pub/Sub (async jobs)            Vertex AI Models
(configs,   model health checks,            embeddings, tuning,
routing     background workers)             safety filters
rules)
 │
 ▼
Cloud Logging / Cloud Monitoring
(telemetry, latency, analytics)
```

Requesty’s control plane and inference router both run fully serverless on GCP, ensuring high scalability, global reliability, and strong security isolation.

---

## 🔧 Google Cloud Services Used

### **1. Cloud Run**
Hosts the stateless API gateway and inference routing engine.  
Autoscaling ensures predictable performance under any load.

### **2. Cloud Load Balancing**
Provides global routing and efficient distribution of API traffic.

### **3. Firestore**
Stores:
- model metadata  
- routing policies  
- prompt templates  
- customer configurations  
- usage policies  

### **4. Pub/Sub**
Handles:
- async jobs  
- provider health checks  
- telemetry batching  
- background tasks  

### **5. Cloud Functions**
Executes asynchronous workflows triggered by Pub/Sub.

### **6. Vertex AI**
Used for:
- Gemini models  
- embeddings  
- safety filters  
- customer-tuned models  

Accessible through the same OpenAI-compatible API.

### **7. Cloud Storage**
Stores logs, model evaluation output, cached embeddings, and large artifacts.

### **8. Cloud Logging & Monitoring**
Provides real-time:
- latency metrics  
- request traces  
- error diagnostics  
- dashboards & alerts  

### **9. Secret Manager & IAM**
Manages credentials and enforces multi-tenant access security.

---

## 📌 Why Requesty Uses Google Cloud

Google Cloud offers the ideal infrastructure for large-scale AI inference:

- **Serverless autoscaling** via Cloud Run  
- **High reliability & low latency** through Google’s global network  
- **Native AI with Gemini models**  
- **Strong observability** through Cloud Logging / Monitoring  
- **Enterprise-level security** via IAM and Secret Manager  
- **Scalable storage and messaging** through Firestore, Pub/Sub, and Cloud Storage  

This allows Requesty to maintain:
- consistent latency  
- high reliability  
- globally distributed workloads  
- secure isolation across tenants  

---

## 🧩 Key Features Enabled by GCP

### ✔ Unified OpenAI-Compatible API  
Supports 200+ LLMs including:  
Gemini, GPT-4, Claude, Mistral, Llama, Bedrock models, and more.

### ✔ Intelligent Model Routing  
Automatically selects the best provider based on:
- latency  
- cost  
- availability  
- workload patterns  
- dynamic failover  

### ✔ Analytics & Telemetry  
Powered by Cloud Logging & Monitoring for real-time insights.

### ✔ Prompt & Model Management  
Policies, templates, versions stored in Firestore.

### ✔ High Resilience  
Built-in fallbacks, retries, circuit breakers, and regional redundancy.

---

## 🧪 Example (OpenAI-Compatible API Request)

```bash
curl https://api.requesty.work/v1/chat/completions \
  -H "Authorization: Bearer YOUR_KEY" \
  -H "Content-Type: application/json" \
  -d '{
        "model": "gpt-4o-mini",
        "messages": [{"role": "user", "content": "Hello!"}]
      }'
```

Request behaves exactly like OpenAI, while transparently routing traffic across multiple LLM providers.

---

## 📚 Use Cases

- SaaS copilots and assistants  
- Automated workflows  
- AI research and evaluation  
- Enterprise multi-LLM strategies  
- Regulated industries requiring data protection  
- Cost-optimized AI inference  

---

## 🌐 Official Website

https://www.requesty.work/

---

## 📩 Contact

**Email:** contact@requesty.work  
**Region:** Singapore  
**Company:** Requesty  

---

## ✅ Purpose of This Document

This document is intended for **Google Cloud Partner Solution Qualification**, demonstrating:

- Real system architecture  
- Actual Google Cloud service usage  
- Clear technical integration  
- Publicly accessible documentation  

This meets Google’s expectations for a valid, production-ready solution.
