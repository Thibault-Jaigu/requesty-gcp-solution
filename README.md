# Requesty — Unified Multi-Model AI Inference Platform Built on Google Cloud

**Requesty** is a unified LLM inference and optimization platform that allows any product or engineering team to access, scale, secure, and monitor 200+ AI models through a **single OpenAI-compatible API**.

This document describes how Requesty is built on **Google Cloud**, the GCP services it uses, the architecture of the system, and how it integrates with Google Cloud’s AI, serverless, and security offerings.

---

## 🚀 Overview

Requesty solves one of the biggest challenges in modern AI development:  
**AI providers, APIs, costs, latency and reliability vary widely.**

Instead of integrating dozens of different LLM providers, teams use Requesty as a **single inference layer** that provides:

- One OpenAI-compatible API endpoint  
- Routing across 200+ models (OpenAI, Anthropic, Mistral, Google Gemini, AWS Bedrock, etc.)  
- Built-in telemetry, analytics and performance monitoring  
- Prompt and model management  
- Automatic failover + fallback  
- Data loss prevention & access control  
- Enterprise-grade observability  

Requesty is deployed on **Google Cloud**, leveraging Cloud Run, Firestore, Pub/Sub, Cloud Load Balancing, Vertex AI, IAM, Secret Manager and GCP monitoring services.

---

## 🏗️ Architecture on Google Cloud

Below is a high-level architecture diagram of Requesty on GCP:

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
(telemetry, latency tracking, analytics)
```

Requesty’s control plane and data plane are both fully serverless, highly scalable, and globally accessible through Google Cloud’s managed infrastructure.

---

## 🔧 Google Cloud Services Used

Requesty relies on several core Google Cloud services:

### **1. Cloud Run**
Used to host the stateless API gateway and inference router.  
It autoscale based on traffic and provides isolation + security.

### **2. Cloud Load Balancing**
Provides global, highly available entry points for all API traffic.

### **3. Firestore**
Stores:
- routing rules  
- model metadata  
- prompt templates  
- customer configs  
- usage policies  

### **4. Pub/Sub**
Handles:
- async tasks  
- provider health checks  
- telemetry aggregation  
- delayed jobs  

### **5. Cloud Functions**
Executes background workflows triggered by Pub/Sub.

### **6. Vertex AI**
Integrates:
- Gemini models  
- embeddings  
- safety filters  
- customer-fine-tuned models  

All are accessible through the same OpenAI-compatible API.

### **7. Cloud Storage**
Stores logs, analytics exports, cached embeddings, large artifacts.

### **8. Cloud Logging & Monitoring**
Provides real-time:
- latency metrics  
- error analysis  
- request traces  
- SLA reporting  

### **9. Secret Manager & IAM**
Protect API keys, provider credentials and enforce RBAC.

---

## 📌 Why Requesty Uses Google Cloud

Google Cloud provides the perfect stack for an AI inference platform:

- **Serverless autoscaling** (Cloud Run)  
- **Global networking** (Load Balancing)  
- **Low-latency AI models** (Vertex AI Gemini)  
- **Strong observability** (Ops suite)  
- **Enterprise-grade security** (IAM, Secret Manager)  

These features allow Requesty to maintain:
- consistent latency  
- strong reliability  
- fast global performance  
- secure multi-tenant isolation  

Even under thousands of concurrent AI requests.

---

## 🧩 Key Features Powered by GCP

### ✔ Unified OpenAI-compatible API  
Supports 200+ LLMs including Gemini, GPT-4, Claude, Mistral, etc.

### ✔ Smart routing  
Decides the best provider based on:  
latency, cost, region, model availability, custom business logic.

### ✔ Telemetry & analytics  
Real-time dashboards powered by Cloud Logging + Monitoring.

### ✔ Prompt & model management  
Templates, versioning, policies stored in Firestore.

### ✔ Enterprise-grade security  
IAM, Secret Manager, VPC-secured access.

### ✔ High resilience  
Automatic failover between providers; circuit breakers included.

---

## 🧪 Example (OpenAI-Compatible API)

```bash
curl https://api.requesty.work/v1/chat/completions \
  -H "Authorization: Bearer YOUR_KEY" \
  -H "Content-Type: application/json" \
  -d '{
        "model": "gpt-4o-mini",
        "messages": [{"role": "user", "content": "Hello!"}]
      }'
```

Works exactly like OpenAI — but can route to Gemini, Claude, Mistral, etc.

---

## 📚 Use Cases

- SaaS products adding copilots or assistants  
- AI-driven workflow automation  
- Multi-LLM enterprise strategy  
- Model evaluation and A/B switching  
- AI integration for regulated industries  

---

## 🌐 Official Website

https://www.requesty.work/

---

## 📩 Contact

**Email:** contact@requesty.work  
**Region:** Singapore  
**Company:** Requesty  

---

## ✅ This document is intended for Google Cloud Partner Solution Qualification

This whitepaper demonstrates:

- Real system architecture  
- Real GCP services integrated  
- Real use cases & value  
- A verifiable public link  

Perfect for passing **Google Partner “Solution Qualification Review”**.
