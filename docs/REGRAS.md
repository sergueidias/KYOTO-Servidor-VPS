# Regras de Documentação — Sistema KYOTO

## 🎯 Objetivo

Garantir consistência, segurança e qualidade na documentação do sistema.

---

## 📄 Uso do Template

Todo novo documento deve obrigatoriamente:

- utilizar o arquivo `docs/TEMPLATE.md`
- seguir todas as seções definidas
- não remover a seção de segurança

---

## 🔐 Segurança

É proibido incluir:

- IP real do servidor
- credenciais
- tokens
- endpoints reais
- links privados

---

## 🧠 Padrão de Escrita

Os documentos devem:

- ser claros e objetivos
- manter abstração suficiente
- evitar detalhes que permitam exploração do sistema

---

## ⚠️ Validação

Um documento é considerado inválido se:

- não seguir o template
- expor dados sensíveis
- não possuir seção de segurança

---

## 🤖 Uso por IAs

Toda IA que escrever neste repositório deve:

- seguir este documento
- tratar o conteúdo como público
- priorizar segurança sobre detalhamento

---

## 📌 Observação

Este repositório representa a versão pública do sistema.

A configuração real permanece fora deste ambiente.