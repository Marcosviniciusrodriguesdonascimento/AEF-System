---
name: relatorio-mensal
description: Rotina de fechamento e relatório gerencial mensal de um cliente — real vs orçado, indicadores, análise de desvios e relatório executivo. Use quando o usuário pedir o relatório mensal, fechamento gerencial do mês, ou acompanhamento mensal de um cliente.
---

# Relatório Gerencial Mensal

Rotina recorrente de fechamento gerencial. Delegue cada etapa ao subagente indicado.

## Etapas

### 1. Consolidação dos dados do mês (`analista-dados` + `coletor-dados-financeiros`)
- Receba/importe os dados do mês (extratos, lançamentos, faturamento, folha).
- Reconcilie fontes (ex.: extrato bancário vs lançamentos) e reporte divergências antes de prosseguir.

### 2. Apuração gerencial (`controller-orcamentario`)
- DRE gerencial do mês e acumulado do ano.
- Real vs orçado vs mesmo mês do ano anterior; decomposição dos principais desvios por materialidade.
- Indicadores do painel: margem de contribuição, EBITDA gerencial, ponto de equilíbrio, ciclo financeiro.

### 3. Leitura financeira (`analista-financeiro`)
- Interpretação dos indicadores: tendências, alertas de liquidez/endividamento, evolução vs meses anteriores.

### 4. Revisão (`revisor-financeiro`)
- Conferência de totais, sinais e consistência com o relatório do mês anterior (saldos que transitam).

### 5. Relatório e apresentação (`redator-executivo`)
- Formato padrão: destaques do mês (3-5 bullets) → DRE resumida → desvios relevantes e causas → indicadores → ações recomendadas → pendências do cliente.
- Se houver dashboard do cliente, alinhe os números com o `especialista-powerbi` (relatório e dashboard nunca podem divergir).

## Regras
- Números do relatório mensal devem bater com o dashboard e com o mês anterior — qualquer quebra de série precisa de nota explicativa.
- Pendências do cliente (documentos não enviados) entram no relatório com impacto explícito.
- Mantenha o mesmo formato todo mês: comparabilidade vale mais que criatividade.
