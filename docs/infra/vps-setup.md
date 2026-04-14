# Servidor VPS — Configuração e Acesso

## 🎯 Visão Geral

O servidor VPS é o núcleo da operação KYOTO, responsável por:

- hospedar serviços de automação
- executar fluxos do n8n
- intermediar integrações externas
- sustentar a lógica operacional do sistema

Este documento descreve a estrutura de forma segura e replicável, sem expor dados sensíveis.

---

## 🔐 Acesso ao Servidor

O acesso é realizado via SSH.

```bash
ssh USER@SERVER_IP -p PORT

Requisitos:
chave SSH configurada
usuário com permissões adequadas
porta definida no servidor

⚠️ Nunca expor:

IP real
usuário root
porta real
🧱 Estrutura do Ambiente

O servidor opera com os seguintes componentes principais:

Docker
Containers de serviços
Gerenciador de processos
Organização geral:
/opt/
  /services
  /data
  /logs
⚙️ Serviços Principais
Automação (n8n)

Responsável por:

orquestração de fluxos
integração com APIs externas
execução de lógica operacional

Executado via container.

Banco de Dados

Utilizado para:

persistência de dados
armazenamento de estados de automação
Serviços auxiliares
cache
filas
logs
🔄 Fluxo Operacional
Entrada de dados via API
Processamento via n8n
Consulta e persistência em banco
Resposta para sistemas externos
🧪 Acesso via Console / IA

A operação pode ser realizada por:

terminal (SSH)
interfaces web
agentes automatizados
Diretriz crítica:

Toda interação automatizada deve:

usar variáveis de ambiente
evitar credenciais fixas
operar em isolamento
🔐 Segurança
Princípios obrigatórios:
uso de variáveis de ambiente (.env)
isolamento via containers
controle de acesso por chave SSH
monitoramento de logs
Proibições:

Nunca incluir neste repositório:

credenciais reais
endpoints reais
IP do servidor
tokens de autenticação
📦 Variáveis de Ambiente (exemplo)
N8N_API_KEY=YOUR_API_KEY
DATABASE_URL=YOUR_DATABASE_URL
SERVER_URL=https://your-domain.com
⚠️ Observações

Este documento representa a estrutura pública do sistema.

A configuração real:

contém dados sensíveis
deve permanecer fora do repositório
é gerenciada em ambiente seguro

---
