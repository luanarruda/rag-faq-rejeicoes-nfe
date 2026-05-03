# 🚀 RAG FAQ - Rejeições NF-e
RAG aplicado ao suporte de ERP: consulta inteligente de rejeições de NF-e utilizando IA.

Este projeto utiliza busca vetorial e geração de respostas para auxiliar na resolução de erros fiscais recorrentes, reduzindo a dependência de suporte humano.

---

## 🧠 Visão Geral
O sistema implementa o conceito de **RAG (Retrieval-Augmented Generation)** para responder dúvidas sobre rejeições de NF-e/NFC-e.

### 🔄 Fluxo
1. Usuário envia uma pergunta  
2. A pergunta é convertida em embedding  
3. O sistema busca conteúdos relevantes no banco vetorial  
4. A IA gera uma resposta baseada no contexto encontrado  

---

## 🏗️ Arquitetura
Usuário → n8n (Webhook) → OpenAI (Embedding) → MongoDB (Vector Search) → OpenAI (Resposta) → Usuário

---

## ⚙️ Tecnologias Utilizadas

- n8n (orquestração de workflows)  
- OpenAI (embeddings + geração de resposta)  
- MongoDB Atlas (vector search)  
- Docker (ambiente de execução)  

---

## 📂 Estrutura do Projeto
rag-faq-rejeicoes-nfe/
├── workflows/
│ ├── FaqRagQuery.json
│ └── KbIndexingPipeline.json
├── .gitignore
└── README.md

---

## 🔄 Workflows

### 📌 FaqRagQuery.json

Responsável por:

- Receber pergunta via webhook  
- Gerar embedding da pergunta  
- Buscar contexto relevante no MongoDB  
- Gerar resposta com IA  

---

### 📌 KbIndexingPipeline.json

Responsável por:

- Processar base de conhecimento  
- Gerar embeddings  
- Armazenar dados no MongoDB  

---

## 🔐 Segurança

As credenciais **não estão incluídas** neste repositório.

Para execução local, é necessário configurar manualmente no n8n:

- OpenAI API Key  
- MongoDB Connection String  

---

## 🚀 Como executar

### 1. Subir o n8n com Docker

```
bash
docker run -it --rm \
  -p 5678:5678 \
  n8nio/n8n
 ```

### 2. Importar os workflows

No n8n:

Vá em Import
Selecione os arquivos da pasta workflows/

### 3. Configurar credenciais

Criar no n8n:

OpenAI API
MongoDB

### 4. Executar
Ativar o workflow
Fazer requisição para o webhook

---

### 🎯 Objetivo do Projeto
- Reduzir chamados repetitivos no suporte de ERP
- Padronizar respostas para erros fiscais
