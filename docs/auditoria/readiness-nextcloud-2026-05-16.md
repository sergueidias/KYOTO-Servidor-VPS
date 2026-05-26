# Readiness para Nextcloud - 2026-05-16

## 🎯 Objetivo

Revisar criticamente a auditoria recente do servidor KYOTO e avaliar se há prontidão documental e operacional para uma instalação futura do Nextcloud.

Esta etapa não instala Nextcloud e não altera produção.

---

## 🧠 Contexto

A revisão foi executada em `2026-05-16`, a partir do ambiente disponível ao Codex.

Conclusão crítica: a prontidão para Nextcloud não está validada. A documentação está mais segura e organizada, mas os recursos reais do VPS KYOTO ainda não foram confirmados em uma sessão Linux do servidor de produção.

O ambiente acessível ao Codex continuou compatível com macOS local, não com o VPS Linux esperado. Por isso, qualquer resultado de recursos abaixo serve apenas para confirmar a inconsistência de ambiente, não para dimensionar o Nextcloud.

---

## ⚙️ Estrutura / Funcionamento

### Documentos revisados

| Arquivo | Leitura crítica |
| --- | --- |
| `README.md` | Lista os documentos principais e agora referencia auditoria e readiness. |
| `docs/STATUS.md` | Registra corretamente que a auditoria real do VPS ainda é pendência. |
| `docs/TEMPLATE.md` | Inclui seção de segurança e evita publicar credenciais ou endpoints reais. |
| `docs/infra/vps-setup.md` | Descreve arquitetura pública em nível seguro, sem configuração sensível. |
| `docs/arquitetura/sistema-kyoto.md` | Mantém visão conceitual da arquitetura, adequada para repositório público. |
| `docs/operacao/tokyo-bot.md` | Descreve fluxo lógico sem expor endpoint real. |
| `docs/auditoria/servidor-kyoto-2026-05-16.md` | Documenta corretamente que a execução anterior não validou o VPS real. |

### Pontos fortes

- A documentação evita dados sensíveis.
- O escopo proíbe instalação, reinício de containers, alterações em Nginx, firewall e compose.
- O relatório anterior não tenta tratar o ambiente local como produção.
- Há checklist seguro para repetir a auditoria no VPS correto.

### Lacunas para Nextcloud

- CPU real do VPS não validada.
- Memória real do VPS não validada.
- Disco real, partições e volumes persistentes não validados.
- Carga atual do servidor não validada.
- Estado real de Docker, redes e volumes não validado nesta etapa.
- Estado real de Nginx, TLS, firewall e Fail2ban não validado nesta etapa.
- Estratégia de backup e restauração para dados do Nextcloud ainda não documentada.
- Estratégia de isolamento entre serviços existentes e Nextcloud ainda não definida.

---

## 🔄 Fluxo Operacional

1. Revisar documentos existentes.
2. Executar comandos adicionais de recursos em modo leitura.
3. Comparar “documentado” contra “real acessível”.
4. Registrar resultado sem publicar saídas sensíveis.
5. Bloquear instalação até validação no VPS correto.

---

## 🧪 Uso / Execução

### Verificações adicionais executadas

| Comando | Resultado seguro |
| --- | --- |
| `uptime` | Executado no ambiente disponível; indica uptime local e não deve ser usado como métrica do VPS KYOTO. |
| `free -h` | Indisponível: comando não encontrado no ambiente disponível. |
| `df -h` | Executado no ambiente disponível; mostrou volumes locais de macOS e não representa armazenamento do VPS. |
| `lsblk` | Indisponível: comando não encontrado no ambiente disponível. |
| `nproc` | Indisponível: comando não encontrado no ambiente disponível. |
| `top -bn1 \| head -40` | Sintaxe Linux rejeitada pelo `top` do ambiente disponível, compatível com macOS. |

### Verificações complementares de serviços

| Comando | Resultado seguro |
| --- | --- |
| `free -h` | Indisponível: comando não encontrado no ambiente disponível. |
| `df -h` | Executado no ambiente disponível; retornou volumes locais e não deve ser usado para dimensionar o VPS KYOTO. |
| `docker ps` | Indisponível: `docker` não encontrado no ambiente disponível. |
| `docker stats --no-stream` | Indisponível: `docker` não encontrado no ambiente disponível. |
| `sudo nginx -t` | Não executado com privilégios: `sudo` exigiu senha no ambiente disponível. |
| `sudo certbot certificates` | Não executado com privilégios: `sudo` exigiu senha no ambiente disponível. |
| `sudo ufw status verbose` | Não executado com privilégios: `sudo` exigiu senha no ambiente disponível. |
| `sudo fail2ban-client status` | Não executado com privilégios: `sudo` exigiu senha no ambiente disponível. |

### Consistência entre documentado e real

| Item | Status | Comentário |
| --- | --- | --- |
| Ambiente de execução | Inconsistente | Documentação espera VPS Linux; ambiente acessível ao Codex respondeu como macOS local. |
| Recursos de CPU | Não validado | `nproc` não está disponível no ambiente acessível. |
| Recursos de memória | Não validado | `free -h` não está disponível no ambiente acessível. |
| Recursos de disco do VPS | Não validado | `df -h` retornou discos locais, não o VPS. |
| Topologia de blocos | Não validado | `lsblk` não está disponível no ambiente acessível. |
| Carga de processos Linux | Não validado | `top -bn1` não é aceito pelo `top` local. |
| Containers Docker | Não validado | `docker` não está disponível no ambiente acessível. |
| Nginx ativo | Não validado | Teste com `sudo` não avançou sem senha no ambiente acessível. |
| Certificados TLS | Não validado | Consulta com `sudo` não avançou sem senha no ambiente acessível. |
| Firewall e Fail2ban | Não validado | Consultas com `sudo` não avançaram sem senha no ambiente acessível. |

---

## 🔐 Segurança

Nenhuma saída bruta completa foi registrada.

Este documento não inclui:

- IPs públicos ou privados reais
- portas reais
- nomes de usuários reais
- domínios privados
- endpoints reais
- tokens, senhas, secrets ou chaves
- listagem completa de processos
- mapa real de volumes, redes, firewall, Nginx ou certificados

---

## 📌 Decisão de Readiness

Status: **não pronto para instalar Nextcloud**.

Motivo: a documentação está adequada como base pública, mas o estado real do VPS KYOTO ainda não foi comprovado. Não há evidência suficiente de CPU, memória, disco, carga, isolamento, backup, TLS e compatibilidade operacional com os serviços atuais.

Antes de qualquer instalação futura, executar a auditoria diretamente no VPS Linux KYOTO e registrar apenas um resumo mascarado dos resultados.

---

## ✅ Critérios mínimos antes de avançar

- Confirmar que a sessão é o VPS KYOTO real.
- Validar CPU, memória, disco, partições e carga.
- Validar containers atuais sem reiniciar nada.
- Validar Nginx e certificados sem alterar configuração ativa.
- Validar firewall e Fail2ban sem modificar regras.
- Definir volumes persistentes e política de backup.
- Definir isolamento do Nextcloud em relação aos serviços existentes.
- Documentar plano de rollback antes da primeira instalação.
