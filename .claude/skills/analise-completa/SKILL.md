---
name: analise-completa
description: Fluxo completo de análise econômico-financeira de uma empresa — da coleta de dados ao relatório executivo revisado. Use quando o usuário pedir uma análise completa, diagnóstico financeiro de um cliente, ou "analisar a empresa X".
---

# Análise Econômico-Financeira Completa

Fluxo de ponta a ponta do AEF-System. Execute as etapas em ordem, delegando cada uma ao subagente especialista via Agent tool.

## Etapas

### 1. Levantamento de dados (`coletor-dados-financeiros`)
- Identifique as fontes: demonstrações enviadas pelo cliente, planilhas no repositório/Drive, ou dados de mercado (ticker).
- Colete e valide: consistência cruzada, campos faltantes marcados como `null` com `_source: "missing"` — nunca inventados.
- Entregável: base validada em JSON/planilha com fontes documentadas.

### 2. Contexto de mercado (`pesquisador-mercado`) — em paralelo com a etapa 1
- Setor, comparáveis, dados macro relevantes (Selic, câmbio, inflação) com fonte e data.
- Pule esta etapa apenas se a análise for puramente interna (sem comparação externa nem valuation).

### 3. Diagnóstico técnico (`analista-financeiro`)
- Análise horizontal/vertical, indicadores de liquidez/endividamento/rentabilidade/atividade, e o que o escopo pedir (valuation, EVA, ciclo financeiro).
- Estrutura: resumo executivo → diagnóstico → pontos críticos → análise detalhada → riscos → oportunidades → recomendações.

### 4. Revisão adversarial (`revisor-financeiro`) — obrigatória
- Verificação de números, sinais, consistência entre demonstrações e premissas não declaradas.
- Corrija o que for apontado antes de seguir. Não pule esta etapa nem em análises "simples".

### 5. Relatório final (`redator-executivo`)
- Formato conforme o destinatário: memo de 1 página, relatório completo, ou material para reunião.
- Para o arquivo final formatado, use as skills `docx`/`pptx`/`pdf-creator` conforme o formato pedido.

## Regras do fluxo
- Nunca apresente ao cliente uma análise que não passou pela etapa 4.
- Registre premissas e limitações de dados no relatório final — transparência protege a consultoria.
- Se dados essenciais faltarem, pare e liste o que precisa ser solicitado ao cliente em vez de estimar.
