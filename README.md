# e-SUS PEC Bootstrap

Este repositorio concentra as automacoes, runbooks, validacoes e inventarios do
e-SUS PEC. Ele foi separado de `packer-proxmox-templates` para manter o ciclo de
vida do PEC independente dos templates Packer/Proxmox.

## Escopo

Este repositorio guarda:

- provisionamento e configuracao do e-SUS PEC em LXC/VM;
- automacoes de primeira execucao, TLS, Gov.br OAuth, importacoes CNES/PBF;
- backup, restore, MinIO/ObjectStorage e WAL-G;
- monitoramento Prometheus, Grafana, Loki, Alloy e exporters relacionados ao
  PEC;
- validacoes e documentacao operacional do PEC.

Fica fora deste repositorio:

- templates Packer de Windows/Linux;
- rotinas SIHA NAS;
- segredos reais em arquivos rastreados.

## Linguagens e ferramentas

Use preferencialmente Python com `uv` para novas automacoes. PowerShell, Bash e
Go tambem sao suportados quando forem mais adequados ao ambiente alvo.

Comandos base:

```powershell
uv sync
uv run python --version
```

Scripts historicos em PowerShell, Bash e Node/MJS foram preservados durante a
migracao. Ao tocar uma rotina existente, mantenha o estilo local ou migre com
teste e documentacao no mesmo commit.

## Ambiente local

O arquivo `.env` local pode existir neste repositorio, mas e ignorado pelo git.
O arquivo `.env.example` contem somente nomes de variaveis e placeholders.

Nunca commite senhas, tokens, chaves privadas, certificados privados ou dados de
saude/faturamento.

## Validacao

Execute os validadores relevantes antes de finalizar uma mudanca:

```powershell
rtk powershell -NoProfile -ExecutionPolicy Bypass -File tests\Validate-EsusPecInfisicalSync.ps1
rtk powershell -NoProfile -ExecutionPolicy Bypass -File tests\Validate-MonitoringStack.ps1
rtk git diff --check
```

Alguns testes dependem de conectividade com Proxmox, Infisical ou CTs
existentes. Quando um teste real nao for executado, registre a limitacao no
relatorio da mudanca.

## Documentacao

Use `docs/README.md` e `docs/_templates/` para localizar ou criar runbooks.
Qualquer mudanca em scripts, backups, restores, jobs, agendamentos, rotinas
administrativas ou variaveis deve atualizar a documentacao no mesmo commit.

