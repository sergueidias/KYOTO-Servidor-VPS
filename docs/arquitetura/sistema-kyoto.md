# Arquitetura do Sistema KYOTO

## 🎯 Objetivo

Definir a estrutura geral do sistema KYOTO, seus componentes e relações.

---

## 🧠 Contexto

O sistema KYOTO é uma arquitetura de automação baseada em:

- servidor VPS
- orquestração via n8n
- integração com agentes (Tokyo Bot)
- armazenamento e controle de dados

Seu objetivo é operar fluxos automatizados com controle, segurança e escalabilidade.

---

## ⚙️ Estrutura Geral

O sistema é dividido em 4 camadas:

### 1. Infraestrutura

- VPS
- Docker
- rede e acesso

---

### 2. Orquestração

- n8n
- fluxos automatizados
- execução de lógica

---

### 3. Inteligência

- agentes (Tokyo Bot)
- regras de decisão
- interpretação de dados

---

### 4. Interfaces

- APIs
- webhooks
- entradas externas (usuários, sistemas)

---

## 🔄 Fluxo Operacional

1. Entrada via API ou mensagem  
2. Processamento no n8n  
3. Aplicação de lógica (bot / regras)  
4. Persistência ou resposta  

---

## 🧪 Uso

Este documento serve como referência para:

- criação de novos fluxos
- integração de novos agentes
- documentação de novos módulos

---

## 🔐 Segurança

### Princípios

- separação entre público e sensível
- uso de variáveis de ambiente
- isolamento por container

---

### Proibições

Nunca documentar:

- endpoints reais
- credenciais
- IP do servidor
- acessos diretos

---

## 📦 Variáveis de Ambiente (exemplo)

```env
SYSTEM_MODE=production
```
