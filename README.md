# 🤖 Customer Support Agent & RAG System

> An intelligent, automated customer support agent built with n8n that reads emails, understands your documents, and replies automatically using AI.

---

## 🚀 What It Does

This workflow automatically:
- 📧 **Monitors your Gmail** for incoming customer emails
- 🧠 **Uses AI (OpenAI GPT)** to understand the query
- 📚 **Searches your knowledge base** (RAG system via Pinecone) for relevant answers
- ✅ **Auto-replies** to simple queries or **creates a draft** for complex ones
- 📂 **Loads documents from Google Drive** into the vector database



## 🛠️ Built With

| Tool | Purpose |
|------|---------|
| [n8n](https://n8n.io) | Workflow automation |
| OpenAI GPT | AI language model |
| OpenAI Embeddings | Text vectorization |
| Pinecone | Vector database (knowledge base) |
| Gmail | Email trigger & response |
| Google Drive | Document source for RAG |



## ⚙️ How It Works

### 1. RAG Setup (Run Once)
```
Google Drive → Download Files → Split Text → OpenAI Embeddings → Pinecone Vector Store
```
- Searches your Google Drive for documents
- Splits them into chunks
- Converts to embeddings and stores in Pinecone

### 2. Support Agent (Runs Automatically)
```
Gmail Trigger → AI Agent → Pinecone Search → Auto Respond?
                                            ↓           ↓
                                       Send Reply   Create Draft
```
- Triggers when a new email arrives
- AI searches the knowledge base for the best answer
- If confident → sends reply automatically
- If unsure → creates a Gmail draft for human review

---

## 📋 Prerequisites

Before importing this workflow, make sure you have:

- [ ] **n8n** installed (cloud or self-hosted)
- [ ] **OpenAI API Key** (for GPT + Embeddings)
- [ ] **Pinecone Account** + API Key + Index created
- [ ] **Google Account** with Gmail & Drive access
- [ ] n8n credentials set up for: Gmail, Google Drive, OpenAI, Pinecone

---

## 📦 Installation & Setup

### Step 1: Import Workflow
1. Open your n8n instance
2. Click **"Add workflow"** → **"Import from file"**
3. Upload `Customer_Support_Agent___Rag_System__1_.json`

### Step 2: Configure Credentials
Set up the following credentials in n8n:
- **Gmail OAuth2** — for email trigger and sending
- **Google Drive OAuth2** — for document access
- **OpenAI API** — for GPT model and embeddings
- **Pinecone API** — for vector storage

### Step 3: Set Up Knowledge Base
1. Upload your support documents to **Google Drive**
2. Run the **RAG setup workflow manually** (click "Execute Workflow")
3. This loads all documents into Pinecone

### Step 4: Activate the Agent
1. Toggle the workflow to **Active**
2. The Gmail trigger will now monitor incoming emails
3. Your AI support agent is live! ✅

