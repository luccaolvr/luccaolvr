# Plane — Instalação e Boas Práticas

## Instalação (Docker, edição Community)

Requisitos: Docker + Docker Compose, 4 GB de RAM ou mais, 2 CPUs ou mais.

```bash
mkdir -p ~/plane/plane-app && cd ~/plane/plane-app
U=https://github.com/makeplane/plane/releases/latest/download
curl -fsSL -o docker-compose.yaml $U/docker-compose.yml
curl -fsSL -o plane.env $U/variables.env
sed -i "s/^SECRET_KEY=.*/SECRET_KEY=$(openssl rand -hex 32)/" plane.env
docker compose --env-file plane.env up -d
```

Acesse `http://localhost` (painel de admin em `http://localhost/god-mode`).
Alternativa interativa: `curl -fsSL -o setup.sh https://github.com/makeplane/plane/releases/latest/download/setup.sh && bash setup.sh`

Comandos úteis:
- Parar: `docker compose --env-file plane.env down`
- Logs: `docker compose --env-file plane.env logs -f api`
- Atualizar: `docker compose --env-file plane.env pull && docker compose --env-file plane.env up -d`

## Boas práticas

### Configuração / segurança
- Troque `SECRET_KEY` e as senhas padrão (Postgres, RabbitMQ, MinIO) no `plane.env`.
- Defina `APP_DOMAIN`/`WEB_URL` com seu domínio real e use HTTPS (proxy reverso ou `CERT_EMAIL`).
- Configure SMTP no god-mode para convites e notificações.
- Desative o cadastro aberto se a instância for privada.
- Faça backup regular dos volumes (`pgdata`, `uploads`) e teste a restauração.
- Fixe uma versão (`APP_RELEASE=vX.Y.Z`) em produção e leia o changelog antes de atualizar.

### Organização do trabalho
- **Workspace** = empresa; **Projeto** = time ou produto. Não crie projetos demais.
- **Work items (issues)**: título claro em forma de ação, descrição com critério de aceite, um responsável.
- **Estados**: mantenha o fluxo simples (Backlog → Todo → In Progress → Review → Done).
- **Labels**: poucas e padronizadas (ex.: `bug`, `feature`, `melhoria`).
- **Prioridade** e **estimativa** em todo item que entrar em ciclo.
- **Cycles** (sprints) de 1 a 2 semanas; revise o que ficou pendente ao fechar.
- **Modules** para agrupar entregas/épicos que atravessam vários ciclos.
- **Views** salvas para filtros recorrentes ("meus itens", "bugs críticos").
- **Pages** para documentação, specs e atas, ligadas aos itens.
- Faça triagem do backlog toda semana: feche duplicados e itens obsoletos.
