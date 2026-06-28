# Documentacao do e-SUS PEC Bootstrap

Este diretorio reune runbooks, evidencias, planos, inventarios e modelos
operacionais do e-SUS PEC.

## Mapa

| Caminho | Uso |
|---|---|
| `docs/_templates/` | Modelos para novas documentacoes operacionais. |
| `docs/credentials/` | Inventarios de variaveis e credenciais sem valores reais. |
| `docs/esus-pec/` | Runbooks, planos, inventarios e evidencias do e-SUS PEC. |
| `docs/monitoring/` | Observabilidade com Prometheus, Grafana, Loki, Alloy e exporters. |
| `docs/setup-readonly/` | Inventarios e planos de leitura/analise sem alteracao. |
| `docs/superpowers/` | Planos e especificacoes auxiliares de implementacao. |
| `docs/MIGRACAO_2026-06-28.md` | Registro da separacao a partir de `packer-proxmox-templates`. |

## Regra operacional

Toda alteracao em scripts, backups, restores, jobs, timers, agendamentos,
rotinas administrativas ou variaveis precisa atualizar a documentacao
correspondente no mesmo commit.

Nao registre valores reais de senhas, tokens, chaves privadas, certificados
privados ou dados sensiveis.

