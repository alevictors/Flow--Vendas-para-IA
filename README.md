# Automação de Vendas com Inteligência Artificial 🤖

Projeto demonstrativo de uma arquitetura de atendimento e vendas automatizadas utilizando **Inteligência Artificial, APIs, integração de sistemas e automação de processos**.

A solução foi estruturada para conectar uma plataforma de atendimento à **OpenAI Responses API**, permitindo conversas contextualizadas, consulta a bases de conhecimento, respostas estruturadas e direcionamento automático da jornada do cliente.

> Este repositório apresenta uma versão demonstrativa e anonimizada da arquitetura. Dados reais, credenciais, tokens, URLs comerciais, informações de clientes e configurações internas não são disponibilizados.

---

## 🎯 Objetivo

O projeto tem como objetivo demonstrar a aplicação prática de Inteligência Artificial em uma jornada comercial automatizada, permitindo:

- Atendimento automatizado com IA;
- Interpretação da intenção do cliente;
- Manutenção do contexto da conversa;
- Consulta a bases de conhecimento;
- Automação de processos comerciais;
- Integração entre sistemas por API;
- Roteamento de diferentes tipos de mensagens;
- Direcionamento para atendimento humano quando necessário;
- Utilização de mensagens interativas para apoiar a conversão;
- Tratamento estruturado das respostas produzidas pela IA.

---

## 🧠 Inteligência Artificial

A solução utiliza o modelo:

**GPT-5.1**

integrado através da:

**OpenAI Responses API**

O modelo recebe instruções específicas de atendimento e utiliza informações recuperadas de uma base de conhecimento para responder ao cliente de maneira contextualizada.

---

## 🔎 Base de Conhecimento e RAG

O projeto utiliza:

**Vector Store + File Search**

para permitir que a Inteligência Artificial consulte informações previamente armazenadas antes de responder determinadas perguntas.

Esse modelo permite trabalhar com uma arquitetura baseada em **RAG — Retrieval-Augmented Generation**, combinando geração de linguagem com recuperação de informações.

Fluxo simplificado:

Cliente  
↓  
Mensagem recebida  
↓  
OpenAI Responses API  
↓  
File Search  
↓  
Vector Store  
↓  
Base de conhecimento  
↓  
Resposta contextualizada

---

## 🔄 Arquitetura do Projeto

```mermaid
flowchart TD

A[Cliente] --> B[Plataforma ASC]

B --> C[Identificação da mensagem]

C --> D[Controle de contexto]
D --> E[Conversation ID]

E --> F[Prompt de Vendas]

F --> G[OpenAI Responses API]

G --> H[GPT-5.1]

H --> I[File Search]
I --> J[Vector Store]

J --> H

H --> K[Structured Output]

K --> L[Mensagem]
K --> M[Trigger]
K --> N[Tag]
K --> O[End Conversation]

L --> P{Tipo de mensagem}

P -->|Texto| Q[Mensagem de Texto]
P -->|Áudio| R[ElevenLabs]
P -->|Imagem| S[Imagem]
P -->|PDF| T[Documento]

M --> U{Decisão}

U -->|Atendimento Humano| V[Transferência]
U -->|Finalizar| W[Encerramento]
U -->|Continuar| X[Aguardar próxima interação]
