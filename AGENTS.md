# Repository Guidelines

## Operational Boundary

Este repositorio e responsavel pelo bootstrap e operacao do e-SUS PEC. O
repositorio `packer-proxmox-templates` fica reservado para templates Packer e
rotinas Proxmox genericas. Nao reintroduza automacoes PEC no repositorio de
templates.

## Tooling

Prefixe comandos com `rtk` quando estiver neste workspace.

Use preferencialmente Python com `uv` para novas automacoes. PowerShell, Bash e
Go sao permitidos quando forem pragmaticamente melhores para o alvo operacional.
Nao adicione uma stack nova sem necessidade.

## Project Structure

- `scripts/esus-pec/`: provisionamento, configuracao, backup, restore, TLS,
  importacoes e integracoes do PEC.
- `scripts/monitoring/`: stack de observabilidade do PEC e alvos relacionados.
- `scripts/common/`: helpers compartilhados por scripts do repositorio.
- `shared/scripts/`: utilitarios reutilizaveis.
- `tests/`: validacoes estaticas e preflights seguros.
- `docs/`: runbooks, evidencias, planos e inventarios operacionais.
- `config/`: exemplos rastreados de variaveis e inventarios sem valores reais.

## Operational Documentation Standard

Qualquer alteracao em scripts, backups, restores, jobs, timers, agendamentos,
rotinas administrativas ou variaveis Infisical deve atualizar a documentacao no
mesmo commit.

Documentos operacionais devem ficar em portugues brasileiro, com:

- objetivo e escopo;
- topologia, CTID/VMID, hostnames, IPs, paths e storages;
- pre-requisitos e dry-run quando existir;
- comandos exatos;
- validacao com resultado esperado;
- backup/restore e rollback;
- riscos, seguranca e exposicao;
- evidencias, logs e checklist de aceite.

## Secrets

Nunca commite `.env`, tokens, senhas, chaves privadas, certificados privados ou
dados sensiveis. Arquivos `.example` devem conter somente nomes de variaveis e
placeholders.

Neste workspace, namespaces Infisical sao separados:

- `INFISICAL_*`: projeto ESUS PEC;
- `TEMPLATE_INFISICAL_*` ou `TEMPLATES_INFISICAL_*`: projetos de template;
- `SIHA_INFISICAL_*`: projetos SIHA.

Scripts devem tornar o namespace pretendido explicito e nao devem fazer fallback
silencioso entre projetos.

## Commits

Mantenha commits atomicos. Uma fatia operacional deve conter scripts/config,
documentacao, exemplos e testes do mesmo escopo, sem misturar mudancas
independentes.

