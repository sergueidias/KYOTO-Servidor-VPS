# Auditoria do Servidor KYOTO - 2026-05-16

## 🎯 Objetivo

Registrar a auditoria inicial solicitada para o servidor KYOTO, sem instalar pacotes, alterar serviços, reiniciar containers ou modificar o Nginx ativo.

Esta etapa não instala Nextcloud.

---

## 🧠 Contexto

A auditoria foi executada a partir do ambiente local disponível ao Codex em `2026-05-16`, timezone `America/Sao_Paulo`.

Resultado principal: a sessão disponível não é o VPS Linux KYOTO. O ambiente identificado é macOS local (`Darwin`, `arm64`), portanto os resultados abaixo não devem ser tratados como estado real do servidor de produção.

Dados sensíveis observados em saídas de comando foram omitidos ou mascarados. Um endereço privado apareceu no `uname -a` local e foi registrado apenas como `[HOST_PRIVADO_MASCARADO]`.

---

## ⚙️ Estrutura / Funcionamento

A auditoria seguiu somente comandos de leitura previamente autorizados. Não foram executadas ações de instalação, alteração de serviço, reinício de container ou edição de Nginx.

Categorias verificadas:

- sistema operacional e uptime
- uso de disco
- Docker e Docker Compose
- Nginx e diretórios de sites
- firewall, Fail2ban e certificados
- status de serviços via `systemctl`

---

## 🔄 Fluxo Operacional

1. Criar branch própria de auditoria.
2. Executar os comandos autorizados no ambiente disponível.
3. Mascarar qualquer dado sensível antes de documentar.
4. Atualizar documentação pública do repositório.
5. Abrir PR com as alterações documentais.

---

## 🧪 Uso / Execução

### Resumo dos comandos executados

| Comando | Resultado seguro |
| --- | --- |
| `hostnamectl` | Indisponível no ambiente local: comando não encontrado. |
| `uname -a` | Ambiente local identificado como `Darwin`, `arm64`; hostname/IP privado mascarado. |
| `lsb_release -a || cat /etc/os-release` | Indisponível no ambiente local: `lsb_release` ausente e `/etc/os-release` inexistente. |
| `uptime` | Executado no ambiente local; uptime aproximado de 17 dias. |
| `free -h` | Indisponível no ambiente local: comando não encontrado. |
| `df -h` | Executado no ambiente local; não representa o VPS KYOTO. Um volume externo local apareceu com uso elevado, fora do escopo do servidor. |
| `lsblk` | Indisponível no ambiente local: comando não encontrado. |
| `docker ps` | Indisponível no ambiente local: `docker` não encontrado. |
| `docker ps -a` | Indisponível no ambiente local: `docker` não encontrado. |
| `docker compose ls` | Indisponível no ambiente local: `docker` não encontrado. |
| `docker network ls` | Indisponível no ambiente local: `docker` não encontrado. |
| `docker volume ls` | Indisponível no ambiente local: `docker` não encontrado. |
| `sudo nginx -t` | Não executado com privilégios: `sudo` exigiu senha no ambiente local. |
| `ls -la /etc/nginx/sites-enabled` | Diretório inexistente no ambiente local. |
| `ls -la /etc/nginx/sites-available` | Diretório inexistente no ambiente local. |
| `sudo ufw status verbose` | Não executado com privilégios: `sudo` exigiu senha no ambiente local. |
| `sudo fail2ban-client status` | Não executado com privilégios: `sudo` exigiu senha no ambiente local. |
| `sudo certbot certificates` | Não executado com privilégios: `sudo` exigiu senha no ambiente local. |
| `systemctl status docker --no-pager` | Indisponível no ambiente local: `systemctl` não encontrado. |
| `systemctl status nginx --no-pager` | Indisponível no ambiente local: `systemctl` não encontrado. |

### Checklist para executar no VPS real

Executar somente em sessão SSH autorizada no VPS KYOTO, sem publicar valores brutos no repositório:

```bash
hostnamectl
uname -a
lsb_release -a || cat /etc/os-release
uptime
free -h
df -h
lsblk
docker ps
docker ps -a
docker compose ls
docker network ls
docker volume ls
sudo nginx -t
ls -la /etc/nginx/sites-enabled
ls -la /etc/nginx/sites-available
sudo ufw status verbose
sudo fail2ban-client status
sudo certbot certificates
systemctl status docker --no-pager
systemctl status nginx --no-pager
```

Antes de registrar resultados:

- mascarar IPs públicos e privados
- mascarar domínios privados, se houver
- mascarar nomes de usuários reais
- remover tokens, senhas, secrets, caminhos com chaves e qualquer credencial
- substituir portas sensíveis por `PORT_MASCARADA`, quando necessário

---

## 🔐 Segurança

Nenhum secret, token, senha, chave privada, IP sensível ou endpoint real foi adicionado a este documento.

As saídas completas dos comandos não foram commitadas. Este relatório mantém apenas conclusões seguras e reproduzíveis.

---

## 📌 Conclusão

A auditoria operacional do VPS KYOTO ainda precisa ser repetida no host correto. A execução desta etapa confirmou apenas que o ambiente local do Codex não corresponde ao servidor Linux esperado.

Até essa validação ser feita no VPS real, não há base segura para instalar Nextcloud ou alterar serviços de produção.
