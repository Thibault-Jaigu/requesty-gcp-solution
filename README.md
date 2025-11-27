# Requesty – Unified Multi-Model AI Inference Platform Built on Google Cloud

**Requesty** is a unified LLM inference and optimization platform that enables any product or engineering team to access 200+ AI models through a **single OpenAI-compatible API**.

This document describes how Requesty is built on **Google Cloud**, the GCP services it uses, its architecture, security posture, and how the platform integrates with Google technologies.

---

## 🚀 Overview

Requesty solves one of the biggest challenges in modern AI development:  
**AI providers, APIs, costs, latency, quality, and reliability vary widely.**

Instead of integrating dozens of different LLM providers independently, teams use Requesty as a **single inference layer**.

Key capabilities:

- One OpenAI-compatible API endpoint  
- Routing across 200+ models (OpenAI, Anthropic, Mistral, Google Gemini, AWS Bedrock, etc.)  
- Built-in telemetry, analytics & performance monitoring  
- Prompt and model management  
- Automatic failover + fallback  
- Data loss prevention & access control  
- Enterprise-grade observability  
- Multi-provider load balancing and optimization  

---

## 🏗 Architecture on Google Cloud

Requesty runs fully on **Google Cloud**, leveraging:

- **Cloud Run** for stateless inference routing  
- **Firestore** for metadata, logs, routing configs and usage tracking  
- **Pub/Sub** for asynchronous analytics and large batch processing  
- **Cloud Load Balancing** to serve global traffic with low latency  
- **VPC + Serverless VPC Access** for network isolation and security  
- **IAM** for identity and permission control  
- **Secret Manager** for provider API keys and internal credentials  
- **Cloud Logging & Monitoring** for observability and audit trails  

This architecture provides reliability, autoscaling, strong security boundaries and cost-efficient AI routing.

---

## 🔒 Security, Compliance & Reliability

Requesty follows strong security and operational practices:

- Identity-based access control via Google IAM  
- API keys and sensitive credentials stored in Secret Manager  
- VPC isolation for internal components  
- Full encryption at-rest and in-transit  
- Cloud Logging for auditability and compliance  
- Automatic regional failover and multi-provider fallback  
- No customer data stored unless explicitly configured  

---

## 🧩 Integration With Google Cloud

Requesty integrates deeply with Google Cloud services:

- **Cloud Run** hosts the routing engine and inference orchestrator  
- **Firestore** stores internal metadata, configs and audit information  
- **Pub/Sub** is used for asynchronous tasks and telemetry pipelines  
- **Load Balancer + CDN** ensure fast responses worldwide  
- **IAM + VPC** ensure strict access control  
- Requesty provides native access to **Google Gemini** models through the unified API  

This design enables scalable, secure, and globally distributed AI workloads.

---

## 🌐 Company Information (United States)

**Company Name:** Requesty  
**Legal Entity:** Requesty Inc.  
**Region / Headquarters:** United States  
**Location:** San Francisco, California, USA  
**Industry:** AI Infrastructure / Developer Tools  
**Website:** https://www.requesty.work  
**Email:** contact@requesty.work  

Requesty Inc. is a U.S.-based AI infrastructure company focused on providing a unified multi-model inference layer for developers and enterprises. The platform offers OpenAI-compatible APIs, multi-provider orchestration, telemetry, analytics, performance optimization, and enterprise-grade reliability—built on top of Google Cloud.

---

## 🔗 Solution Link (for Google Review)

Public GitHub Repository (recommended by Google):  
https://github.com/Thibault-Jaigu/requesty-gcp-solution

---

