# Operação — Tokyo Bot

## 🎯 Objetivo

Definir o funcionamento do Tokyo Bot dentro da arquitetura KYOTO, incluindo entrada, processamento e resposta.

---

## 🧠 Contexto

O Tokyo Bot é um agente automatizado que opera através de uma API, com orquestração via n8n e uso do Notion como base de dados.

Seu objetivo é responder interações com base em regras e um prompt estruturado.

---

## ⚙️ Estrutura

O sistema é composto por:

- API (entrada de mensagens)
- n8n (execução de regras e fluxo)
- Notion (armazenamento de dados)
- Prompt (geração de resposta)

---

## 🔄 Fluxo Operacional

1. Entrada via API  
2. n8n recebe e interpreta  
3. Consulta dados no Notion  
4. Aplica regras definidas  
5. Monta contexto para o prompt  
6. Gera resposta  
7. Retorna via API  

---

## 🧪 Uso

Exemplo de fluxo:

```bash
POST /api/message
{
  "input": "mensagem do usuário"
}
```
